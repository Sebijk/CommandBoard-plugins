-------------------------------------------
cbSEO Version 1.0.0 Beta 2pl1
Autor: Sebijk ( http://www.sebijk.de )
Getestet mit: Command Board 1.0 Beta 2.0
-------------------------------------------
Dieser Hack macht euer Commandboard suchmaschinenoptimiert.
Da ich es noch nicht ausgiebig getestet habe, ist er auf
den Betastatus versetzt worden.

Um diesen Hack zu benutzen, solltet ihr unbedingt mod_rewrite
installiert und aktiviert haben.

Dateien, die modifiziert werden müssen:
-----------------------------------------
thread.php
newthread.php
templates/standard/board_thread_zeile.tpl
templates/standard/_kategorie_zeile.tpl
templates/standard/_foren_zeile.tpl
templates/standard/newthread.tpl
templates/standard/newpost.tpl
templates/standard/thread.tpl

FAQ:
Frage: Was wird aus $sid?
Antwort: Sie ist vorübergehend gelöscht, aber ich werde
da nach eine kompatible Möglichkeit arbeiten. Wenn du
unbedingt $sid brauchst, dann kannst du die mit ?{$sid}
anhängen.

1. Lade die .htaccess auf deinen CB-Verzeichnis hoch.

2.1 Öffne thread.php

Suche nach:
------------------------------------------------------------
$url = "thread.php?threadid=$threadid&seite=".ceil($mengeteilen)."&$sid#ende";
------------------------------------------------------------

Ersetze das in:
------------------------------------------------------------
$url = "thema-$threadid-".ceil($mengeteilen).".html#ende";
------------------------------------------------------------

Weitersuchen nach:
------------------------------------------------------------
$seiten = blaetterfunktion($seite,$maxseite,"?threadid=$threadid&$sid");
------------------------------------------------------------

Ersetze das in:
------------------------------------------------------------
$seiten = blaetterfunktion($seite,$maxseite,"");
-------------------------------------------------------------


2.2 Öffne newthread.php

Suche nach:
------------------------------------------------------------
$tpl->vars("ziel","thread.php?threadid=$lastthreadid&$sid");
------------------------------------------------------------

Ersetze das in:
------------------------------------------------------------
$tpl->vars("ziel","thema-$lastthreadid.html");
------------------------------------------------------------

2.3 Öffne newpost.php

Suche nach:
------------------------------------------------------------
$tpl->vars("ziel","thread.php?postid=$lastpostid&$sid");
------------------------------------------------------------

Ersetze das in:
------------------------------------------------------------
$tpl->vars("ziel","themenbeitrag-$lastpostid.html");
------------------------------------------------------------

2.4 Öffne templates/standard/board_thread_zeile.tpl

Suche nach:
------------------------------------------------------------
<a href="thread.php?threadid={$thread_id}&extra=last&{$sid}">
------------------------------------------------------------

Ersetze das in:
------------------------------------------------------------
<a href="letzter-beitrag-{$thread_id}.html">
------------------------------------------------------------


2.5 Öffne templates/standard/_kategorie_zeile.tpl

Suche nach:
------------------------------------------------------------
<a id="kategorie" href="board.php?boardid={$kategorie_id}&{$sid}">
------------------------------------------------------------

Ersetze das in:
------------------------------------------------------------
<a id="kategorie" href="forum-{$kategorie_id}.html">
------------------------------------------------------------


2.6 Öffne templates/standard/_foren_zeile.tpl

Suche nach:
------------------------------------------------------------
<a href="board.php?boardid={$board_id}&{$sid}">
------------------------------------------------------------

Ersetze das in:
------------------------------------------------------------
<a href="forum-{$board_id}.html">
------------------------------------------------------------

Weitersuchen nach:
------------------------------------------------------------
<a title="{$lastthreadtitle}" href="thread.php?threadid={$lastthread_id}&extra=last&{$sid}">
------------------------------------------------------------

Ersetze das in:
------------------------------------------------------------
<a title="{$lastthreadtitle}" href="letzter-beitrag-{$lastthread_id}.html">
------------------------------------------------------------


2.7 Öffne templates/standard/newthread.tpl

Suche nach:
------------------------------------------------------------
<a href="board.php?boardid={$board_id}&{$sid}">
------------------------------------------------------------

Ersetze das in:
------------------------------------------------------------
<a href="forum-{$board_id}.html">
------------------------------------------------------------


2.8 Öffne templates/standard/newpost.tpl

Suche nach:
------------------------------------------------------------
<a href="board.php?boardid={$board_id}&{$sid}">
------------------------------------------------------------

Ersetze das in:
------------------------------------------------------------
<a href="forum-{$board_id}.html">
------------------------------------------------------------

Weitersuchen nach:
------------------------------------------------------------
<a href="thread.php?threadid={$thread_id}&{$sid}">
------------------------------------------------------------

Ersetze das in:
------------------------------------------------------------
<a href="thema-{$thread_id}.html">
------------------------------------------------------------


2.9 Öffne templates/standard/thread.tpl

Suche nach (2x):
------------------------------------------------------------
<a href="board.php?boardid={$board_id}&{$sid}">
------------------------------------------------------------

Ersetze das in (2x):
------------------------------------------------------------
<a href="forum-{$board_id}.html">
------------------------------------------------------------