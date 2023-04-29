# TalkToPDF
GPT-3.5 bzw. GPT-4 liest für Dich (PDF)-Texte und beantwortet deine Fragen zum Text. 

![TalkToPDF-Condense-Demo](./talktopdf-demo.png)

## Was das soll und wie man's macht: 

Mehr dazu [im Blog-Post auf janeggers.tech](https://www.janeggers.tech/eeblog/2023/kann-ich-die-ki-fuer-mich-den-stuckrad-barre-lesen-lassen/)

## Tja, und...?

Klar: das gibt es schon. Wenn man ohnehin ein OpenAI-API-Token hat, kann man zum Beispiel auch [pdfgpt.io](https://pdfgpt.io) nutzen - da kann man ohne weitere Anmeldung Dokumente bis zu 1000 Seiten befragen (mit einer etwas anderen Technik, dazu mehr unten unter "Grenzen"). Das hier ist kein produktionstaugliches Tool, sondern ein Experiment. 

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
Text, Fragen und Antworten müssen in die Token-Grenze passen - das setzt für GPT3.5 (max. 4096 Token) die Grenze bei 3-5 Seiten. (Und dann sind nur noch sehr kurze Fragen und Antworten möglich.) Kondensieren ermöglicht Texte mit bis zu 8-facher Länge - aber so etwa bei 30-40 Seiten ist Schluss. 

Tools, die mehr Seiten können, lösen das mit einem etwas anderen Verfahren: 
- Erstelle für jeden Absatz ein "Embedding" - einen semantischen Fingerabdruck des Textabschnitts, einen Vektor für den Sinn des Textes gewissermaßen.
- Wenn eine Frage gestellt wird, durchsuche eine Datenbank aller Embeddings und fische die raus, die am besten passen. 
- Lade den Volltext der entsprechenden Absätze und - als Kontext - ein paar davor und ein paar danach in GPT-3.5, zusammen mit der Nutzer-Frage. 
Irgendwann mal. 

(Und dann sind da noch die PDFs, die keinen Text enthalten, sondern nur Grafik bzw. abfotografierten Text - anderes Thema. Auch ein andermal.) 

## Beispiel-PDF zum Ausprobieren: 

Dieser [35-Seiten-Report](https://reutersinstitute.politics.ox.ac.uk/sites/default/files/2022-09/RISJ%20paper_SimonE_TT22_Final.pdf) von Reuters passt kondensiert so gerade eben noch in GPT3.5 - man kann immerhin kurze Fragen stellen. GPT-4 mit seiner doppelt so hohen Token-Grenze antwortet problemlos, allerdings nicht ganz günstig. 

## Zukünftig Vektor-Datenbank?

Der richtige Weg wäre vielleicht eine "Vektor-Datenbank": Jeden Abschnitt/Absatz in ein Embedding umsetzen lassen - gewissermaßen einen Fingerabdruck der Bedeutungen des Texts - und dann nach passenden Embeddings suchen, diese auslesen und das Modell darüber reden lassen. Dadurch könnte sehr viel Text durchsucht werden - wie man es schafft, dass das Modell gezielt in den Volltext hereinliest, um antworten zu können, muss aber erst noch erprobt werden. 
