Fuß und Radentscheid Dresden - Webseite


# Using this repo

we are using [Jekyll](https://jekyllrb.com), a static website generator to build this page.
It's very easy to use and we don't need a giant bunch of dependencies while using wordpress, typo3 or other dynamic site generators.

All pages relying on simple [markdown files](https://daringfireball.net/projects/markdown/basics)

Used Theme: [Minimal-Mistakes](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/)

# Installation

## Windows

More info:  https://jekyllrb.com/docs/installation/windows

1) Download latest [Ruby+DevKit](https://rubyinstaller.org/downloads) and run it.
1) If the *RubyInstaller2* does not open, do it manually by issuing the command `ridk install`
1) Enter `1,2,3` to install *MSYS2 base, MINGW development toolchain* and *update MSYS2*.
1) Close your terminal windows and reopen it.
1) VSCodium/VSCode (oder andere IDE) neu starten.
1) Issue the command gem `install jekyll bundler`.
1) After the install finished, try jekyll -v
1) now clone this repo in a folder of choice. For example via `git clone https://github.com/RobTranquillo/fuss-und-radentscheid-dresden.git`
1) enter the new folder and run `bundle install`
1) starting your live webserver with `bundle exec jekyll serve`
1) open the page with http://127.0.0.1:4000/

## Linux

Die Schritte sind im Grunde die gleichen, wie bei Windows, ausgenommen die Installatin von Ruby.
In Linux ruby 3.0.0 comes up with an error in pathutil therefore **ruby 2.7 is recomended(!)** for jekyll.

### Fedora
```
sudo dnf module install ruby:2.7/default
ruby --version
```

### Ubuntu
```
sudo apt update
sudo apt install ruby-full
ruby --version
```



# Contribution

1) To contribute to this project you need to understand what git is: https://www.youtube.com/watch?v=MgnRFZJ7M2s
1) you need a git client: https://git-scm.com/book/de/v2/Erste-Schritte-Git-installieren or https://desktop.github.com/
1) if you had cloned the repository (see here under installation) you can make an change in the files and commit it to the repo
1) For easy internationalisation should all UI texts only resides in: _data\ui-text.yml

My recommendation for use is https://code.visualstudio.com/ with the following extensions:
- https://github.com/gitkraken/vscode-gitlens
- https://github.com/enyancc/vscode-ext-color-highlight
- https://github.com/panoply/vscode-liquid
- https://github.com/TheRealSyler/vscode-sass-indented
- https://github.com/TheRealSyler/vscode-sass-indented
All are not mandatory but make it much more pleasant to work.

# Anpassung
## Inhalt

Wie bei Lego werden bei Jekyll + minimal-mistakes Seiten meistens auf vielen vorhandenen Bausteinen einfach zusammen gesetzt.
MMistakes bietet dafür schon die gängisten Seitenlayouts inclusive der wichtigsten Funktionen leist zu nutzen an:
https://mmistakes.github.io/minimal-mistakes/docs/layouts/

## Design

Alle CSS Änderungen fangen in der Datei `_sass\minimal-mistakes.scss` an. In dieser werden alle Dateien des Unterordners `_sass\minimal-mistakes` eingebunden. In diesen können alle Änderungen vor genommen werden. Weitere Dateien können erzeugt und in der `minimal-mistakes.scss` eingefügt werden.

Wir verwenden einen eigenen Color-Skin diese befindet sich hier `_sass\minimal-mistakes\skins\_fussradentscheid.scss`.

Alle Bilder befinden sich im Ordner `assets/images` sowie alle Javascript Dateien in `assets/js`

Mehr Informationen finden sich hier:
- https://mmistakes.github.io/minimal-mistakes/docs/stylesheets/
- https://mmistakes.github.io/minimal-mistakes/docs/javascript/

## Navigation

Die Einträge des Hauptmenus im Kopf der Seite werden durch die Datei `_data/navigation.yml` gesteuert.
Konkret durch den Aufbau von *mainmenu*.

In der Datei `_includes\masthead.html` wird dieses ausgelesen und in ein Menü zusammengebaut.

## Erstellen einer neuen Seite bestehend aus einzelnen Karten (Cards)

In unserem System können wir ein Seite aus beliebig vielen Einzeldateien, den Cards, zusammensetzen.
Um eine neue Seite mit Karten zu erstellen gehe wie folgt vor.

1) erzeuge die gewünschte neue Seite im Ordner `pages`
1) damit die Seite für NutzerInnen erreichbar ist, sollte sie auch in der `_data/navigation.yml`verlinkt sein
1) Im Front Matter der neuen Seite wird auf die gewünschten Karten verwiesen: `cards: Bezeichner`
1) Achte auch darauf hier ein Seiten Layout zu verwenden, welches Cards anzeigt. ZB `layout: splash`
1) Im ordner `_cards` wird ein neuer Ordner angelegt passend zum Bezeichner
1) Darin liegen nun alle gewünschten Karten
1) Damit Jekyll den neuen Ordner verwendet muss es neugestartet werden `bundle exec jekyll serve`
1) Im Front Matter jeder Card wird auf die zugehörige page verwiesen mittels: `page: Bezeichner`

## Einen neuen Kartentyp erstellen

Alle verfügbaren Kartentypen sind im Verzeichnis `_layout/cards`.
Hier muss nur eine neue Karte erzeugt werden mit dem entsprechenden Titel und mit dem gewünnschten HTML gefüllt werden.
Am einfachsten ist evtl. einfach eine vorhandene Karte zu kopieren und zu verändern.

Um auf die Daten aus dem Front Matter und dem Inhalt der Markdowndatei zu zugreifen, die auf die neue Karte verweist,
sind wieder alle Liquid Variablen möglich. Also zB. `{{ page.title }}` oder `{{ content }}`
