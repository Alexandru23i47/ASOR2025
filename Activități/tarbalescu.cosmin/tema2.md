### Problema 1
Pentru a vedea ultima linie dintr-un fișier, trebuie ținut minte:
```bash
tail -1 fisier.txt
```
Comanda cu **sed**:
```bash
sed -n '$p' fisier.txt
```
Aici,
- `sed` citește fișierul linie cu linie
- `-n` dezactivează afișarea implicită 
- `$` selecteaza ultima linie
- `p` tipărește linia selectată

### Problema 2
Numărul de linii dintr-un fișier:
```bash
wc -l fisier.txt
```
Comanda cu **sed**:
```bash
sed -n '$=' fisier.txt
```
Aici,
- `sed` numerotează intern liniile
- `$` ajunge la ultima linie
- `=` afișează numărul liniei curente
### Problema 3
Afișarea liniilor 10–20 dintr-un fișier fără a memora `less` sau `awk`
Comanda cu **sed**:
```bash
sed -n '10,20p' fisier.txt
```
- `10` si `20` definește un interval de linii
- `p` tipărește doar acel interval
- `-n` dezactivează restul output-ului
### Problema 4
Afișarea doar liniilor care conțin un cuvânt( fără `grep`)
```bash
sed -n '/error/p' fisier.log
```
- `/error/` selectează liniile care conțin „error”
- `p` le afișează
- `-n` oprește afișarea celorlalte linii
### Problema 5
Prima linie dintr-un fișier
```bash
head -1 fisier.txt
```
Comanda cu **sed**:
```bash
sed -n '1p' fisier.txt
```
- `1` reprezintă prima linie
- `p` afișează linia
- `-n` evită afișarea celorlalte linii
