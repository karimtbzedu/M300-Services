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

Anstatt vor jedem Titel ein <\h1><\h1> schreiben zu müssen, kann man in Markdown einfach Hashtags setzen.  
\# H1 Titel  
\## H2 Titel  
\###### H6 Titel  

### Systemsicherheit


## K3
### Eingerichtete Umgebung
Als Grundinstallation habe ich mich erstmals für einen Apache2 Webserver mit Webalizer entschieden. 

#### Apache 2 Webserver
Apache ist der <b>meistgenutzte</b> Webserver im Internet. Er ist flexibel konfigurierbar und über eine Vielzahl von Modulen erweiterbar.<sup>1</sup>
  
Das quellfreie Open Source-Produkt wird unter Federführung der Apache Software Foundation fortlaufend weiterentwickelt.<sup>2</sup> Ausserdem ist er leicht zu installieren, was ihn unter anderem so beliebt macht.
  
<sup>1</sup>Quelle [wiki.ubuntuusers.de](https://wiki.ubuntuusers.de/Apache_2.4/)  
<sup>2</sup>Quelle [checkdomain.de](https://www.checkdomain.de/hosting/lexikon/apache/)

#### Webalizer
Das Programm Webalizer dient zur Auswertung der Logdateien, die Webserver auf Basis von Besucheranfragen erstellen. Die Software erzeugt Berichte im HTML-Format, die anschliessend mit einem beliebigen Webbrowser betrachtet werden können.<sup>1</sup>

Mittels den Möglichkeiten in K4 möchte ich dann ein Hardening für den Webserver durchführen.
  
<sup>1</sup>Quelle [wiki.ubuntuusers.de](https://wiki.ubuntuusers.de/Webalizer/)

### Vagrant-Befehle



### Umgebungs-Variablen
### Netzwerkplan
### Sicherheitsaspekte
### Testfälle

## K4
### Sicherheitsaspekte implementieren
#### Firewall inkl. Rules
#### Reverse-Proxy
#### Benutzer- und Rechtevergabe
#### Zugang SSH-Tunnel
#### Sicherheitsmassnahmen


## K5
### Persönliche Lernentwicklung
#### Vorwissen - Wissenszuwachs
#### Reflexion