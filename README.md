# TalkToPDF
GPT-3.5 bzw. GPT-4 liest für Dich (PDF)-Texte und beantwortet deine Fragen zum Text. 

![TalkToPDF-Condense-Demo](./talktopdf-demo.png)

## Was man braucht
- Ein Google-Konto (um das Notebook in Colab auszuführen); ersatzweise eine lokale juPyter-Installation
- Ein gültiges Token für die OpenAI-API
- Ein paar Cent über die Kreditkarte
- Ein nicht zu langes PDF, das Text enthält (wenn das PDF nur Fotos des Textes enthält, wird der Text nicht verarbeitet)

## Wie man es nutzt
- Das [Notebook](./TalkToPDF.ipynb) anklicken und den "Open in Colab"-Button anklicken. (Also: in Googles Colab öffnen)
- Das kleine "Play"-Dreieck bei der ersten Code-Zelle anklicken - die Vorbereitungen werden ausgeführt
- Das kleine "Play"-Dreieck bei der nächsten Code-Zelle anklicken - und ein gültiges OpenAI-API-Token eingeben. 
- Das kleine "Play"-Dreieck bei der nächsten Code-Zeile anklicken, ein PDF hochladen.
- Ggf. Modell (und damit Token-Grenze) anpassen und ggf. den Text kondensieren lassen. 
- Mit dem Modell über das PDF chatten. 

## Grenzen
Text, Fragen und Antworten müssen in die Token-Grenze passen - das setzt für GPT3.5 (max. 4096 Token) die Grenze bei 3-5 Seiten. (Und dann sind nur noch sehr kurze Fragen und Antworten möglich.) Kondensieren ermöglicht Texte mit bis zu 8-facher Länge. 

## Beispiel-PDF zum Ausprobieren: 

Dieser [35-Seiten-Report](https://reutersinstitute.politics.ox.ac.uk/sites/default/files/2022-09/RISJ%20paper_SimonE_TT22_Final.pdf) von Reuters passt kondensiert so gerade eben noch in GPT3.5 - man kann immerhin kurze Fragen stellen. GPT-4 mit seiner doppelt so hohen Token-Grenze antwortet problemlos, allerdings nicht ganz günstig. 

## Zukünftig Vektor-Datenbank?

Der richtige Weg wäre vielleicht eine "Vektor-Datenbank": Jeden Abschnitt/Absatz in ein Embedding umsetzen lassen - gewissermaßen einen Fingerabdruck der Bedeutungen des Texts - und dann nach passenden Embeddings suchen, diese auslesen und das Modell darüber reden lassen. Dadurch könnte sehr viel Text durchsucht werden - wie man es schafft, dass das Modell gezielt in den Volltext hereinliest, um antworten zu können, muss aber erst noch erprobt werden. 
