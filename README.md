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
- Fernseher 
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
- IrTrans (Fernsehersteuerung) 
- Sprachsteuerung (Siri)
- OpenHab

## Eingabegeräte
### FlipMouse
Was ein FlipMouse ist findet man in dem Link: https://www.asterics-foundation.org/projekte-2/flipmouse/

Die Einstellungen von FlipMouse 


### Fabi - Flexible Assistive Button Interface
Was ein FABI ist findet man in dem Link: https://www.asterics-foundation.org/projects/fabi/

Die Einstellungen von FABI


## Umgebungssteuerung 
### AsTeRICs Grid
Für die Umgebungssteuerung wird ein zentraler OpenHab Server verwendet, um die Beleuchtung zu steuern sowie die Temperatur in der Wohnung des Schlafzimmers zu regeln. 
Desweiteren soll die Beschattung des Wohnzimmers gesteuert werden. 
Es wird das Asterics Grid verwendet, um diese Steuerungen durchzuführen. Die Tatsache, dass Sandra nur ihren Mund bzw. ihre Lippen bewegen kann, ermöglicht die Verwendung einer FlipMouse. 

### Grid-Konfiguration


Das Hauptseite -Grid beinhaltet zwei Zimmern und eine Mediensteuerung. Durch das Klicken mit einer Fabi-Button oder das Pusten in die FlipMouse, kann ein Grid ausgewählt werden. Dieses wird zusätzlich laut ausgesprochen und zu einer weiteren Seite des Grids navigiert. Zudem wird eine Asterics Aktion ausgeführt, welches Daten zu einem OpenHab Server sendet. 
Dabei ist es wichtig ein OpenHab Model in der Asterics Configuration Suite (ACS) hochzuladen und anschließend diese mit dem ARE zu verbinden. 
Für eine korrekte Verbindung mit dem OpenHab-Server im Smart Homes Labor ist im ACS der richtige Hostname unter Properties zu vergeben. (Siehe unten) 



### Asterics Aktion bearbeiten
Um die Smart Homes Elemente durch einem Tastendruck oder durch das Pusten/Saugen in die FlipMouse zu steuern, muss die Asterics Aktion richtig konfiguriert werden.
Als erstes muss eine neue Asterics Aktion angelegt werden. Gleichzeitig sollte das ARE im Hintergrund laufen, damit das Model zum Grid heruntergeladen werden kann. Als nächstes wählt man die Komponente openHAB.1_c und sendet zum Port actionString die richtigen Befehle für die Steuerungen. Im untenstehenden Bild sind die verwendeten Befehle zu sehen.



Einpaar Items wie Temperatur Regelung und das Dimmbares Licht Ein-/Ausschalten sind nicht im Smart Lab integriert und daher nur in der Basic-UI ersichtlich. 



### Schlafzimmer -Grid
Im Schlafzimmer Grid können Beleuchtung oder Temperatur ausgewählt werden. Diese leiten zu einer weiteren Seite, wo die Steuerungen als Asterics Aktionen durchgeführt werden. 
Aufgrund Sandras Sehschwäche wurden große Felder erstellt.




### Temperatur -Grid
Im Temperatur Grid kann zwischen 5, 10, 15 und 22 Grad ausgewählt werden. Weiters gibt es noch die Option eine automatische Nachtabsenkung zu aktivieren oder zu deaktivieren. 



### Mediensteuerung -Grid
Mit diesem Grid kann der Fernseher gesteuert werden. 
Mittels IrTrans Aktuator wurden Infrarot Signale aus der Fernbedienung eingelesen und abgespeichert. Aufgrund Sandras motorischen Beschränkungen wurde im Grid selbst alle wichtigen Tasten des Fernsehers abgebildet. In den untenstehenden Bildern sind die richtigen Einstellungen zu entnehmen. 




### Wohnzimmer -Grid 
Im Wohnzimmer Grid können die Jalousinen hinauf und hinunter navigiert werden. Auch hier musste der richtige Befehl zu dem Port "ActionString" versendet werden, um das gewünschte Ziel zu erreichen.
  


## Computer
### Accessibility Settings
Für den Wunsch Sandras Computerspiele spielen zu können und Emails zu schreiben wurde ein Windows 11 Laptop verwendet.
Unter dem Feld Barrierefreiheit "Sehen" wurde die Bildschirmlupe um 300% vergrößert und ein Rot-Grün Farbfilter aktiviert. Zudem wurde ebenfalls die Sprachausgabe aktiviert. 
Für eine einfachere Handhabung des Kommunizierns werden Emails über die Sprachassistentin Siri mittels SmartPhones versendet. Als Alternative zum Versenden von Mails kann auch der Computer verwendet werden. Hierfür wird die Bildschirmtastatur mittels FlipMouse angesteuert.



### Computerspiel
In der Abbildung wurde das Computerspiel "Tunnel Rush" getestet. Auch hier wurde unter Berücksichtigung Sandras Fähigkeiten das Fabi mit zwei Buttons verwendet. Grundsätzlich können alle Spiele gespielt werden, die nur mit linken und rechten Pfeiltasten spielbar sind. 
Die Konfiguration des Fabi Buttons sind oben bei den Eingabegeräten zu entnehmen. 



## SMS schreiben und Anruf tätigen mittels Siri
Das Apple Siri ist eine Sprachassistentin, der für Sandra perfekt geeignet ist, um Anrufe zu tätigen oder Emails zu verschicken. In den Einstellungen muss das erste Feld "Auf Hey Siri achten" aktiviert sein, um nur über die Sprache an Siri Befehle zu übermitteln.
Im untenstehenden Video ist die Kommunikation mit Siri erkennbar.
  

Hier ist zu sehen wie Siri verwendet wird, um einen Anruf zu tätigen und eine SMS zu schreiben.




# Ergebnis FitsTask!

Das Ergebnis mit dem besten Throughput wurde bereits im zweiten Versuch erreicht.
 
Die Sewquenz mit dem schechtesten Throughput ist aus dem unteren Bild zu entnehmen.
