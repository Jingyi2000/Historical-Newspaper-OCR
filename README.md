# Historical Newspaper OCR Project

## 1. Project Introduction

This project aims to perform efficient layout and text recognition on historical newspaper scans to support parallel reading on websites and create a corpus for language research and the visualization of knowledge graphs. It focuses particularly on processing historical newspaper scans with complex layouts, rich content, and scanning quality below average, using the 1942 newspapers of Freiheitskampf as an example.

After extensive testing of OCR tools, pero-ocr, with its pre-trained Optical Layout Recognition (OLR) and Optical Character Recognition (OCR) models, has been proven to be highly suitable for our needs. Therefore, the core functionalities of this project include image preprocessing of batch historical newspapers and using pero-ocr for layout and text recognition. The recognized layout results will be stored in XML files and further extracted into full text for subsequent research and application.

## 2. Technology Stack/Dependencies

- **OpenCV**: For image processing tasks.
- **Matplotlib**: For data visualization.
- **NumPy**: Provides high-performance multi-dimensional array objects and related operations.
- **SciPy**: For scientific and technical computing.
- **pero-ocr**: A specialized optical character recognition library for document images.
- **Numba**: For accelerating the execution speed of Python code.
- **ConfigParser**: For handling configuration files.
- **XML Processing**: For handling XML data.

## 3. Installation Guide

Ensure the system has Python 3.6 or higher and pip installed. It is recommended to follow the steps below in a virtual environment to avoid potential dependency conflicts.

1. **Create and activate a virtual environment**:
   ```
   python -m venv myenv
   source myenv/bin/activate # Unix or MacOS
   myenv\Scripts\activate # Windows
   ```

2. **Use pip to install all necessary libraries**:
   ```
   pip install numpy opencv-python matplotlib scipy numba configparser xmltodict pero-ocr
   ```

## 4. Usage Instructions

- After completing environment setup and basic installation, start with image preprocessing in the `image_preprocessing` folder. Effect testing on a few test images can be done through `testcase` before proceeding to batch processing. Solutions for potential issues encountered during batch processing are provided in the notebooks.
- After image preprocessing, proceed to `pero_ocr`, download the pre-trained model, and execute the pero-ocr Python package. If problems arise, it is recommended to ask questions on the pero-ocr GitHub page.
- After obtaining the XML files storing the layout and text recognition results, if needed, full text extraction can be performed through `fulltext_extract`.

## 5. References

- O Kodym, M Hradiš: Page Layout Analysis System for Unconstrained Historic Documents. ICDAR, 2021.
- M Kišš, K Beneš, M Hradiš: AT-ST: Self-Training Adaptation Strategy for OCR in Domains with Limited Transcriptions. ICDAR, 2021.
- J Kohút, M Hradiš: TS-Net: OCR Trained to Switch Between Text Transcription Styles. ICDAR, 2021.


## Kurzbeschreibung der Prozessschritte pro Woche

### Woche 9.10 - 15.10
1. Überblick über die Arbeit der vorherigen Praktikanten, Festlegung der Projektziele
2. Lektüre von Leitliteratur in Zotero bezüglich maschinellem Lernen und OCR
3. Erste Validierungsversuche mit dem NewspaperNavigator Modell

### Woche 16.10 - 22.10
1. Über ein eigenes Forschungsthema nachdenken
2. Suche nach geeigneter Software für Texterkennung: [eScriptorium](https://gitlab.com/scripta/escriptorium)
3. Erstellung einer Zeitplanung und Klarstellung der Arbeitsschritte

### Woche 23.10 - 29.10
1. Das Forschungsthema formulieren: „Der Freiheitskampf“ im Kontext der Endphase des NS-Regimes (1942-1945): Eine korpusbasierte Untersuchung der lexikalischen Strategien zur Propaganda 
2. 2 Seite aus 1942 auf eScriptorium erstmal segmentieren und manuell korrigieren (als GT)

### Woche 30.10 - 5.11
1. Versuch des Trainings auf 3 Seite als GT in eScriptorium gescheitert -> Warte auf neuen PC und versuche, ein Webkonto zu beantragen.
2. Nutzung von gleichzeitigen Zeitungen als Referenzkorpus, die aus Zeitraum 1942-1953 auf Deutsches Zeitungsportal [Deutsches Zeitungsportal](https://www.deutsche-digitale-bibliothek.de/newspaper) -> Einsatz eines Crawlers und Auswahl der Zeitungen
3. Lesen von Fachliteratur zur historischen Korpuslinguistik

### Woche 5.11 - 12.11
1. Anfragen bei Herrn Lasch und Herrn Würzner nach Zugangsberechtigung zum eScriptorium-Webkonto (aufgrund der Art abgelehnt), direkt bei eScriptorium um ein Konto bitten (bisher keine Antwort erhalten). Vorteil des eScriptorium-Webkontos: öffentlich verfügbare vortrainierte Modelle (auf lokal gibt's nichts)
2. Nutzen des vortrainierten Modells von [PERO-OCR](https://pero-ocr.fit.vutbr.cz/ocr/show_results/90a706d0-62c4-42b9-8ecc-092222fc9402/d68bd829-a616-4aa6-9cb0-32affc094234) für OLR und OCR mit sehr guten Ergebnissen, aber Nachteil: vortrainierte Modelle nicht öffentlich verfügbar, nur online nutzbar
3. Verwenden von PERO-OCR exportierten GT in eScriptorium für das Training des Modells, Genauigkeit von 69% bei 20 Seiten GT -> Überlegung zur Optimierung des Arbeitsablaufs, besonders Umgang mit großen Datenmengen

### Woche 13.11 - 19.11
1. Nutzungszugang für die Instanz der UB Mannheim durch Kontakt mit Frau Will erhalten, aber die Erkennungsleistung ist nicht so gut wie bei PERO-OCR -> Verzicht auf die eScriptorium Plattform und Nutzung des darauf basierenden Programms Kraken
2. Weiteres Lernen der Anwendung von OCR-D und Entwurf des gesamten Arbeitsablaufs
3. Erste Entwürfe für das Poster des Leipzig DH Tages

### Woche 20.11 - 26.11
1. Auswahl zwischen OCR-D, Kraken-OCR und PERO-OCR -> Überlegung von Kombination verschiedener Tools
2. Für Modelltraining bietet PERO-OCR bessere vortrainierte Modelle -> Möglichkeit, auf deren Grundlag anzupassen
3. Fertigstellung des Posters

### Woche 27.11 - 03.12
1. Durchsicht und Ausprobieren von PERO-OCRs Github: [Methoden und Funktionen](https://github.com/DCGM/pero-ocr/issues/26) klar, aber Schwierigkeiten beim Verstehen des Workflows
2. PERO-OCR bietet keinen spezifischen Prozess für das Training von Modellen an -> schwierig, auf dieser Basis eigene Modelle zu trainieren -> Anfrage um Unterstützung bei [PERO-OCR](https://kandi.openweaver.com/python/DCGM/pero-ocr#Community-Discussions)
3. Lernen der Nutzung von PyTorch für Machine Learning durch [Videos](https://www.bilibili.com/video/BV1gU4y1r7Ku/?p=9&vd_source=0e71679c4395d829ea9700ae7bb124ec) sowie Hands-on Practice und gleichzeitiges Nachholen von Crash-Kursen in linearer Algebra
4. Vorbereitung der Präsentation für den DH Tag

### Woche 04.12 - 10.12
1. Teilnahme am DH-Tag in Leipzig war bedeutend. Unser Projekt weckte großes Interesse. Besonders interessant: Projeket Text plus (eine Erweiterung des CLARIN-D-Projekts, die umfangreiche Textkorpora und Analysetools bietet.
2. Verwenden den OpenCV Konturerkennungsalgorithmus, um die gescannten Teile zuzuschneiden und zu neigen. Der Erkennungseffekt ist sehr gut [testcase](Bildvorverarbeitung/testcase.ipynb) -> warten auf Massenverarbeitung 

### Woche 11.12 - 19.12
1. Anwendung des in testcase verwendeten Algorithmus auf die Dateien aus dem Jahr 1942 auf dem neuen Rechner, entdeckt, dass Bilder mit schlammgrauen rechteckigen Blöcken die Erkennungsergebnisse erheblich beeinträchtigen -> mehrere Versuche des Zuschneidens und der Parameteranpassung führten zur Entdeckung eines neuen Erkennungsalgorithmus [image_crop](Bildvorverarbeitung/image_crop.ipynb)
2. Aufgrund anhaltender Probleme mit der Schrägkorrektur-Funktion wurde vorübergehend auf diese Funktion verzichtet, denn das hat keinen signifikanten Einfluss auf die nachfolgende Texterkennung.
3. Die erste [Massenverarbeitung](Bildvorverarbeitung/massen_image_crop.ipynb) auf dem neuen Computer ergab nicht zufriedende Ergebnisse, wobei etwa weniger als 60 % korrekt verarbeitet wurden. Es gab jedoch noch 40 % Fehler bei der Seitenaufteilung.

### Woche 08.01 - 12.01
1. Frühere fehlerhafte Analyse: Feste Parameter sind nicht geeignet für komplexe Scans, daher wurde ein neues Verfahren für die Massenverarbeitung entwickelt: Anwendung unterschiedlicher Algorithmen mit verschiedenen Parametern je nach Situation.
2. Die Scans von Dezember 1942 wurden mit dem neuen Verfahren bearbeitet, wobei eine Genauigkeit von bis zu 95% erreicht wurde. Einzelne Fehler wurden manuell zugeschnitten.

### Woche 15.01 - 19.01
1. Überprüfen erneut die Ergebnisse der Bildvorverarbeitung und passen Sie einzelne Bilder manuell an.
2. Führen den Layout- und Textanalyseprozess mit PERO OCR durch, [Schwierigkeiten](https://gitlab.hrz.tu-chemnitz.de/praktikum_2023/layout_analysis_new/-/blob/main/PERO%20OCR/intallation&test.ipynb?ref_type=heads) im Bereich der Konfiguration der Umgebung, insebesondere bei Versionskonflikte zwischen Pakete.
3. Die obige Frage wurde an das PERO OCR-Team auf [Github](https://github.com/DCGM/pero-ocr/issues/58) gestellt.

### Woche 22.01 - 26.01
1. Durch Herabstufung der Paketversionen wurde die Integration von PERO OCR erfolgreich durchgeführt und die Massenverarbeitung durchgeführt.
2. Extraktion der Textinformationen aus den Ergebnissen und Speicherung in separaten txt-Dokumenten für die nachfolgende Analyse.
3. Durchführung der Abschlussgespräche und Beginn einer Reihe von Abschlussarbeiten.
4. Eine [Antwort](https://github.com/DCGM/pero-ocr/issues/58) vom PERO OCR-Team wurde erhalten, die Lösung besteht darin, den Entwicklungsbranch zu verwenden.

### Woche 07.02 - 09.02
1. Optimierung der Dokumentation, einschließlich Hinzufügen von Codekommentaren, Verfassen von README-Dokumenten, Entfernen unnötiger Dateien
2. Entwurf des Inhalts zum Blogartikel „Denken ohne Geländer“ 
