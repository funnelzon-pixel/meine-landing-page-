# Power Buy and Sell System (TradingView Indikator)

Ein eigenständig entwickelter TradingView-Indikator im Stil von **Valhalla Indicators**
(valhallaindicators.com), inspiriert von den öffentlich beschriebenen Kernfunktionen:
präzise Buy/Sell-Signale, automatische Entry/Stop-Loss/Take-Profit-Level, ein Live-Dashboard
mit Performance-Statistiken und Alert-Unterstützung.

## Wichtiger Hinweis zur Vorlage

Der originale Valhalla-Indikator ist ein **Invite-Only-Script auf TradingView** – der
Quellcode ist proprietär, nicht öffentlich einsehbar und wird nur zahlenden Mitgliedern
freigeschaltet. Eine echte "1:1"-Kopie des internen Algorithmus ist daher technisch nicht
möglich, da keine Quelle existiert, die man einsehen könnte. Was öffentlich dokumentiert ist
(Setup-Guides, FAQ, Marketing-Seiten), wurde ausgewertet und als Feature-Set nachgebaut:

- Exakte Entry-, Stop-Loss- und Take-Profit-Preise direkt im Chart
- Umschaltbarer Modus "Use Opposite Signal as Stop Loss" (Stop-and-Reverse, immer im Markt)
- Alternativ: fester ATR-Stop mit zwei Take-Profit-Zielen (TP1 verschiebt den Stop auf
  Break-even, TP2 schließt den Rest)
- Live-Dashboard mit Trendstatus, Power Score, Win-Rate, Anzahl Signale, Ø R-Multiple und
  Gewinn-Streaks
- Alarme für Buy, Sell, Take-Profit- und Stop-Loss-Treffer

Die eigentliche Signal-Logik ("Power Score") wurde neu entwickelt: eine Kombination aus
SuperTrend, EMA(200)-Trendfilter, RSI, MACD-Histogramm, Volumen-Expansion und
ATR-Volatilitätsexpansion. Ein Signal wird nur ausgelöst, wenn der Trend dreht **und**
der Confluence-Score (0–100) den eingestellten Schwellenwert erreicht.

## Installation in TradingView

1. TradingView öffnen → Pine Editor (unten im Chart-Fenster).
2. Neues, leeres Script anlegen und den Inhalt von `PowerBuySellSystem.pine` einfügen.
3. Auf "Speichern" klicken und einen Namen vergeben (z. B. "Power Buy and Sell System").
4. Auf "Zum Chart hinzufügen" klicken.
5. Über das Zahnrad-Icon des Indikators die Einstellungen (Trend Engine, Power Score,
   Risk Management, Display) an das gehandelte Symbol/Timeframe anpassen.

## Einstellungen im Überblick

| Gruppe | Parameter | Beschreibung |
|---|---|---|
| Trend Engine | SuperTrend ATR Period/Multiplier | Bestimmt die Basis-Trendrichtung |
| Trend Engine | Trend Filter EMA Length | Übergeordneter Trendfilter (Standard 200) |
| Power Score | RSI/MACD/Volumen-Parameter | Bausteine des 0–100 Confluence-Scores |
| Power Score | Minimum Power Score | Schwellenwert, ab dem ein Signal ausgelöst wird |
| Risk Management | Use Opposite Signal as SL | Stop-and-Reverse (immer im Markt) ein/aus |
| Risk Management | Stop Loss ATR Multiplier | Nur relevant, wenn obiger Schalter aus ist |
| Risk Management | Take Profit 1 / 2 (R-Multiple) | Zielgewinne in Vielfachen des Risikos |
| Display | Dashboard, Linien, Farben | Visuelle Anpassung |

## Alerts einrichten

Rechtsklick auf den Chart → "Alarm hinzufügen" → als Bedingung den Indikator
"Power Buy and Sell System" wählen und eine der vier Bedingungen (Buy Signal, Sell Signal,
Take Profit Hit, Stop Loss Hit) auswählen.

## Disclaimer

Dieses Skript dient ausschließlich zu Informations- und Bildungszwecken und stellt keine
Anlageberatung dar. Historische Signal-Performance im Dashboard ist eine vereinfachte,
theoretische Berechnung (R-Multiples) und keine Garantie für zukünftige Ergebnisse.
