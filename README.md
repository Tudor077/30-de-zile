# Provocarea 30 de zile

O aplicație pentru elevi de liceu care vor să afle unde le pleacă banii. Timp de
30 de zile notezi ce cheltui, primești în fiecare săptămână o provocare nouă,
iar clasa ta concurează cu celelalte clase. Nu câștigă clasa care cheltuie cel
mai puțin, ci cea care notează cel mai constant.

> Prototip pentru **Banometru**. Totul rulează în browser, fără cont și fără
> server: datele rămân doar pe telefonul tău.

## Cum funcționează

1. **Notezi ce cheltui, în 5 secunde.** Scrii suma, alegi categoria și, dacă
   vrei, adaugi o notă. Dacă într-o zi n-ai cheltuit nimic, apeși
   „Azi: 0 lei”.
2. **Primești o provocare nouă în fiecare săptămână.**
3. **Clasa ta urcă în clasament** pe măsură ce notezi în cât mai multe zile.

La început răspunzi la 3 întrebări scurte despre cum îți gestionezi banii.
Aceleași întrebări vin și la final, ca să vezi ce s-a schimbat.

## Provocările

| Săptămâna | Provocarea | Obiectiv |
|---|---|---|
| 1 | **Fotografia**: doar notezi tot, fără să schimbi nimic | Notează în 5 din 7 zile |
| 2 | **Ziua zero**: o zi în care nu cheltui niciun leu | O zi cu 0 lei |
| 3 | **Vânătoarea**: găsește un abonament, un joc sau un obicei pe care dai bani degeaba | Marchează o cheltuială ca „regretată” |
| 4 | **Țeapa**: cinci mesaje reale de pe telefon, care e țeapă și care nu? | Ia 4 din 5 la test |

## Ce găsești în aplicație

- **Azi**: seria ta pe 30 de zile (albastru = ai notat, verde = zi fără
  cheltuieli), totalul zilei și ultimele cheltuieli. Apeși pe o cheltuială
  ca s-o ștergi.
- **Rezumat**: unde îți pleacă banii, pe categorii, plus media pe zi, ritmul
  pe lună, cât dai pe lucruri regretate și cât ar însemna asta pe un an.
- **Provocări**: provocarea săptămânii curente și testul „Țeapă sau real?”.
- **Clase**: clasamentul claselor, după cât de constant notează fiecare.

Categoriile sunt: 🍔 Mâncare, 🎉 Ieșiri, 👕 Haine, 🎮 Jocuri și abonamente,
🚌 Transport și 📦 Altele.

## Instalare pe telefon

Aplicația e un PWA, adică o pagină web care se poate instala ca o aplicație și
care merge și fără internet după prima deschidere.

1. Deschide pagina aplicației în browser.
2. **Android (Chrome):** meniul ⋮ → *Adaugă pe ecranul de pornire*.
   **iPhone (Safari):** butonul de partajare → *Adaugă pe ecranul principal*.

## Rulare locală

Nu există nimic de compilat sau de instalat. Service worker-ul are nevoie de un
server, așa că pornești unul simplu în folderul proiectului:

```sh
python -m http.server 8000
```

apoi deschizi `http://localhost:8000`.

## Pentru prezentare

Clasamentul este simulat: celelalte clase sunt fictive și există ca aplicația
să poată fi prezentată fără mai mulți utilizatori reali.

| Gest | Ce face |
|---|---|
| 3 atingeri pe „Clasamentul claselor” | arată panoul de prezentare (date demo / ia-o de la capăt) |
| 2 atingeri pe numele clasei din antet | simulează o zi: avansează o zi, adaugă cheltuieli și urcă treptat în clasament |
| 3 atingeri pe „Ziua X din 30” | sare la ziua următoare |
| Ții apăsat pe un rând din clasament | îl muți în altă poziție |
| 2 atingeri pe un procent din clasament | îl modifici |

**Încarcă date demo** umple aplicația cu 18 zile de cheltuieli realiste.
**Ia-o de la capăt** șterge tot (trebuie apăsat de două ori).

## Fișiere

| Fișier | Ce conține |
|---|---|
| `index.html` | toată aplicația: interfața, stilurile și logica |
| `sw.js` | service worker-ul care o face să meargă offline |
| `manifest.webmanifest` | numele, culorile și iconițele pentru instalare |
| `icon-192.png`, `icon-512.png` | iconițele aplicației |

Datele se salvează în `localStorage`, sub cheia `p30_v1`.
