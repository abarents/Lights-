# WLED JUCE Controller als VST3 plugin voor een DAW (zoals Cubase)

Een C++ / JUCE-applicatie om WLED LED-controllers aan te sturen. Deze software kan zowel via HTTP JSON-requests als via het realtime UDP DNRGB/DNRGBW-protocol communiceren met WLED-apparaten.

## Functionaliteiten

* **Verschillende werkmodi**:
* **Single Colour (JSON)**: Stuur een handmatige of geautomatiseerde kleur en helderheid naar een specifiek WLED-segment.


* **Multi-Controller UDP (DNRGB/DNRGBW)**: Stuur effen kleuren efficiënt naar meerdere WLED-controllers tegelijk via UDP (zonder HTTP-overhead).


* **Presets**: Schakel direct tussen WLED-presets (0-250) inclusief helderheidsregeling.


* **Segment Mixers**: Beheer meerdere segmenten tegelijk via een 8-kanaals mixer of een gedetailleerde 1-kanaals weergave.




* **Automatische Record-reactie**: Optioneel een segment automatisch laten reageren op een actieve opnamestatus (bijvoorbeeld tijdens het opnemen in een DAW) met een configureerbare kleur en helderheid.


* **Verbindingsdiagnostiek**: Ingebouwde ping- en statuscontrole om direct te verifiëren of de WLED-controller bereikbaar is en welke firmwareversie draait.



## Technische Componenten

De codebase is opgebouwd rondom de volgende hoofdcomponenten:

* `LightsAudioProcessor` & `LightsAudioProcessorEditor`: De kernlogica en de grafische interface gebouwd met JUCE.


* `WledLookAndFeel`: Aangepaste styling voor sliders, knoppen en segmenten.


* `WledSegmentSender` & `WledPresetSender`: Achtergrondthreads voor het afhandelen van HTTP POST-verzoeken naar de WLED JSON API.


* `WledDnrgbSender`: UDP-realtime verzender die grote LED-strips automatisch opsplitst in pakketten binnen de protocollimiet (max 489 LEDs per pakket).


* `WledStateFetcher` & `WledConnectionTester`: Achtergrondthreads voor het ophalen van de huidige status en het testen van de netwerkverbinding.
