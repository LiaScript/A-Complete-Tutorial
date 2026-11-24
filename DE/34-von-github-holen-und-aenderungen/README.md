<!--
language: de
narrator: Deutsch Female
author: Jarvis
comment: Omas versunkener Apfelkuchen – ein Kurs zum Mitbauen.
mode: Presentation
import: https://raw.githubusercontent.com/LiaTemplates/Pyodide/0.5.0/README.md
import: https://raw.githubusercontent.com/LiaTemplates/Lia-ChemLab/0.4.0/README.md
@ofen: 175 °C Umluft
@richtig: Lecker – genau! 🍎
@fast: Fast! Schau noch einmal ins Rezept.
@tipp: <div style="background:#fff4e0;border-left:6px solid #e8a100;padding:8px 12px;border-radius:6px">👵 **Omas Tipp:** @0</div>
@mal: <script format="number" localestyle="unit" unit="gram" unitdisplay="long">@0 * @1</script>
-->

# Omas Apfelkuchen

--{{0}}--
Willkommen! Heute backen wir Omas Apfelkuchen. Viel Spaß beim Nachbacken!

Ein versunkener Apfelkuchen aus Rührteig. Nach einem Rezept von **[lecker.de](https://www.lecker.de/versunkener-apfelkuchen-nach-omas-rezept-30093.html)**.

![Ein runder Apfelkuchen in der Backform, oben mit Apfelspalten belegt](bilder/Apple_cake.jpg "_Abbildung:_ Omas Apfelkuchen – Foto: [Quasipodo](https://commons.wikimedia.org/wiki/File:Apple_cake.JPG), Lizenz [CC BY-SA 3.0](https://creativecommons.org/licenses/by-sa/3.0)")

?[Apfelkuchen – zum Anhören](https://upload.wikimedia.org/wikipedia/commons/6/63/De-Apfelkuchen.ogg "So spricht man es aus – Sprecher: joni, CC BY-SA 3.0")

## Zutaten

- 175 g Butter
- 175 g Zucker
- 4 Eier
- 300 g Mehl
- 3 TL Backpulver
- 750 g Äpfel
  - am besten säuerliche, zum Beispiel Boskop

### Mengen auf einen Blick

| Zutat | Gramm |
|---|---:|
| Butter | 175 |
| Zucker | 175 |
| Mehl | 300 |
| Äpfel | 750 |

    {{|>}}
Ein Kuchen hat 12 Stücke. In jedem Stück steckt $\frac{1}{12}$<!-- aria-label="ein Zwölftel" --> der Äpfel.

    {{|>}}
$$
\frac{750\,\text{g}}{12} \approx 62\,\text{g}
$$<!-- aria-label="750 Gramm geteilt durch 12, das sind etwa 62 Gramm" -->

Im Café: ein Stück 3 \$, der ganze Kuchen 30 \$.

### Für mehrere Kuchen

Für zwei Kuchen brauchst du @mal(175,2) Butter.

Für einen halben Kuchen: @mal(175,0.5) Butter.

Für drei Kuchen: <script>let kuchen = 3
175 * kuchen</script> g Butter.

Wie viele Kuchen? <script input="range" min="1" max="5" value="2" output="kuchen" input-always-active aria-label="Wie viele Kuchen?">@input</script>

Butter: <script format="number" localestyle="unit" unit="gram" unitdisplay="long">175 * @input(`kuchen`)</script>

Äpfel: <script format="number" localestyle="unit" unit="kilogram" unitdisplay="long">750 * @input(`kuchen`) / 1000</script>

Ändere die Zahl hinter `kuchen` und klick auf Ausführen.

``` js
let kuchen = 2
console.log("Butter:", 175 * kuchen, "g")
console.log("Zucker:", 175 * kuchen, "g")
console.log("Mehl:", 300 * kuchen, "g")
750 * kuchen + " g Äpfel"
```
<script>@input</script>

Und in Python – für so viele Kuchen, wie du willst.

``` python
anzahl = int(input("Wie viele Kuchen willst du backen? "))
for kuchen in range(1, anzahl + 1):
    print(kuchen, "Kuchen:", 750 * kuchen, "g Äpfel")
```
@Pyodide.eval

Und als Diagramm.

``` python
import matplotlib.pyplot as plt

zutaten = ["Butter", "Zucker", "Mehl", "Äpfel"]
gramm = [175, 175, 300, 750]

plt.bar(zutaten, gramm)
plt.title("Woraus besteht der Kuchen?")
plt.ylabel("Gramm")
plt.show()
```
@Pyodide.eval

## So geht's

    --{{0}}--
So backst du Omas Apfelkuchen – Schritt für Schritt.

    --{{1 Deutsch Male}}--
Zuerst rührst du den Teig. Und denk an den Ofen!

    {{1-3}}
Tipp: Den Ofen schon jetzt auf @ofen vorheizen.

    {{1}}
1. Butter und Zucker schaumig rühren, die Eier nach und nach unterrühren.

    --{{2}}--
Dann kommen Mehl und Backpulver dazu.

    {{2}}
2. Mehl und Backpulver mischen, unterrühren und den Teig in die Form streichen.

    --{{3}}--
Zum Schluss die Äpfel – und ab in den Ofen.

    {{3}}
3. Die Äpfel vierteln, darauflegen und bei @ofen etwa 45 Minuten backen.

## Omas Tipps

Kleine ~Geheimnisse~ Tipps, damit der Kuchen gelingt.

1\. Advent: Dann backt Oma diesen Kuchen jedes Jahr.

@tipp(Lauwarm mit einem Klecks Sahne servieren.)

### Der Teig

@tipp(Butter und Eier rechtzeitig aus dem Kühlschrank nehmen.)

    {{|>}}
@tipp(`Alle Zutaten sollten **Zimmertemperatur** haben, sonst gerinnt der Teig.`)

### Warum geht der Kuchen auf?

Backpulver enthält Natron. In der Hitze entsteht daraus Kohlenstoffdioxid – das Gas macht den Teig locker. Links zum Vergleich: kochendes Wasser.

```json @ChemLab.sim
{"scene":"kitchen","bench":[
  {"type":"beaker","id":"beaker1","ml":100,"contains":[{"reagent":"H2O","ml":50}]},
  {"type":"testtube","id":"testtube1","contains":[{"reagent":"NaHCO3 powder","g":2}]},
  {"type":"thermometer","id":"thermometer1","in":"beaker1"},
  {"type":"burner","id":"burner1","under":"beaker1","flame":2},
  {"type":"thermometer","id":"thermometer2","in":"testtube1"},
  {"type":"burner","id":"burner2","under":"testtube1","flame":2}
 ]}
```

### Die Äpfel

@tipp(Säuerliche Sorten wie _Boskop_ passen gut.)

Ihre Säure sorgt dafür, dass der Kuchen **~~nicht~~** pappig süß wird.

<!-- data-show-partial-solution -->
![Ein Apfel](https://commons.wikimedia.org/wiki/Special:FilePath/Belle_de_Boskoop_apple.jpg?width=500 "Sorte: [[ Granny Smith | (Boskop) | Elstar ]]")
![Zwei Äpfel im Korb](https://commons.wikimedia.org/wiki/Special:FilePath/Apfel_032_Elstar_%28fcm%29.jpg?width=500 "Sorte: [[ Granny Smith | Boskop | (Elstar) ]]")
![Ein Apfel](https://commons.wikimedia.org/wiki/Special:FilePath/One_Green_Apple.jpg?width=500 "Sorte: [[ (Granny Smith) | Boskop | Elstar ]]")
[[?]] Granny Smith ist kräftig grün.
[[?]] Elstar ist überwiegend rot, mit etwas Gelb.
[[?]] Boskop ist grünlich mit einem rötlichen Hauch.

_Fotos:_ [Sandstein](https://commons.wikimedia.org/wiki/File:Belle_de_Boskoop_apple.jpg), [CC BY 3.0](https://creativecommons.org/licenses/by/3.0) · [Frank C. Müller](https://commons.wikimedia.org/wiki/File:Apfel_032_Elstar_%28fcm%29.jpg), [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0) · [Donguk Kang](https://commons.wikimedia.org/wiki/File:One_Green_Apple.jpg), [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0)

### Apfel in anderen Sprachen

| Sprache | Apfel |
|---|---|
| Englisch | {|> UK English Female}{apple}<!-- class="notranslate" translate="no" --> |
| Französisch | {|> French Female}{pomme}<!-- class="notranslate" translate="no" --> |
| Russisch | {|> Russian Female}{яблоко}<!-- class="notranslate" translate="no" --> |

### Zum Anschauen

!?[Apfelernte in Südtirol](https://commons.wikimedia.org/wiki/Special:FilePath/Apple_harvest_in_South_Tyrol_2015_video.webm "Apfelernte in Südtirol – Marsupium, CC0")

!?[Buchstabensuppe – ein Rezept als LiaScript-Kurs](https://www.youtube.com/watch?v=EfCugmwbGe8)

### Zum Ausprobieren

??[Ein Apfelkuchen in 3D](https://sketchfab.com/3d-models/apple-cake-1-scaniverse-e102487e36644ef2af467fac40ba2033 "3D-Scan: JFN, CC BY 4.0")

??[Brüche: Einführung](https://phet.colorado.edu/sims/html/fractions-intro/latest/fractions-intro_all.html?locale=de "PhET Interactive Simulations, University of Colorado Boulder, CC BY-NC 4.0")

## Teste dein Wissen

Wie viele Eier kommen in den Teig?

<!-- data-text-solved="@richtig" data-text-failed="@fast" -->
[[4]]

Was gehört in Omas Apfelkuchen?

- [[ ]] Birnen
- [[X]] Äpfel
- [[ ]] Kirschen
- [[X]] Butter
- [[X]] Eier

Wie viele Minuten backt der Kuchen?

<!-- data-text-solved="@richtig" data-text-failed="@fast" -->
[[45]]

### Noch mehr Fragen

Welche Äpfel passen am besten in Omas Kuchen?

<!-- data-text-solved="@richtig" data-text-failed="@fast" -->
- [( )] süße
- [(X)] säuerliche
- [( )] möglichst weiche
[[?]] Schau auf der Seite „Die Äpfel“ nach.
***
Säuerliche Äpfel wie _Boskop_: Ihre Säure sorgt dafür, dass der Kuchen nicht pappig süß wird.
***

Bei wie viel Grad backt der Kuchen?

[[ 150 °C | ( 175 °C ) | 200 °C ]]

Butter und Zucker werden [[schaumig]] gerührt, die Äpfel werden [[ halbiert | (geviertelt) | gerieben ]].

Welches Gas entsteht aus dem Natron im Backpulver?

[( )] Sauerstoff
[(X)] Kohlenstoffdioxid
[( )] Stickstoff


## Deine Meinung

Hast du Omas Apfelkuchen schon gebacken?

- [(ja)] Ja, schon gebacken
- [(bald)] Mache ich bald
- [(nein)] Eher nicht

Welche Äpfel nimmst du am liebsten?

[[___]]

Wie viele Stücke schaffst du?

[(1)] ein Stück
[(2)] zwei Stücke
[(3)] drei oder mehr
