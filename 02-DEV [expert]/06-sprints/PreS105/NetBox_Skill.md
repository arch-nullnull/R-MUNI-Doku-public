---
name: nbx
beschreibung: >
  NBX Skill für R+MUNI. Aktivieren wenn NBX-Flow Scripts (NBX00-NBX04)
  entwickelt oder gewartet werden, oder wenn NetBox als Datenquelle für
  den R+MUNI ECM-Flow diskutiert wird. Ergänzt r-muni-visualization —
  überlagert ihn nicht. Scope: IST-Erfassung Hardware + Services via
  NetBox Community. IPAM, Tenancy, Circuits: out of scope, Folge-Sprint.
---

# NetBox Skill — NBX-Flow Kontext für R+MUNI

## Zweck und Grenzen

Dieser Skill liefert den Kontext für den **NBX-Flow** in R+MUNI.
Er ist schmal und fokussiert — kein NetBox-Expertensystem.

**In scope:**
- NetBox Community Initialisierungs-Scripts (Device-Type-Library-Import, pynetbox)
- netbox-agent (Solvik) — Hardware-Erfassung auf Zielmaschinen
- REST API Endpunkte für DCIM + Virtualization + Services
- NBX-Flow Logik (NBX00-NBX04) und Output-Format nbx_trash.csv

**Explizit out of scope (Folge-Sprints):**
- IPAM: IP-Adressen, VLANs, Prefixes, VRFs
- Tenancy, Circuits, Power, Cables
- Software-Inventar (kein natives NetBox-Konzept im Core)
- NetBox Enterprise / Cloud Features
- GraphQL API, Custom Scripts innerhalb NetBox

Bei Fragen zu out-of-scope Bereichen: rückfragen, nicht ableiten.

---

## NetBox Kurzprofil

Was NetBox ist: Source of Truth für Netzwerk-Infrastruktur (DCIM + IPAM).
Philosophie: Intended State dokumentieren — nicht Monitoring-Daten sammeln.
Lizenz: Apache 2, Open Source, Community Edition kostenlos.
Repos: github.com/netbox-community/
API-Basis: REST, JSON Responses, Primary Key id (Integer, stabil pro Instanz).
Auth: Token-basiert — Authorization: Token <token> im HTTP Header.
Pagination: Standard 50 Objekte — ?limit=0 deaktiviert Pagination (alle Objekte).
Versionshinweis: Ab v4.3 ist InventoryItem deprecated, Modules verwenden.

---

## Community Scripts — Erst-Initialisierung

### 1. Device-Type-Library-Import

Repo: github.com/netbox-community/Device-Type-Library-Import
Zweck: Importiert Hersteller + Gerätemodelle aus der Community YAML-Library
in eine frische NetBox-Instanz. Voraussetzung bevor echte Devices erfasst
werden können — NetBox braucht Device-Typen als Basis.

Ablauf:
  git clone https://github.com/netbox-community/Device-Type-Library-Import.git
  cd Device-Type-Library-Import
  python3 -m venv venv && source venv/bin/activate
  pip install -r requirements.txt
  cp .env.example .env        # URL + Token eintragen
  python3 main.py             # importiert gewählte Hersteller

Output: Device-Typen in NetBox — Basis für spätere Device-Erfassung.
Relevanz für NBX-Flow: Einmaliger Vorbereitungsschritt, kein Teil von NBX00-NBX04.


### 2. pynetbox

Repo: github.com/netbox-community/pynetbox
Zweck: Offizieller Python API Client der Community — abstrahiert REST API Calls.
Installation: pip install pynetbox

Basis-Nutzung:
  import pynetbox
  nb = pynetbox.api('http://localhost:8000', token='<token>')

  # Alle aktiven Devices
  devices = nb.dcim.devices.filter(status='active')

  # Alle VMs
  vms = nb.virtualization.virtual_machines.all()

  # Services auf Devices
  services = nb.dcim.services.all()

Relevanz für NBX-Flow: Basis-Library für NBX01 (Rohdaten-Erfassung Modus A).
Hinweis: requests waere Alternative — pynetbox ist Community-Standard
und behandelt Pagination automatisch.


### 3. netbox-agent

Repo: github.com/Solvik/netbox-agent
Zweck: Läuft auf Zielmaschinen, erfasst Hardware via dmidecode und
schreibt direkt in NetBox via REST API.

Was er erfasst:
  - Server / Chassis / Blade Hardware (Hersteller, Modell, Serial)
  - Physische + virtuelle Netzwerkinterfaces mit IPs (IPv4 + IPv6)
  - Hardware-Komponenten: CPU, GPU, RAM, RAID Cards, Disks, PSUs (als Modules)
  - Hypervisor zu VM Zuordnung
  - Rack-Location (via Treiber, wenn konfiguriert)

Konfiguration: /etc/netbox_agent.yaml
Ausfuehrung: netbox_agent -c /etc/netbox_agent.yaml --update

Relevanz für NBX-Flow:
  Agent schreibt in NetBox. NBX01 liest danach via REST API (Modus A).
  Agent ist kein direkter Script-Input — er ist der Erfassungskanal.

---

## REST API — Relevante Endpunkte (NBX-Flow Scope)

### DCIM — Physical Infrastructure

GET /api/dcim/devices/?status=active&limit=0
  Relevante Felder:
    id                          nbx_raw_id (3PartyID Basis)
    name                        Name
    device_type.model           Model
    device_type.manufacturer.name   Manufacturer
    device_role.name            Role
    platform.name               Platform (OS)
    site.name                   Site
    status.value                active / planned / decommissioned / offline
    serial                      Property: serial_number
    asset_tag                   Property: asset_tag
    description                 Description

GET /api/dcim/racks/?limit=0
  Relevante Felder:
    id, name, site.name, status.value, u_height
    Physical Layer: Facility / Equipment Container

GET /api/dcim/modules/?limit=0   (ab NetBox v4.3, ersetzt InventoryItem)
  Relevante Felder:
    id, device.id, module_type.model, serial, asset_tag
    Hardware-Komponenten als Properties auf Devices


### Virtualization

GET /api/virtualization/virtual-machines/?status=active&limit=0
  Relevante Felder:
    id                          nbx_raw_id
    name                        Name
    cluster.name                Property: cluster
    platform.name               Platform
    status.value                active / planned / offline / staged
    vcpus                       Property: vcpus
    memory                      Property: memory_mb
    disk                        Property: disk_gb
    primary_ip.address          Property: primary_ip


### Services (Application Layer)

GET /api/dcim/services/?limit=0           Services auf physischen Devices
GET /api/virtualization/services/?limit=0  Services auf VMs
  Relevante Felder:
    id                          nbx_raw_id
    name                        Name
    device.name                 Property: host_device (bei dcim)
    virtual_machine.name        Property: host_vm (bei virtualization)
    protocol.value              Property: protocol (tcp/udp)
    ports                       Property: ports
    description                 Description

Wichtig zu Services: Services in NetBox = laufende Netzwerkdienste
(Port + Protokoll auf einem Host). Keine installierten Software-Pakete.
Fuer Application Layer im ArchiMate Modell ist das der verfuegbare
Rohstoff aus NetBox Community ohne Plugins.

---

## Nested Objects — Feldextraktion

API Response enthaelt verschachtelte Objekte. NBX02 muss aufloesen:

  # FALSCH — gibt dict-Objekt zurueck
  name = device['platform']

  # RICHTIG — auf Wert zugreifen
  platform = device['platform']['name'] if device['platform'] else ''
  status   = device['status']['value']
  mfr      = device['device_type']['manufacturer']['name']
  model    = device['device_type']['model']
  site     = device['site']['name'] if device['site'] else ''

Null-Handling: Viele Felder koennen null sein.
NBX02 setzt leeren String "" fuer null-Werte — kein None im CSV.

---

## NBX-Flow Uebersicht

NetBox (befuellt via netbox-agent oder manuell)
  |
  v
NBX00   Validierung + Root-Aufloesung
        prueft API-Verbindung (Modus A) oder Datei-Verfuegbarkeit (B/C)
        schreibt NBX00-root.resolved.txt in 02-stages/99-logs/

NBX01   Rohdaten-Erfassung via pynetbox (Modus A — primaer)
        /api/dcim/devices/ + /api/virtualization/virtual-machines/
        /api/dcim/racks/ + /api/dcim/services/ + /api/virtualization/services/
        schreibt nbx_raw.json in 02-stages/ (Zwischenartefakt, in .gitignore)

NBX02   Normierung + Feldextraktion
        flacht JSON ab, loest nested objects auf
        Null-Handling: None wird zu ""
        schreibt nbx_normalized.csv in 02-stages/ (Zwischenartefakt)

NBX03   3PartyID Anreicherung + Dubletten-Check
        erzeugt 3PartyID: nbx_<id> (z.B. nbx_2230)
        Dubletten-Check via Name + nbx_objecttype
        schreibt nbx_trash.csv nach
          01-artifacts\02-csv\03-child\00-archimatechild\

NBX04   Uebergabe-Report
        schreibt nbx_handoff_report.txt in 02-stages\99-logs\
        Inhalt: Anzahl Objekte je Typ, SKIPs, Warnungen

---

## Output-Format nbx_trash.csv

Ablageort : 01-artifacts\02-csv\03-child\00-archimatechild\nbx_trash.csv
Encoding  : UTF-8 ohne BOM
Trennzeichen: Komma (,)
Verwendung: Eingang in ECM Phase 1 (ECM01 einmalig) oder Phase 2 (ECM02)

Header:
  3PartyID,nbx_objecttype,Name,Role,Platform,Site,Status,Manufacturer,Model,Description,nbx_source,nbx_raw_id

Spalten:
  3PartyID        nbx_<id>                            konstruiert
  nbx_objecttype  device/vm/rack/service_device/      konstruiert
                  service_vm
  Name            Gerätename / Servicename             name
  Role            Device Role                          device_role.name
  Platform        OS / Plattform                       platform.name
  Site            Standort                             site.name
  Status          active / planned / ...               status.value
  Manufacturer    Hersteller                           device_type.manufacturer.name
  Model           Gerätemodell                         device_type.model
  Description     Freitext                             description
  nbx_source      API / AgentDump / Export             konstruiert
  nbx_raw_id      Integer                              id

Beispielzeilen:
  3PartyID,nbx_objecttype,Name,Role,Platform,Site,Status,Manufacturer,Model,Description,nbx_source,nbx_raw_id
  nbx_2230,device,router1,core-router,Junos,Wien-DC1,active,Juniper,vQFX-10000,,API,2230
  nbx_4417,vm,webserver-01,web,Ubuntu 22.04,,active,,,,API,4417
  nbx_7001,service_vm,nginx,,,,,,,Port 443/tcp,API,7001

---

## Konfigurationsdatei nbx_config.txt

Ablageort: neben root.cfg im Blueprint Root
In .gitignore aufnehmen — enthaelt API Token.

  nbx_mode=A                          # A=API / B=AgentDump / C=Export
  nbx_api_url=http://localhost:8000   # nur Modus A
  nbx_api_token=<TOKEN>               # nur Modus A — NIEMALS ins Repo
  nbx_dump_path=                      # nur Modus B/C — relativer Pfad zu Root
  nbx_status_filter=active            # active / planned / all
  nbx_limit=0                         # 0 = alle Objekte (Pagination off)

Sicherheit: Token in KeePass. Read-Only Recht reicht fuer NBX-Flow vollstaendig.

---

## Abgrenzung zu anderen R+MUNI Flows

  NBX-Flow   NetBox Rohdaten erfassen und normieren (nbx_trash.csv produzieren)
  ECM-Flow   nbx_trash.csv konsumieren, Archi Mapping, Import
  CSV-Flow   Archi Export zu Master CSVs zu Archi Import
  CLE-Reihe  Ordner bereinigen vor und nach NBX-Lauf

NBX produziert — ECM konsumiert. Keine Ueberschneidung.

---

## Reihenfolge Erst-Setup (einmalig, vor NBX-Flow Sprint)

  1. NetBox Community installieren (Docker oder native)
  2. Device-Type-Library-Import ausfuehren — Hersteller/Modelle laden
  3. netbox-agent auf Zielmaschinen installieren + konfigurieren
  4. netbox-agent ausfuehren — Devices erscheinen in NetBox
  5. API Token in NetBox erzeugen (Read-Only genuegt)
  6. Token in KeePass ablegen
  7. nbx_config.txt befuellen (Token nicht ins Repo)
  8. NBX00 ausfuehren — Verbindungstest

---

NBX Skill | R+MUNI Blueprint | S1.02 | 2026-04-06
Scope: IST-Erfassung Hardware + Services. IPAM + weitere Bereiche: Folge-Sprint.
