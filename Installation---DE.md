# Installation

## Vorraussetzungen
Grundvorraussetzung für die Nutzung der TU-Design-Klassen ist eine funktionierende Installation einer LaTeX-Distribution.
Üblich sind TeX Live oder MiKTeX.

## Linux
###Vorbemerkung
`$ code` kann von einem normalen Benutzer im Terminal ausgeführt werden.  
`# code` erfordert Administratorrechte.

### Globale Installation
Für Debian und -derivate (wie Ubuntu oder Linux Mint) werden .deb-Pakete angeboten. Für den Normalbenutzer ist die Installation darüber vorzuziehen.

Die globale Installation erfolgt unter Nutzung des Makefiles und GNU Make.
Die nötigen Schritte sind wie folgend:

0. TODO: Schriften installieren
0. Das Repository klonen: `$ git clone https://github.com/bebro/tuddesign.git` 
0. Verzeichnis öffnen: `$ cd tuddesign`
0. Installieren: `# make install`
0. Tex-Tree neu einlesen:  
    TeX Live: `$ texhash`  
    MiKTeX: `$ mktexlsr`
0. Dokumentation erstellen: `$ make doc`
0. Mit Dokumentation erneut installieren: `# make install`

### lokale Installation
Falls Änderungen eingebracht werden sollen, ist eine lokale Installation im home-Verzeichnis des Nutzers empfehlenswert.
Es muss sichergestellt werden, dass die verwendete LaTeX-Distribution, einen lokalen texmf-tree unterstützt.
Bei TeX Live ist dies der Ordner ~/texmf (gespeichert in der Variable TEXMFHOME).
Nach klonen des Git-Repository verlinkt man die Inhalte des texmf-Ordners in den lokalen texmf-tree.
Nach dem Neu-Einlesen des TeX-tree, sind die Klassen verfügbar.
Mittels `$make doc` lässt sich dann noch die Dokumentation bauen.

