# Einführung in HTML

Vielleicht fragst Du Dich, was ein Template (Vorlage) ist?

Ein Template (zu deutsch "Vorlage") ist eine Textdatei und ermöglicht es uns, verschiedene Inhalte in einer einheitlichen Darstellung zu erzeugen. Eine Vorlage für z.B. einen Brief hilft uns, immer gleich aussehende Nachrichten zu versenden, in denen sich Empfänger, Betreff und Text jeweils ändern, das äußere Format jedoch bestehen bleibt.

Ein Django-Template wird mit einer Sprache namens HTML beschrieben. (Genau das HTML aus dem ersten Kapitel: **Wie das Internet funktioniert**).

## Was ist HTML?

HTML ist recht einfacher Code, der von deinem Browser - z.B. Chrome, Firefox oder Safari - interpretiert wird, um dem Benutzer eine Website darzustellen.

HTML bedeutet "HyperText Markup Language". **HyperText** heißt, dass es sich um einen Text handelt, der Hyperlinks zwischen den Seiten unterstützt. **Markup** heißt so viel wie "Auszeichnung" und meint, dass wir mit HTML-Code Teilen der Webseite eine Bedeutung geben (den Text damit auszeichnen), die Browser verstehen. HTML-Code besteht aus **Tags**, wovon jeder mit `<` beginnt und mit `>` endet. Diese Tags stellen die Markup-**Elemente** dar.

## Dein erstes Template!

Ein Template zu erstellen, heißt, eine entsprechende Datei dafür zu erstellen. Alles ist eine Datei, wie Du vielleicht schon bemerkt hast.

Templates werden im Verzeichnis `blog/templates/blog` gespeichert. Als erstes erzeugen wir das Verzeichnis `templates` in deinem Blog-Verzeichnis. Im Template-Verzeichnis selbst erstellen wir ein weiteres Verzeichnis `blog`:

    blog
    └───templates
        └───blog
    

(Falls Du Dich wunderst, warum wir zwei `blog`-Verzeichnisse brauchen - das hängt mit den nützlichen Namenskonventionen von Django zusammen, die das Leben einfacher machen, wenn Deine Projekte immer komplizierter und komplexer werden.)

Als nächstes erstellen wir eine Datei `post_list.html` (erst mal ohne Inhalt) innerhalb des Verzeichnisses `blog/templates/blog`.

Kontrolliere deine überarbeitete Webseite unter: http://127.0.0.1:8000

> Falls Du die Fehlermeldung `TemplateDoesNotExists` angezeigt bekommst, versuche den Server neu zu starten. Öffne die Konsole, stoppe den Server mit Strg+C (Steuerung and C Tasten zusammen drücken) und starte ihn neu mit dem `python manage.py runserver` Kommando.

![Abbildung 11.1][1]

 [1]: images/step1.png

Der Fehler sollte weg sein! Toll :) Deine Webseite ist allerdings noch leer, weil dein Template leer ist. Das müssen wir ändern.

Füge folgenden Text in deine Template-Datei ein:

    html
    <html>
        <p>Hi there!</p>
        <p>It works!</p>
    </html>
    

Hat sich die Seite geändert? Sieh nach: http://127.0.0.1:8000/

![Abbildung 11.2][2]

 [2]: images/step3.png

Es funktioniert! Gute Arbeit! :)

*   Jede Webseite sollte mit dem Tag `<html>` beginnen, `</html>` steht immer am Ende. Zwischen den beiden Tags `<html>` und `</html>` steht der gesamte Inhalt der Webseite
*   `<p>` ist der Tag für ein Absatz-Element (paragraph), `</p>` beendet einen Absatz

## Head & body

Jede HTML Seite gliedert sich in zwei Teile: **head** und **body**.

*   Das Element **head** speichert im "Kopf" der Seite Informationen über die Seite, die dir nicht angezeigt werden.

*   Das Element **body** enthält den "Körper" - also den dargestellten Inhalt der Seite.

Im `<head>` informieren wir den Browser über Einstellungen und Konfigurationen der Webseite, z.B. wie sie dargestellt werden soll, und im `<body>` was tatsächlich dargestellt werden soll.

In den `<head>` können wir z.B. noch den Titel (title) der Seite mit aufnehmen:

    html
    <html>
        <head>
            <title>Ola's blog</title>
        </head>
        <body>
            <p>Hi there!</p>
            <p>It works!</p>
        </body>
    </html>
    

Speichere die Datei und aktualisiere die Seite im Browser.

![Abbildung 11.3][3]

 [3]: images/step4.png

Der Titel "Ola's blog" wird nun im Browser angezeigt. Hast du es bemerkt? Der Browser hat `<title>Ola's blog</title>` interpretiert und in die Titelleiste übernommen (dieser Titel wird auch in den Lesezeichen usw. verwendet).

Wie Du vielleicht bemerkt hast, hat jedes Element zu Beginn einen öffnenden Tag und einen zugehörigen *schließenden Tag* mit `/` und die Elemente sind darin *eingebettet*. Ein Tag in einem zweiten kann nicht außerhalb von diesem geschlossen werden, die Reihenfolge muss immer stimmen. 

Es ist wie Sachen in Kisten stecken. In die größte Box: `<html></html>` kommt eine kleinere Box: `<body></body>`, und dort wiederum packen wir viele kleine Kisten hinein: </code>`<p></p></0>.</p>

<p>Die Regeln und Reihenfolgen von <em>schließenden</em> Tags und <em>Verschachtelung</em> der Elemente musst Du immer einhalten. Anderenfalls können Browser die Seite nicht richtig interpretieren und darstellen.</p>

<h2>Dein Template anpassen</h2>

<p>Jetzt kannst du ein bisschen rumprobieren und dein Template umgestalten! Hier sind ein paar nützliche Tags dafür:</p>

<ul>
<li><code><h1>Überschrift</h1>` - (headline) für wichtigste Überschriften</li> 
*   `<h2>Unter-Überschrift</h2>` die nächsttiefere Überschiftenebene
*   `<h3>Unter-unter Überschrift</h3>` ... und so weiter bis `<h6>`
*   `<em>Text</em>` hebt deinen Text hervor
*   `<strong>Text</strong>` macht deinen Text fett
*   `<br />` fängt eine neue Zeile an (du kannst alles zwischen br schreiben)
*   `<a href="http://djangogirls.org">link</a>` erstellt einen Link
*   `<ul><li>Erster Punkt</li><li>second item</li></ul>` generiert eine Liste so wie diese hier!
*   `<div></div>` definiert einen Abschnitt auf einer Seite</ul> 
Hier ein Beispiel eines vollständigen Templates:

    html
    <html>
        <head>
            <title>Django Girls blog</title>
        </head>
        <body>
            <div>
                <h1><a href="">Django Girls Blog</a></h1>
            </div>
    
            <div>
                <p>published: 14.06.2014, 12:14</p>
                <h2><a href="">My first post</a></h2>
                <p>Aenean eu leo quam. Pellentesque ornare sem lacinia quam venenatis vestibulum. Donec id elit non mi porta gravida at eget metus. Fusce dapibus, tellus ac cursus commodo, tortor mauris condimentum nibh, ut fermentum massa justo sit amet risus.</p>
            </div>
    
            <div>
                <p>published: 14.06.2014, 12:14</p>
                <h2><a href="">My second post</a></h2>
                <p>Aenean eu leo quam. Pellentesque ornare sem lacinia quam venenatis vestibulum. Donec id elit non mi porta gravida at eget metus. Fusce dapibus, tellus ac cursus commodo, tortor mauris condimentum nibh, ut f.</p>
            </div>
        </body>
    </html>
    

Wir haben hier drei verschiedene `div` Abschnitte erstellt.

*   Das erste `div` Element enthält den Titel unseres Blogs - eine Überschrift und einen Link
*   Zwei weitere `div` Elemene beinhalten unsere Blogposts und ein Publikationsdatum, `h2` mit dem Titel des Posts und zwei `p` (paragraph) Tags mit Text, eines für das Datum und eines für den Blogpost.

Wir bekommen das Folgende:

![Abbildung 11.4][4]

Yaaay! Bis jetzt zeigt unser Template aber immer genau die **gleichen Inhalte** - wobei wir aber vorhin davon gesprochen haben, dass Templates uns erlauben **verschiedene** Informationen im **gleichen Format** darzustellen.

Eigentlich wollen wir richtige Posts anzeigen, die in unserer Django Admin Oberfläche hinzugefügt wurden -und das wollen wir als nächstes tun.

## Noch eine Sache: anwenden!

Es wäre gut das alles live draußen im Internet zu sehen, oder? Lass uns noch eine PythonAnywhere-Anwendung machen:

### Committe, und pushe deinen Code auf Github

Lass uns nachsehen, welche Dateien sich nach dem letzten Veröffentlichen (deploy) geändert haben. (Führe diese Befehle lokal aus und nicht auf PythonAnywhere):

    $ git status
    

Überprüfe, ob du im `Djangogirls` Verzeichnis bist und sag `git`, dass alle Änderungen in diesem Verzeichnis hinzugefügt werden sollen:

    $ git add -A .
    

> **Beachte** `-A` (kurz für "all") bedeutet, dass `git` auch Dateien berücksichtigt, die du gelöscht hast (in der Standardeinstellung werden nur neue/geänderte Dateien hinzugefügt). Denk auch daran (Kapitel 3), dass `.` das aktuelle Verzeichnis meint.

Bevor wir alle Dateien hochladen prüfen wir, was `git` hochladen will (alle Dateien, die `git` hochladen wird, sind jetzt grün):

    $ git status
    

Fast fertig, wir sagen nun noch, dass diese Änderung im Verlauf gespeichert werden soll. Wir erstellen eine "Commit Message", in dem wir beschreiben was wir verändert haben. Du kannst an diesem Punkt hier alles rein schreiben, aber es ist nützlich etwas zu Sinnvolles einzutragen, damit du dich in Zukunft erinnern kannst was du geändert hast.

    $ git commit -m "HTML der Site geändert."
    

> **Beachte** Du musst Anführungszeichen um den Commit Kommentar machen.

Nachdem wir das gemacht haben, laden (push) wir unsere Änderungen auf GitHub:

    git push
    

### Zieh dir neuen Code runter auf PythonAnywhere und lade deinen Browser neu.

*   Öffne die [PythonAnywhere consoles page][5] und gehe zu deiner **Bash Konsole** (oder starte eine neue). Dann, führe folgendes aus:

    $ cd ~/my-first-blog 
    $ source myvenv/bin/activate 
    (myvenv)$ git pull 
    [...] 
    (myvenv)$ python manage.py collectstatic 
    [...]
    

Und schau zu, wie Dein Code runtergeladen wird. Wenn Du prüfen willst, ob der Code angekommen ist, kannst Du zum **Files tab** rüberspringen und Deinen Code auf PythonAnywhere sehen.

*   Anschließend spring rüber zum [Web tab][6] und klick auf **Neu laden** in Deinem Browser.

Dein Update sollte live sein! Lade die Seite neu in deinem Browser. Es sollten nun Änderungen zu sehen sein. :)

 [4]: images/step6.png
 [5]: https://www.pythonanywhere.com/consoles/
 [6]: https://www.pythonanywhere.com/web_app_setup/