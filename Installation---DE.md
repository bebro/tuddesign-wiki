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

## Windows 7

###MikTeX 2.9

####Vorbemerkung

Um unter windows 7 64bit Probleme mit der Installation von fehlenden Paketen zu vermeiden, muss man bei der Installation von MikTeX unter dem punkt "install missing packages on the fly" auf jeden Fall "yes" anklicken.  
die Option "ask me first" führt dann bei texcniccenter zu Problemen, da sich warum auch immer das Pop-up Fenster nicht öffnen kann. Dann hängt sich pdf-latex mit der Fehlermeldung  
>pdflatex.exe GUI framework cannot be initialized  

auf und es wird kein pdf-Dokument erzeugt.  
Mit dem oben genannten Haken bei "yes" kann man dem ganzen aus dem Weg gehen. Allerdings funktioniert das manchmal nur bei einer Neuinstallation von MikTeX. Nachträglich diese Einstellung unter **start/MikTeX 2.8/maintenance (admin)/settings (admin)** zu ändern funktionierte nicht immer.

####Installation

In einen beliebigen Ordner die Zip-Dateien mit den Schriftarten (**tudfonts-tex_current.zip**) und dem TUD-Design (**latex-tuddesign_current.zip**) und evt. fachbereichs-spezifische Vorgaben für Abschlussarbeiten (**latex-tuddesign-thesis_current.zip**) herunterladen und entpacken. Aus den zwei (bzw. drei) Ordnern einen machen (Unterordner mit gleichem Namen zusammenfassen).  
_Vorsicht! Ordner mit Leerzeichen im Namen unbedingt vermeiden! Leerzeichen müssen gesondert behandelt werden (Überbleibsel der 80er Jahre) und sind generell eine schlechte Idee._  

0. Eine Konsole mit Administrator-Rechten öffnen (z. B. mit der Eingabe von runas /user:Administrator cmd unter Ausführen im Startmenü)
0. In das Verzeichnis wechseln, in dem das eben entpackte texmf-Verzeichnis liegt (mit `cd <DIR>`).
0. Den Ordner **texmf\fonts\map\dvipdfm** inklusive seines Inhalts löschen.
`rmdir /Q /S "texmf\fonts\map\dvipdfm`
0. Kopieren der Unterverzeichnisse von texmf in den Ordner %PROGRAMFILES%\tuddesign\.
`xcopy texmf "%PROGRAMFILES%\tuddesign" /E /I`
0. Dannach den Befehl
`mo_admin`
ausführen.
0. Zum Reiter Roots wechseln, den [add]-Knopf drücken und das Verzeichnis **%PROGRAMFILES%\tuddesign** auswählen. Dann auf [OK] drücken.

  _Im Unterschied zur Installation unter MikTeX 2.8 werden folgende Befehle nicht in der Admin-Konsole ausgeführt, sonder in einer gewöhnlichen, also z. B. mit der Eingabe von cmd unter Ausführen im Startmenü._

0. Dann in der Konsole den Befehl
`initexmf --update-fndb`
ausführen.
0. Den Befehl
`initexmf --edit-config-file=updmap`
ausführen. 
0. Folgende Zeilen in die sich öffnende Datei einfügen und speichern:

  >Map 5ch.map  
  >Map 5fp.map  
  >Map 5sf.map

  _Entspricht dem Inhalt der Datei updmap.d\20tex-tudfonts.cfg._
    
0. Dann den Befehl
`initexmf --mkmaps`
ausführen.

0. Danach funktioniert es manchmal, dass aber zuverlässig. Happy Working! :-)

####Wenn es nicht fuktioniert hat

Häufig hilft es mit dem Paketmanager (admin) 
**mpm_mfc_admin**
ein beliebiges Paket zu installieren. Auch ein reboot kann nicht schaden, da MikTeX Options in der registy einträge ändert.

####Kontrollmöglichkeit für die Schriftarten

Sollte es zu Problemen mit den Schriftarten kommen, empfiehlt sich ein Blick in die Datei psfonts.map, die man unter
**C:\Dokumente und Einstellungen\All Users\Anwendungsdaten\MikTeX\2.8\dvips\config**
findet. In ihr sollten folgende Einträge, i. d. R. in den ersten Zeilen zu finden sein:

>5chb8r Charter-Bold "TeXBase1Encoding ReEncodeFont" <8r.enc <5chb8a.pfb  
>5chbo8r Charter-Bold "TeXBase1Encoding ReEncodeFont 0.167 SlantFont" <8r.enc <5chb8a.pfb  
>5chr8r Charter "TeXBase1Encoding ReEncodeFont" <8r.enc <5chr8a.pfb  
>5chri8r Charter-Italic "TeXBase1Encoding ReEncodeFont" <8r.enc <5chri8a.pfb  
>5chro8r Charter "TeXBase1Encoding ReEncodeFont 0.167 SlantFont" <8r.enc <5chr8a.pfb  
>5fpm8r FrontPageMedium "TeXBase1Encoding ReEncodeFont" <8r.enc <5fpm8a.pfb  
>5fpmo8r FrontPageMedium "TeXBase1Encoding ReEncodeFont 0.167 SlantFont" <8r.enc <5fpm8a.pfb  
>5fpr8r FrontPage "TeXBase1Encoding ReEncodeFont" <8r.enc <5fpr8a.pfb  
>5fpro8r FrontPage "TeXBase1Encoding ReEncodeFont 0.167 SlantFont" <8r.enc <5fpr8a.pfb  
>5sfr8r Stafford "TeXBase1Encoding ReEncodeFont" <8r.enc <5sfr8a.pfb  
>5sfro8r Stafford "TeXBase1Encoding ReEncodeFont 0.167 SlantFont" <8r.enc <5sfr8a.pfb  

Ist dies nicht der Fall oder stehen dort zwar die TU Schriftarten, aber mit wesentlich kürzeren Einträgen, so ist zu überprüfen ob das Verzeichniss **texmf\fonts\map\dvipdfm\tex-tudfonts** existiert. Es sollte nicht vorhanden bzw. leer sein.

####Updates

In einen beliebigen Ordner die Zip-Dateien mit den Schriftarten (**tudfonts-tex_current.zip**) und dem TUD-Design (**latex-tuddesign_current.zip**) und evt. fachbereichs-spezifische Vorgaben für Abschlussarbeiten (**latex-tuddesign-thesis_current.zip**) herunter laden und entpacken.

0. Eine Konsole mit Administrator-Rechten öffnen (z. B. mit der Eingabe von runas /user:Administrator cmd unter Ausführen im Startmenü) 
0. In das Verzeichnis wechseln, in dem das eben entpackte texmf-Verzeichnis liegt (mit `cd <DIR>`).
0. Den Ordner _texmf\fonts\map\dvipdfm_ inklusive seines Inhalts löschen.  
`rmdir /Q /S "texmf\fonts\map\dvipdfm"`
0. Kopieren der Unterverzeichnisse von texmf in den Ordner **%PROGRAMFILES%\tuddesign\.**  
`xcopy texmf "%PROGRAMFILES%\tuddesign" /E /I`
0. In der Konsole den Befehl  
`initexmf --admin --update-fndb`
ausführen.

###TeXlive2008

####Allgemeine Hinweise

Die vorliegende Anleitung wurde mit TeXlive 2008 unter Windows XP sowie Vista getestet. Über andere Kombinationen kann ich keine Aussage treffen.

Für Hinweise, Korrekturen, Ergänzungen usw. stehe ich gerne zur Verfügung.

####Installation

In einen beliebigen Ordner die Zip-Dateien mit den Schriftarten (**tudfonts-tex_current.zip**) und dem TUD-Design (**latex-tuddesign_current.zip**) herunter laden und entpacken.
Kopieren der Unterverzeichnisse von texmf in den lokalen Texlive-Ordner.
(i. d. R. **C:\Programme\texlive-2008\texmf-local**)
Das Verzeichnis updmap.d wird nicht benötigt.

0. Eine Konsole öffnen (z. B. mit der Eingabe von cmd unter Ausführen im Startmenü)
0. Auf der Konsole den Befehl `texhash` ausführen
0. Dannach die Befehle  
`updmap-sys --enable Map=5ch.map`  
`updmap-sys --enable Map=5fp.map`  
`updmap-sys --enable Map=5sf.map`
0. Ein `updmap-sys --listmaps` sollte (am Ende der riesigen Liste) unter anderem die Zeilen

  >Map 5ch.map  
  >Map 5fp.map  
  >Map 5sf.map  

  zurückliefern.

Danach sollte alles funktionieren. Denke ich. Ich verwende zur Zeit TeXlive unter Eclipse Galileo mit dem TeXclipse Plugin.

