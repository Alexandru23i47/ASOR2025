### Problema 1

Pentru a vedea ultimul rând dintr-un fișier, trebuie ținută minte comanda specifică `tail`:

```bash
tail -1 fisier.txt
```

Un rezultat echivalent, folosind o comandă **sed**:

```bash
sed -n '$p' fisier.txt
```

Aici,

- `sed` citește fișierul rând cu rând
- `-n` dezactivează afișarea imediată a rândurilor
- `$` se referă la ultimul rând
- `p` tipărește rândul selectat

### Problema 2

Calcularea numărului de rânduri dintr-un fișier-text:

```bash
wc -l fisier.txt
```

Un rezultat echivalent, folosind o comandă **sed**:

```bash
sed -n '$=' fisier.txt
```

Aici,

- `sed` numerotează intern rândurile
- `$` se referă la ultimul rând
- `=` afișează numărul rândului curent
  
### Problema 3

Afișarea rândurilor 10–20 dintr-un fișier-text fără a memora opțiuni ale comenzilor `less` sau `awk`:

```bash
sed -n '10,20p' fisier.txt
```

Aici,

- valorile `10` și `20` sunt capetele unui interval de adrese de rânduri
- `p` tipărește doar rândurile corespunzând acestui interval
- `-n` dezactivează tipărirea imediată a restului *output*-ului (datelor de ieșire)

### Problema 4

Afișarea doar a rândurilor care conțin un cuvânt dat (fără să apelăm la comanda `grep`):

```bash
sed -n '/error/p' fisier.log
```

Aici,

- `/error/` selectează rândurile care conțin expresia „error”
- `p` le afișează
- `-n` oprește afișarea imediată a celorlalte rânduri
  
### Problema 5

Afișarea primului rând dintr-un fișier-text:

```bash
head -1 fisier.txt
```

Un rezultat echivalent, folosind o comandă **sed**:

```bash
sed -n '1p' fisier.txt
```

Aici,

- `1` reprezintă primul rând
- `p` afișează rândul
- `-n` evită afișarea imediată a celorlalte rânduri
