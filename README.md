# four-axis-CNC-Hot-wire-Cutter
This repo shows the construction and software for an four axis cnc hot wire cutter

# CNC Heißdraht-Schneider mit Rotationsachse

Dieses Projekt umfasst die Entwicklung und Steuerung einer **5-Achs-CNC-Heißdrahtschneidemaschine**. Durch die Kombination von zwei unabhängigen XY-Ebenen und einer synchronisierten Drehachse können komplexe 3D-Geometrien aus Schaumstoffblöcken präzise herausgearbeitet werden.

---

# Funktionsweise

Das System nutzt eine spezialisierte Kinematik, um Material nicht nur linear, sondern auch volumetrisch durch Rotation abzutragen.

## Mechanischer Aufbau

Die Hardware besteht aus drei Kernkomponenten:

* **Die XY-Ebenen:** An beiden Enden des Drahtes befindet sich jeweils eine unabhängige 2D-Linearführung. Dies ermöglicht unterschiedliche Profile pro Seite (z.B. für Tragflächen oder konische Körper).
* **Der Heißdraht:** Ein elektrisch beheizter Schneidedraht, der unter Spannung zwischen den XY-Schlitten geführt wird.
* **Die Rotationsachse:** Zwischen den Ebenen ist eine Drehaufnahme montiert, die den Materialblock hält und präzise rotiert.

## Bewegungsablauf

Der Prozess folgt einer koordinierten Strategie:
1. Der Schaumstoffblock wird in der **Zentralachse** fixiert.
2. Während die **Linearantriebe** den Draht durch die Ebenen führen, dreht sich der Block synchron dazu.
3. Durch die Überlagerung der Bewegungen wird die gewünschte Form "abgewickelt" oder spiralförmig geschnitten.

---

# Technische Details

Die Präzision des Schnitts hängt maßgeblich von der Abstimmung zwischen Drahtvorschub, Temperatur und Rotationsgeschwindigkeit ab.

## Achsen-Konfiguration

| Achse | Komponente | Beschreibung |
| :--- | :--- | :--- |
| **X1 / Y1** | Ebene A | Positioniert das linke Drahtende |
| **X2 / Y2** | Ebene B | Positioniert das rechte Drahtende |
| **A-Achse** | Rotation | Dreht den Materialblock (Werkstück) |

## Physikalische Grundlagen

Die Heizleistung $P$ des Drahtes muss dynamisch an die Schnittgeschwindigkeit $v$ angepasst werden, um Abbrand zu minimieren:

$$P = k \cdot L \cdot v + P_{loss}$$

---

# Prozess-Visualisierung

Der folgende Ablauf zeigt den Datenfluss von der Idee bis zum fertigen Bauteil:

```mermaid
graph TD
    A[CAD Modell] --> B[Slicer / CAM]
    B --> C{G-Code Controller}
    C --> D[Linearachsen X1/Y1 & X2/Y2]
    C --> E[Rotationsachse A]
    D --> F[Finales Bauteil]
    E --> F
