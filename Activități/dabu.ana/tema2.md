# Utilizări ale editorului `sed`

## 1. Afișarea unei linii specifice dintr-un fișier

Pentru a afișa o singură linie dintr-un fișier text, fără a afișa restul conținutului, putem folosi comanda:

```bash
sed -n '4p' fisier.txt
``` 
Aici,
+ sed este editorul de fluxuri;
+ -n dezactivează afișarea implicită;
+ 4p indică afișarea liniei a patra;
+ fisier.txt este fișierul de intrare.

## 2. Înlocuirea unui cuvânt cu altul într-un text

Pentru a înlocui toate aparițiile unui cuvânt cu altul într-un text, folosim:

```bash
echo "Ana are mere" | sed 's/mere/pere/g'
```
+ echo furnizează textul de intrare;
+ | transmite rezultatul către sed;
+ s/mere/pere/g realizează substituția globală.

## 3. Ștergerea liniilor goale dintr-un fișier

Pentru a elimina toate liniile goale dintr-un fișier text se folosește:

```bash
sed '/^$/d' fisier.txt
```
+ ^$ reprezintă o linie goală;
+ d șterge liniile corespunzătoare;
+ fisier.txt este fișierul procesat.

## 4. Numerotarea liniilor unui fișier

Pentru a afișa un fișier text cu numerotarea liniilor, folosim:

```bash
sed = fisier.txt | sed 'N;s/\n/ /'
```
+ = afișează numărul liniei;
+ N combină numărul cu linia;
+ substituția elimină linia nouă dintre ele.

## 5. Extragerea numerelor dintr-o linie de text

Pentru a extrage doar numerele dintr-o linie care conține și alte caractere, folosim:

```bash
echo "ID produs: 12345" | sed 's/[^0-9]*\([0-9]\+\).*/\1/'
```
+ expresia regulată selectează secvența numerică;
+ \1 afișează grupul capturat.





