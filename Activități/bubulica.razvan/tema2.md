# 1. Înlocuirea tuturor aparițiilor unui cuvânt dintr-un fișier

## Enunțul utilizării

Se dorește înlocuirea tuturor aparițiilor unui cuvânt cu un alt cuvânt într-un fișier text (de exemplu, corectarea automată a unui termen greșit scris), fără a modifica direct fișierul original, ci afișând rezultatul la ieșirea standard.

## Comanda sed (formă completă)

```shell
bash
sed 's/vechi/nou/g' fisier.txt
```

## Descrierea detaliată a comenzii

* sed – pornește editorul de flux sed.
* 's/vechi/nou/g' – scriptul sed propriu-zis:

  * s este comanda de *substituție* (substitute).
  * vechi este expresia regulată care descrie textul căutat.
  * nou este textul cu care va fi înlocuit cel găsit.
  * g (global) indică faptul că înlocuirea se face pentru *toate aparițiile* de pe fiecare linie, nu doar pentru prima.
* fisier.txt – fișierul de intrare asupra căruia sed aplică transformarea.

Sed citește fișierul linie cu linie, aplică substituția pe fiecare linie și afișează rezultatul.

---

# 2. Ștergerea liniilor goale dintr-un fișier

## Enunțul utilizării

Se dorește eliminarea tuturor liniilor goale dintr-un fișier text, pentru a obține un fișier compact, fără spații inutile între linii.

## Comanda sed (formă completă)

```shell
bash
sed '/^$/d' fisier.txt
```

## Descrierea detaliată a comenzii

* sed – editorul de flux.
* '/^$/d' – script sed:

  * ^ marchează începutul liniei.
  * $ marchează sfârșitul liniei.
  * ^$ descrie o linie goala
  * d este comanda *delete*, care șterge liniile ce corespund adresei date.
* fisier.txt – fișierul procesat.

Pentru fiecare linie care este goală, sed o elimină și nu o mai trimite la ieșire.

---

# 3. Afișarea doar a liniilor care conțin un anumit text

## Enunțul utilizării

Se dorește afișarea exclusiv a liniilor care conțin un anumit cuvânt (de exemplu, filtrarea mesajelor de eroare dintr-un fișier jurnal).

## Comanda sed (formă completă)

```shell
bash
sed -n '/eroare/p' fisier.log
```

## Descrierea detaliată a comenzii

* sed – editorul sed.
* -n – opțiune care dezactivează afișarea implicită a tuturor liniilor.
* '/eroare/p' – script sed:

  * eroare este expresia regulată căutată.
  * p este comanda *print*, care afișează liniile ce corespund expresiei.
* fisier.log – fișierul de intrare.

Sed va afișa doar liniile care conțin textul „eroare”, ignorând restul.

---

# 4. Numerotarea liniilor unui fișier

## Enunțul utilizării

Se dorește afișarea conținutului unui fișier cu numerotarea fiecărei linii, utilă pentru analiză sau depanare.

## Comanda sed (formă completă)

```shell
bash
sed = fisier.txt | sed 'N;s/\n/ /'
```


## Descrierea detaliată a comenzii

* Prima comandă sed = fisier.txt:

  * = este o comandă sed care afișează *numărul liniei curente*.
* Operatorul | transmite ieșirea primei comenzi către următoarea.
* A doua comandă sed 'N;s/\n/ /':

  * N adaugă următoarea linie în spațiul de lucru (pattern space).
  * s/\n/ / înlocuiește caracterul de linie nouă cu un spațiu.

Rezultatul final este o afișare de forma: număr_linie conținut_linie.

---

# 5. Eliminarea comentariilor dintr-un fișier de configurare

## Enunțul utilizării

Se dorește eliminarea liniilor de comentariu (care încep cu #) dintr-un fișier de configurare, pentru a vedea doar setările efective.

## Comanda sed (formă completă)

```shell
bash
sed '/^#/d' configurare.conf
```

## Descrierea detaliată a comenzii

* sed – editorul sed.
* '/^#/d' – script sed:

  * ^# identifică liniile care încep cu caracterul #.
  * d șterge aceste linii.
* configurare.conf – fișierul analizat.

Sed parcurge fișierul linie cu linie și elimină toate comentariile, afișând doar liniile relevante.

---
