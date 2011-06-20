

outline of the report
=====================

Idee: 
Das Gehirn hat wohl nicht genug kapazität um alle einströmenden Informationen in gleicher Tiefe zu verarbeiten. Wir denken es dass Aufmerksamkeit dazu dient die im Gehirn verfügbaren resourcen möglichst effizient zu verteilen. Ein bekanntes Model zur Verteilung der Aufmerksamkeit ist das Salienzmodel von Itti und Koch. Neuere Forschungen (Walter) zeigen dass es nicht nur low-level salienz gibt, sondern schon sehr früh unsere Aufmerksamkeit auf Objekte gelenkt wird, sogenannte Protoobjekte. Wir haben uns also überlegt wie wir möglichst simpel (einfache Heuristik) eine suche nach protoobjekten implementieren können um dann nur in diesen vorselektierten Bereichen die rechnerisch Aufwändigen Analysen zur Objektsuche auszuführen.

Hierzu benutzen wir nun eine 3D Kamera. Das Tiefenbild dient uns als einfache Heuristik mit der Annahme dass Objekte von starken "Tiefengradienten" eingefasst sind.

first parallel stage, later serial processing

look what I wrote for my A&C summaries

spotlight


free viewing macht salienz sinn, sonst ist aufmerksamkeit wohl eher task abhaengig.


Summaries
=========

* Walther und Koch: 
    * Benutzen ein Bottom up modell


Ausblick, weitere Ideen
=======================

* walther und koch benutzen den bekannten saliency map ansatz um die fläche von protoobjekten zu finden. Das könnte man bestimmt schön kombinieren. Wir könnten ja z.B. unseren Tiefengradienten als eine der Saliency maps nehmen. Vielleicht sogar noch mit hohem gewicht, weil es so ein guter ansatz ist. Dann über andere maps aber z.b. auch farb homogenität und ähnliches mit einfließen lassen. 