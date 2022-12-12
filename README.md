# AATSandraSchlafzimmer

# Use Case - Sandra
### ATGL: Gurbisz, Kindla, Hetlinger & Marjanovic


## Aufgabenstellung: 
Sandra hat eine körperliche Einschränkung und eine starke Sehbeeinträchtigung. Sie hat einen Rollstuhl, einen Laptop und ein SmartPhone. Sie kann Buchstaben nur in dreifacher Größe erkennen, benötigt hohen Kontrast und hat eine Rotsehschwäche (Protanopie). Sie würde gerne eine gewisse Autonomie zurückerlangen und ihre Umgebung (z.B. Licht, Jalousien, Musik) steuern zu können. Darüberhinaus würde sie gerne Klänge erzeugen können und sich die Zeit mit
Computerspielen vertreiben. Sie möchte gerne im Internet surfen oder am Smartphone mit ihren Freunden kommunizieren können.

## Vorhandene Funktionen:
- linker Arm: Daumen+Zeigefinger
- Kopfbewegung
- Mund/Lippen, Saugen/Pusten
- Sprache

## Wunsch
### 1. Umgebungssteuerung
- Steuerung Licht, Temperatur/Jalousien
- Visuals erzeugen 
### 2. Computer
- Internet surfen
- E-Mail schreiben
- Computerspiel spielen
### 3. SmartPhone bedienen
- SMS schreiben
- Anruf tätigen

# Lösung

## Verwendete Komponenten:
- Asterics Grid
- IrTrans (Lampensteuerung) 
- Sprachsteuerung (Siri)
- OpenHab

## Eingabegeräte
### FlipMouse
Was ein FlipMouse ist findet man in dem Link: https://www.asterics-foundation.org/projekte-2/flipmouse/

Die Einstellungen von FlipMouse 
![flipmouse](https://user-images.githubusercontent.com/82451150/207044769-62cf4231-0d89-4890-a417-9a83c328d93c.jpeg)


### Fabi - Flexible Assistive Button Interface
Was ein FABI ist findet man in dem Link: https://www.asterics-foundation.org/projects/fabi/

Die Einstellungen von FABI

![fabi](https://user-images.githubusercontent.com/82451150/207044816-fd619e6f-f019-488f-abd5-8700e2bce462.jpeg)

## Umgebungssteuerung 
### AsTeRICs Grid
Für die Umgebungssteuerung wird ein zentraler OpenHab Server verwendet, um die Beleuchtung zu steuern sowie die Temperatur in der Wohnung des Schlafzimmers zu regeln. 
Desweiteren soll die Beschattung des Wohnzimmers gesteuert werden. 
Es wird das Asterics Grid verwendet, um diese Steuerungen durchzuführen. Die Tatsache, dass Sandra nur ihren Mund bzw. ihre Lippen bewegen kann, ermöglicht die Verwendung einer FlipMouse. 

### Grid-Konfiguration

<img width="769" alt="Screenshot 2022-12-12 193134" src="https://user-images.githubusercontent.com/82451150/207125939-8c902ff3-3527-4bbe-a4b9-e4666c05cdd6.png">


Das Hauptseite -Grid beinhaltet zwei Zimmern und eine Lampensteuerung. Durch das Klicken mit einer Fabi-Button oder das Pusten in die FlipMouse, kann ein Grid ausgewählt werden. Dieses wird zusätzlich laut ausgesprochen und zu einer weiteren Seite des Grids navigiert. Zudem wird eine Asterics Aktion ausgeführt, welches Daten zu einem OpenHab Server sendet. 
Dabei ist es wichtig ein OpenHab Model in der Asterics Configuration Suite (ACS) hochzuladen und anschließend diese mit dem ARE zu verbinden. 
Für eine korrekte Verbindung mit dem OpenHab-Server im Smart Homes Labor ist im ACS der richtige Hostname unter Properties zu vergeben. (Siehe unten) 

![ACS](https://user-images.githubusercontent.com/82451150/207045139-b913a3c3-9a78-4084-918a-08d4bf8dac94.png)

### Asterics Aktion bearbeiten
Um die Smart Homes Elemente durch einem Tastendruck oder durch das Pusten/Saugen in die FlipMouse zu steuern, muss die Asterics Aktion richtig konfiguriert werden.
Als erstes muss eine neue Asterics Aktion angelegt werden. Gleichzeitig sollte das ARE im Hintergrund laufen, damit das Model zum Grid heruntergeladen werden kann. Als nächstes wählt man die Komponente openHAB.1_c und sendet zum Port actionString die richtigen Befehle für die Steuerungen. Im untenstehenden Bild sind die verwendeten Befehle zu sehen.

<img width="874" alt="Screenshot 2022-12-12 211353" src="https://user-images.githubusercontent.com/82451150/207145301-fb54d959-3df2-4711-9489-529160e54b22.png">

![TEMP](https://user-images.githubusercontent.com/82451150/207045532-c48d8cfe-2588-44d1-8498-ea859e8564e3.png)

Ein paar Items wie Temperatur Regelung und das Dimmbares Licht Ein-/Ausschalten sind nicht im Smart Lab integriert und daher nur in der Basic-UI ersichtlich. 

![Basic-UI](https://user-images.githubusercontent.com/82451150/207045320-c5d92357-c189-4b71-82e7-6f52c126ee66.png)


### Schlafzimmer -Grid
Im Schlafzimmer Grid können Beleuchtung oder Temperatur ausgewählt werden. Diese leiten zu einer weiteren Seite, wo die Steuerungen als Asterics Aktionen durchgeführt werden. 
Aufgrund Sandras Sehschwäche wurden große Felder erstellt.

<img width="757" alt="Screenshot 2022-12-12 193404" src="https://user-images.githubusercontent.com/82451150/207126325-125b3e0a-e4ea-4693-8b7b-820795cbc9e9.png">

<img width="770" alt="Screenshot 2022-12-12 193443" src="https://user-images.githubusercontent.com/82451150/207126469-f9323a7b-ecf9-438e-875d-ff53cf21284f.png">

### Temperatur -Grid
Im Temperatur Grid kann zwischen 5, 10, 15 und 22 Grad ausgewählt werden. Weiters gibt es noch die Option eine automatische Nachtabsenkung zu aktivieren oder zu deaktivieren. 

<img width="764" alt="Screenshot 2022-12-12 193530" src="https://user-images.githubusercontent.com/82451150/207126630-66ddc2bb-ab06-439b-9932-6b3d46aadc2e.png">

### Lamp -Grid
Mit diesem Grid kann eine Lampe gesteuert werden. 
Mittels IrTrans Aktuator wurden Infrarot Signale aus der Fernbedienung eingelesen und abgespeichert. Aufgrund Sandras motorischen Beschränkungen wurde im Grid selbst alle wichtigen Tasten des Fernsehers abgebildet. In den untenstehenden Bildern sind die richtigen Einstellungen zu entnehmen. 

<img width="939" alt="Screenshot 2022-12-12 213223" src="https://user-images.githubusercontent.com/82451150/207149441-001b5474-9bce-43c5-b3fd-6d7205cc6320.png">

<img width="757" alt="Screenshot 2022-12-12 193619" src="https://user-images.githubusercontent.com/82451150/207127040-6f04fa51-dc95-443b-a39c-8df61c319ef8.png">
<img width="766" alt="Screenshot 2022-12-12 193635" src="https://user-images.githubusercontent.com/82451150/207127060-f9192f50-666a-4163-8453-7d9ac51a7ead.png">

<img width="761" alt="Screenshot 2022-12-12 193653" src="https://user-images.githubusercontent.com/82451150/207127071-8b3386c4-e8ac-4cb4-b249-6249bc42df86.png">

<img width="761" alt="Screenshot 2022-12-12 193707" src="https://user-images.githubusercontent.com/82451150/207127100-092c51f8-8afb-49a5-90f6-bd9c250b57b5.png">

<img width="776" alt="Screenshot 2022-12-12 211142" src="https://user-images.githubusercontent.com/82451150/207145045-c0338600-4045-4389-be74-47bb10abe72c.png">

### Wohnzimmer -Grid 
Im Wohnzimmer Grid können die Jalousinen hinauf und hinunter navigiert werden. Auch hier musste der richtige Befehl zu dem Port "ActionString" versendet werden, um das gewünschte Ziel zu erreichen.
  
<img width="752" alt="Screenshot 2022-12-12 194140" src="https://user-images.githubusercontent.com/82451150/207127930-4ee52153-0080-4ab3-a9bd-1634fb3b6a85.png">

## Computer
### Accessibility Settings
Für den Wunsch Sandras Computerspiele spielen zu können und Emails zu schreiben wurde ein Windows 11 Laptop verwendet.
Unter dem Feld Barrierefreiheit "Sehen" wurde die Bildschirmlupe um 300% vergrößert und ein Rot-Grün Farbfilter aktiviert. Zudem wurde ebenfalls die Sprachausgabe aktiviert. 
Für eine einfachere Handhabung des Kommunizierns werden Emails über die Sprachassistentin Siri mittels SmartPhones versendet. Als Alternative zum Versenden von Mails kann auch der Computer verwendet werden. Hierfür wird die Bildschirmtastatur mittels FlipMouse angesteuert.

![barierre](https://user-images.githubusercontent.com/82451150/207147829-999fa27f-4e06-480c-b913-4fcf7ad7b4b2.png)
![lupe](https://user-images.githubusercontent.com/82451150/207147841-ce0065e2-7f5e-4c5b-8c7b-463491296256.png)
![farben](https://user-images.githubusercontent.com/82451150/207147888-b07c9dd9-63e8-41f4-8ec4-015dc9975c9d.png)


### Computerspiel
In der Abbildung wurde das Computerspiel "Tunnel Rush" getestet. Auch hier wurde unter Berücksichtigung Sandras Fähigkeiten das Fabi mit zwei Buttons verwendet. Grundsätzlich können alle Spiele gespielt werden, die nur mit linken und rechten Pfeiltasten spielbar sind. 
Die Konfiguration des Fabi Buttons sind oben bei den Eingabegeräten zu entnehmen. 

![spiel](https://user-images.githubusercontent.com/82451150/207044641-8f593b0a-8233-4726-9cc3-c0dda1e3fddf.jpeg)


## SMS schreiben und Anruf tätigen mittels Siri
Das Apple Siri ist eine Sprachassistentin, der für Sandra perfekt geeignet ist, um Anrufe zu tätigen oder Emails zu verschicken. In den Einstellungen muss das erste Feld "Auf Hey Siri achten" aktiviert sein, um nur über die Sprache an Siri Befehle zu übermitteln.
Im untenstehenden Video ist die Kommunikation mit Siri erkennbar.
  

Hier ist zu sehen wie Siri verwendet wird, um einen Anruf zu tätigen und eine SMS zu schreiben.

https://user-images.githubusercontent.com/82451150/207145633-cadf5ec3-eb92-43ae-8d74-db82b25cfa15.mp4

https://user-images.githubusercontent.com/82451150/207145654-16a2ab34-72d2-4f60-a0b3-1bbc685f8ece.mp4

# Ergebnis FitsTask!

![WhatsApp Bild 2022-12-06 um 11 35 07](https://user-images.githubusercontent.com/82451150/207128770-18e05ef0-efab-46fe-b1c8-ba7464df0157.jpg)

Das Ergebnis mit dem besten Throughput wurde im sechsten Versuch erreicht.
 ![WhatsApp Bild 2022-12-06 um 11 34 52](https://user-images.githubusercontent.com/82451150/207128728-46bdd0e6-ea69-41b5-a0fd-f666777c165e.jpg)

Die Sewquenz mit dem schechtesten Throughput ist aus dem unteren Bild zu entnehmen.
![WhatsApp Bild 2022-12-06 um 11 34 57](https://user-images.githubusercontent.com/82451150/207128753-0481deac-f200-4d10-9d04-d7cec5c7bbfb.jpg)
