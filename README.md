# ha-IR-Sauna

Dieses Repository enthält ein Home-Assistant-Blueprint zur Steuerung einer Infrarot-Sauna mit zwei Strahlern ("Liege" und "Oben").

## Blueprint: IR Sauna – Programm Zone

Der Blueprint [`ir_sauna_program_zone.yaml`](blueprints/automation/ir_sauna/ir_sauna_program_zone.yaml) bietet folgende Programme:

- **AUS** – Strahler werden ausgeschaltet.
- **Gleichmässig** – Beide Strahler laufen mit konstanter Intensität.
- **Intervall** – Wellensignal mit gleichlaufender Auf- und Abwärtssteuerung auf Basis einer Zyklusdauer.
- **Einmal AUF und AB** – Ein Auf- und Abwärtszyklus über die Gesamtzeit.

Dauer, maximale Intensität und Zyklusdauer werden über Input-Helfer konfiguriert und ein Timer zeigt die Restlaufzeit an.
