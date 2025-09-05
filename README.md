# ha-IR-Sauna

Dieses Repository enthält ein Home-Assistant-Blueprint zur Steuerung einer Infrarot-Sauna mit zwei Strahlern ("Liege" und "Oben").

## Blueprint: IR Sauna – Programm Zone

Der Blueprint [`ir_sauna_program_zone.yaml`](blueprints/automation/ir_sauna/ir_sauna_program_zone.yaml) bietet folgende Programme:

- **AUS** – Strahler werden ausgeschaltet.
- **Gleichmässig** – Beide Strahler laufen mit konstanter Intensität.
- **Intervall** – Wellensignal mit gleichlaufender Auf- und Abwärtssteuerung auf Basis einer Zyklusdauer.
- **Einmal AUF und AB** – Ein Auf- und Abwärtszyklus über die Gesamtzeit.

Dauer, Min-/Max-Intensität und Zyklusdauer werden über Input-Helfer konfiguriert und ein Timer zeigt die Restlaufzeit an.
Änderungen an Min-/Max-Intensität sowie der Zyklusdauer wirken sich während des laufenden Programms sofort aus.

### Eingänge und Ausgänge

Der Blueprint verknüpft folgende Entitäten und nutzt sie wie angegeben:

- **Programmauswahl (`input_select`)** – Bestimmt welches Programm läuft und wird nach Ende auf `AUS` zurückgesetzt.
- **Dauer in Minuten (`input_number`)** – Legt die Gesamtlaufzeit des Programms bzw. die Schrittzeit bei *Einmal AUF und AB* fest.
- **Max-Intensität % (`input_number`)** – Oberer Grenzwert für die Helligkeit der Strahler.
- **Min-Intensität % (`input_number`)** – Unterer Grenzwert für die Helligkeit der Strahler.
- **Intervall – Zyklusdauer (`input_number`)** – Definiert die Dauer eines Auf- und Ab-Zyklus im Programm *Intervall*.
- **Timer für Restlaufzeit (`timer`)** – Zeigt die verbleibende Laufzeit an; Ablauf oder Abbruch schaltet die Strahler aus.
- **Strahler – Liege (`light`)** und **Strahler – Oben (`light`)** – Die gesteuerten IR-Strahler, deren Helligkeit entsprechend des gewählten Programms geregelt wird.
