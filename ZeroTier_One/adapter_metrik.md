
# ZeroTier One

## Problem

Game Server Discovery funktioniert nicht obwohl gegenseitiges anpingen geht.

## Lösung

1. Systemsteuerung
1. Netzwerk und Internet
1. Netzwerk- und Freigabecenter
1. Adaptereinstellungen ändern (links im Menü)
1. ZeroTier One Adapter 
    1. rechtsklick &#9658; Eigenschaften
    1. `Internetprotokoll Version 4 (TCP/IPv4)` auswählen
    1. Eigenschaften
    1. Erweitert..
    1. Automatische Metrik &#9658; Haken rausnehmen
    1. Schnittstellenmetrik &#9658; `1`
    1. OK

## Netzwerk wechseln

1. altes Netzwerk deaktivieren (sonst keine auto server discovery)
   1. rechtsklick auf ZeroTier One im Tray
   2. Show Networks..
   3. Haken bei *Connected* rausnehmen
2. neues Netzwerk verbinden
   1. rechtsklick auf ZeroTier One im Tray
   2. Join Network..
   3. folge den Schritten von **Lösung** zum Einstellen der Schnittstellenmetrik
