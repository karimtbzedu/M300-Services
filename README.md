# Dokumentation M300 LB02
## Von Karim Darwiche

## Inhaltsverzeichnis

  - [K1](#k1)
  - [K2](#k2)
    - [Persönlicher Wissenstand](#persönlicher-wissenstand)
    - [Linux](#linux)
    - [Virtualisierung](#virtualisierung)
    - [Vagrant](#vagrant)
    - [Versionsverwaltung / Git](#versionsverwaltung--git)
    - [Mark Down](#mark-down)
    - [Systemsicherheit](#systemsicherheit)
  - [K3](#k3)
    - [Eingerichtete Umgebung](#eingerichtete-umgebung)
    - [Vagrant-Befehle](#vagrant-befehle)
    - [Umgebungs Variablen](#umgebungs-variablen)
    - [Netzwerkplan](#netzwerkplan)
    - [Sicherheitsaspekte](#sicherheitsaspekte)
    - [Testfälle](#testfälle)
  - [K4](#k4)
    - [Sicherheitsaspekte implementieren](#sicherheitsaspekte-implementieren)
      - [Firewall inkl. Rules](#firewall-inkl-rules)
      - [Reverse-Proxy](#reverse-proxy)
      - [Benutzer- und Rechtevergabe](#benutzer--und-rechtevergabe)
      - [Zugang SSH-Tunnel](#zugang-ssh-tunnel)
      - [Sicherheitsmassnahmen](#sicherheitsmassnahmen)
  - [K5](#k5)
    - [Persönliche Lernentwicklung](#persönliche-lernentwicklung)
      - [Vorwissen - Wissenszuwachs](#vorwissen---wissenszuwachs)
      - [Reflexion](#reflexion)

## K1
Auf meinem Notebook habe ich die folgenden Programme eingerichtet:
1. VirtualBox (inkl. Ubuntu VM)
2. Vagrant
3. Visualstudio-Code
4. Git-Client
5. SSH-Key für Client erstellt

## K2
### Persönlicher Wissenstand
### Linux
Linux ist lediglich der Kernel des Betriebssystems und ist für die Kommunikation zwischen Hardware und Software zuständig.
Die GUI baiserten Desktops werden dann mit Linux-Distrubutionen erstellt.

### Virtualisierung
Unter Virtualisierung verstehe ich das Bereitstellen von Hardware, um eine virtuelle Maschine laufen zu lassen. Was im Endeffekt auf der Maschine betrieben wird spielt dabei keine Rolle. Es kann also etwas GUI basiertes, ein Server oder irgend ein Desktop sein.

### Vagrant
Im Prinzip kann Vagrant Virtualisierungshosts, wie bspw. in diesem Modul VirtualBox fernsteuern. Der Benutzer spart viel Zeit durch Vagrant, da die Erstellung einer VM anhand einer Konfig Datei automatisiert wird.

### Versionsverwaltung / Git
Die Versionsverwaltung im Git ermöglicht es einem Benutzer, ältere Dateien abzurufen. Falls man als Autor etwas gelöscht hat, kann man die benötigten Informationen ganz leicht aus einer älteren Version wiederherstellen.

### Markdown
Markdown ist ein einfacher Text zu HTML übersetzer, der für Web Autoren erstellt wurde. Es erlaubt einem, auch Offline Texte zu schreiben und diese dann sobald man eine Internetverbindung hat leicht zu publizieren. 

Anstatt, dass man alles mühsam in HTML schreiben muss, wurde ein ganz leichter Code entwickelt, welcher es dem Benutzer erlaubt, gleich wie in HTML zu schreiben.  
  
<b>Beispiel</b>  
Anstatt vor jedem Titel ein <'h1><\h1> schreiben zu müssen, kann man in Markdown einfach Hashtags setzen.  
\# H1 Titel  
\## H2 Titel  
\###### H6 Titel  

### Systemsicherheit

## K3
### Eingerichtete Umgebung
Als Grundinstallation habe ich mich vorerst für einen Apache2 Webserver mit Webalizer entschieden. 
Diese Umgebung wird dann in K4 aussreichend gehardet.

#### Apache 2 Webserver
Apache ist der <b>meistgenutzte</b> Webserver im Internet. Er ist flexibel konfigurierbar und über eine Vielzahl von Modulen erweiterbar.<sup>1</sup>
  
Das quellfreie Open Source-Produkt wird unter Federführung der Apache Software Foundation fortlaufend weiterentwickelt.<sup>2</sup> Ausserdem ist er leicht zu installieren, was ihn unter anderem so beliebt macht.
  
<sup>1</sup>Quelle [wiki.ubuntuusers.de](https://wiki.ubuntuusers.de/Apache_2.4/)  
<sup>2</sup>Quelle [checkdomain.de](https://www.checkdomain.de/hosting/lexikon/apache/)

#### Installation Apache 2

Die Installation stellt sich als äusserst einfach raus.

1. Paketquellen von Ubuntu aktualisieren
`sudo apt-get update`

2. Nun wird Apache installiert. Das Argument -y bewirkt, dass keine manuelle Eingabe benötigt wird.
`sudo apt-get install -y apache2`

Testen kann man das ganze mit `curl http://localhost`

#### Webalizer
Das Programm Webalizer dient zur Auswertung der Logdateien, die Webserver auf Basis von Besucheranfragen erstellen. Die Software erzeugt Berichte im HTML-Format, die anschliessend mit einem beliebigen Webbrowser betrachtet werden können.<sup>1</sup>

Mittels den Möglichkeiten in K4 möchte ich dann ein Hardening für den Webserver durchführen.
  
<sup>1</sup>Quelle [wiki.ubuntuusers.de](https://wiki.ubuntuusers.de/Webalizer/)

#### Installation Webalizer
1. Paketquellen von Ubuntu aktualisieren
`sudo apt-get update`

2. Nun wird Webalizer installiert. Das Argument -y bewirkt, dass keine manuelle Eingabe benötigt wird.
`sudo apt-get install -y webalizer`

### Vagrant-Befehle

`vagrant init` Vagrantfile anlegen  
`vagrant up` Vagrant-VM starten  
`vagrant ssh` Eine SSH-Verbindung zur VM aufbauen  
`vagrant status` Zeigt den aktuellen Status der VM an  
`vagrant port` Zeigt die Weitergeleiteten Ports der VM an  
`vagrant halt` Stoppt die VM  
`vagrant destroy` Löscht die VM  

#### Vagrant VM erstellen

1. Zuerst einen neuen Ordner erstellen, in der die VM dann abgelegt wird.
`mkdir MeineVagrantVM`

2. Dann mit `cd` in den neu erstellten Ordner wechseln.
`cd MeineVagrantVM`

3. In diesem Ordner eine neue Vagrant VM inkl. Vagrantfile erstellen. In unserem Fall Ubuntu.
`vagrant init ubuntu/xenial64`

Die VM wird nun erstellt.

### Netzwerkplan
#### Netzwerkplan Funktion Vagrant
![Netzwerkplan-1](https://i.ibb.co/KVhZRw6/vagrant-netzwerkdesign.png "")

#### Netzwerkplan meine Umgebung
![Netzwerkplan-2](https://i.ibb.co/y6nT1WC/networkplan-det.png "Logo Title Text 1")

### Sicherheitsaspekte
### Testfälle

## K4
### Sicherheitsaspekte implementieren
Ich habe eine Firewall mit Rules erstellt und einen Reverse-Proxy eingerichtet. Zudem habe ich die Benutzer- und Rechtevergabe, SSH-Tunnel und Sicherheitsmassnahmen dokumentiert.
#### Firewall inkl. Rules

1. Ich habe zuerst die Firewall installiert:  
   `sudo apt-get install ufw`  

Vor dem aktivieren habe ich aber die Rules erstellt.

1. Rules habe ich so erstellt:  
`sudo ufw allow from [Source IP] to [Destination IP oder any] port [Port-Nummer]`

Hier die Firewall-Rule Tabelle, die laufend aktualisiert wird. Im ersten Schritt habe ich SSH und MySQL aktiviert.
| IP       | Port | Protokoll | Beschreibung     | Direction | Ziel |
|----------|------|-----------|------------------|-----------|------|
| 10.0.0.2 | 22   | TCP/UDP   | SSH Zugang       | <->       | any  |
| 10.0.0.2 | 3306 | TCP/UDP   | MySQL Zugang Web | ->        | any  |
| 10.0.0.2 | 80   | TCP       | HTTP             | ->        | any  |
|          |      |           |                  |           |      |
|          |      |           |                  |           |      |

3. Die Firewall musste ich nach dem erstellen noch aktivieren:  
`sudo ufw enable`

#### Reverse-Proxy

1. Den Reverse-Proxy habe ich mit dem folgenden Befehl installiert:  
   `sudo apt-get install libxml2-dev`

2. Nun habe ich drei Module aktiviert:  
   `sudo a2enmod proxy`
   `sudo a2enmod proxy_html`
   `sudo a2enmod proxy_http`

3. Die Konf-Datei von Apache2 /etc/apache2/apache2.conf musste ich mit folgendem ergänzen:
   `ServerName localhost`

4. Danach habe ich den Apache2 Dienst neugestartet.
   `sudo service apache2 restart`

Sollte ich jetzt eine Konfig machen wollen, kann ich das z.B in /etc/apache2/sites-enabled/001-reverseproxy.conf machen.
![Reverse-Proxy](https://i.ibb.co/xSFq5xD/Bild1.png "Logo Title Text 1"

#### Benutzer- und Rechtevergabe

#### Benutzer
In Linux gibt es unterschiedliche Bentuzer, Gruppen und Rechte im Filesystem. Dateien werden einem Benutzer und einer Gruppe zugeordnet. Während man in mehreren Gruppen sein kann, gibt es immer eine primäre Gruppe in dem ein Benutzer sein kann.  
  
Beim Anmelden wird sich mit Benutzername und Kennwort angemeldet. Alle Aktionen (bspw. ein Programm starten) die man ausführt werden mit den Rechten gemacht die dem Benutzer zugeordnet wurden.

Der Benutzer root ist im System allmächtig und kann jedes Recht brechen. Zu bestimmten Administrativen Funktionen ist nur der root-Benutzer berechtigt. Generell kennt Linux nur 2 Arten von Benutzern: root und normale Benutzer, zusätzliche Zwischenabstufungen gibt es nicht, es ist jedoch möglich normalen Benutzern erweiterte Befugnisse zu geben (mit dem Programm sudo).
Für einige Prozesse und Dienste gibt es zusätzliche Benutzer.

| Benutzername     | Funktion |
|------------------|-------------|
| root  | Der Systemverwalter unter Linux   |
| nobody  | Wird von Prozessen als Benutzererkennung verwendet, wenn nur ein Minimum an Rechten vergeben werden soll |
| cupsys  | Benutzer des Druckdienstes CUPS   |
| www-data  | Benutzer des Webservers Apache    |
	
#### Gruppen
Gruppen lassen sich ähnlich wie Benutzer anlegen, ändern oder löschen.  
1. Gruppe anlegen: `groupadd`
2. Gruppe ändern: `groupmod`
3. Gruppe löschen: `groupdel`

Beispiele:  
`groupadd webadmin`  
Dies legt die Gruppe webadmin an.
  
`groupdel webadmin`  
Dies löscht die Gruppe wieder.  

`group beispieluser1`
So kann man herausfinden, in welchen Gruppen ein Bentuzer Mitglied ist.  

Nun gibt es primäre und sekundäre Gruppen. Wie bei Kapitel Benutzer bereits erklärt, kann ein Benutzer nur in einer Gruppe primäres Mitglied sein. Er kann dafür in beliebig vielen sekundären Gruppen sein.
  
Wenn eine neue Datei angelegt wird, müssen diese nicht nur einem Benutzer, sondern auch einer Gruppe zugeordnet werden. Hierzu wird die primäre Gruppe benutzt. Neu angelegte Dateien gehören also immer zur primären Gruppe des Benutzers der diese Datei angelegt hat. 

#### Dateisystem
Jede Datei und jedes Verzeichnis in einem Linux-System hat 3 Berechtigungen, die für alle 3 Eigentümer definiert sind.
  
<b>Lesen (r):</b> Diese Berechtigung gibt die Berechtigung, eine Datei zu öffnen und zu lesen. Leseberechtigung auf ein Verzeichnis gibt die Möglichkeit, dessen Inhalt aufzulisten.
  
<b>Schreiben (w):</b> Die Schreibberechtigung gibt die Berechtigung, den Inhalt einer Datei zu ändern. Die Schreibberechtigung für ein Verzeichnis gibt die Berechtigung, in dem Verzeichnis gespeicherte Dateien hinzuzufügen, zu entfernen und umzubenennen. 
      
<b>Ausführen (x):</b> Unter Unix/Linux kann man ein Programm nur ausführen, wenn die Ausführungserlaubnis gesetzt ist. Wenn die Ausführungsberechtigung nicht gesetzt ist, kann man den Programmcode möglicherweise trotzdem sehen/ändern (vorausgesetzt, man hat Lese- und Schreibberechtigung), aber nicht ausführen.

Mit dem Befehl `ls -l` kann man die Berechtigung für eine Datei oder ein Verzeichnis ansehen.

Output: `-rw-r--r--`

Der Output ist so aufgebaut, dass zuerst die Berechtigung für den Benutzer, danach für die Gruppe und dann für andere Benutzer angezeigt wird.

Um eine Berechtigung zu setzen, kann man den Befehl `chmod berechtigung dateiname` benutzen.

Es gibt zwei Möglichkeiten, wie man den Befehl benutzen kann:  
1. Absolute Mode
2. Symbolic Mode

Ich zeige nun den Absoluten Modus, da dieser viel einfacher ist. 

Beispiel: `chmod 764 apache2.conf`

Benutzer (Besitzer): R+W+E (Lesen,Schreiben,Ausführen)  
Gruppe: R+W (Lesen und ausführen)  
Alle: R (Lesen)  

| Nummer  |	Berechtigungs-Typ |	Symbol |
| ------- |-------------------|--------|
| 0 	    | Keine Berechtigung 	  |   ---
| 1  	    | Execute 	        |  --x
| 2 	    | Write 	          |  -w-
| 3 	    | Execute + Write 	|  -wx
| 4 	    | Read 	            |  r--
| 5 	    |  Read + Execute 	|     r-x 
| 6 	    | Read +Write 	    |    rw
| 7 	    | Read + Write +Execute | rwx

<b>Hauptverzeichnise</b>
  
`/bin` ein Ort für die am häufigsten verwendeten Terminal-Befehle, wie ls, mount, rm, etc.
  
`/boot` enthält Dateien, die zum Starten des Systems benötigt werden, (bspw. der Linux-Kernel)
  
`/dev` enthält alle Gerätedateien, bei denen es sich nicht um reguläre Dateien handelt, sondern die stattdessen auf verschiedene Hardware-Geräte verweisen

`/etc` enthält systemweite Konfigurationsdateien, die das Systemverhalten für alle Benutzer beeinflussen.

`/home` das persönliche Verzeichnis für den Benutzer.

`/lib` enthält sehr wichtige dynamische Bibliotheken und Kernel-Module

`/media` ist als Einhängepunkt für externe Geräte wie Festplatten oder Wechselmedien (Disketten, CDs, DVDs) gedacht.

`/mnt` ist ebenfalls ein Ort für Mount-Punkte, aber speziell für "temporär gemountete" Geräte, wie z.B. Netzwerk-Dateisysteme.

`/opt` kann verwendet werden, um zusätzliche Software für Ihr System zu speichern, die nicht vom Paketmanager verwaltet wird.

`/proc` ist ein virtuelles Dateisystem, das einen Mechanismus für den Kernel bietet, um Informationen an Prozesse zu senden.

`/root` ist das Home-Verzeichnis des Superusers

`/run` ist ein temporäres Dateisystem, das früh im Boot-Prozess verfügbar ist und in dem flüchtige Laufzeitdaten gespeichert werden. Dateien unter diesem Verzeichnis werden zu Beginn des Boot-Prozesses entfernt.

`/sbin` enthält wichtige administrative Befehle, die im Allgemeinen nur vom Superuser verwendet werden sollten.

`/srv` kann Datenverzeichnisse von Diensten wie HTTP (/srv/www/) oder FTP enthalten.

`/sys` ist ein virtuelles Dateisystem, auf das zugegriffen werden kann, um Informationen über die Sicht des Kernels auf das System einzustellen oder zu erhalten.

`/tmp` ist ein Ort für temporäre Dateien, die von Anwendungen verwendet werden.

`/usr` enthält die Mehrzahl der Benutzer-Dienstprogramme und Anwendungen und repliziert teilweise die Wurzelverzeichnisstruktur, z.B. mit unter anderem /usr/bin/ und /usr/lib.

`/var` ist variablen Daten gewidmet, wie z.B. Protokollen, Datenbanken, Websites und temporären Spool-Dateien (E-Mail usw.), die von einem Bootvorgang zum nächsten bestehen bleiben. Ein bemerkenswertes Verzeichnis, das es enthält, ist /var/log, in dem Systemprotokolldateien aufbewahrt werden. 

#### Zugang SSH-Tunnel


#### Sicherheitsmassnahmen


## K5
### Persönliche Lernentwicklung
#### Vorwissen - Wissenszuwachs
#### Reflexion
### Quellenverzeichnis

1. [wiki.ubuntuusers.de - Apache 2.4](https://wiki.ubuntuusers.de/Apache_2.4/)  
2. [checkdomain.de - Apache](https://www.checkdomain.de/hosting/lexikon/apache/)
3. [wiki.ubuntuusers.de - Webalizer](https://wiki.ubuntuusers.de/Webalizer/)
4. [maruweb.de- Linux](http://dozent.maruweb.de/material/benutzer.shtml)
5. 