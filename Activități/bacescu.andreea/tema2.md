# Tema 2 – **Cinci** utilizări practice ale editorului `sed` în linia de comandă

## Studiu

Editorul `sed`, cunoscut și sub denumirea de *stream editor*, este un utilitar specific sistemelor
de operare **Linux** și **Unix**, folosit pentru prelucrarea textului în mod neinteractiv.
Acesta primește date prin intrarea standard sau din fișiere și le procesează secvențial,
linie cu linie. Prin intermediul comenzilor și al expresiilor regulate, `sed` permite
realizarea unor operații precum eliminarea anumitor linii, modificarea conținutului,
selectarea fragmentelor de text sau filtrarea informațiilor. Datorită eficienței sale și
a integrării cu comenzile din shell, `sed` este frecvent utilizat pentru automatizarea
prelucrării fluxurilor de date în linia de comandă.

---

## Utilizarea 1 – Eliminarea spațiilor de la sfârșitul liniilor

**Problemă:** - Ștergerea spațiilor inutile de la finalul fiecărei linii dintr-un flux de text.

**Comandă:**

```bash
printf "text1   \ntext2  \ntext3 \n" | sed -E 's/[ \t]{1,}$/%/'
```

**Explicație:**

- `printf` generează un flux de text cu spații la final de linie.
- Operatorul `|` transmite fluxul către comanda `sed`.
- `[ \t]{1,}` identifică orice număr nenul de spații sau taburi.
- `$` indică sfârșitul liniei.
- Comanda de substituție elimină aceste caractere *goale* și le
  înlocuiește cu caracterul de control `%`.

---

## Utilizarea 2 – Dublarea doar a liniilor pare

**Problemă:** - Afișarea de două ori a liniilor cu număr par dintr-un flux de date.

**Comandă:**

```bash
# daca sed-ul din Alpine Linux nu accepta formula `~`:
# testati comanda urmatoare in emulatorul [ https://sed.js.org/ ]
printf "a\nb\nc\nd\n" | sed '2~2p'
```

**Explicație:**

- `printf` generează mai multe linii de text.
- `2~2` selectează fiecare a doua linie, începând cu linia 2.
- `p` afișează suplimentar liniile selectate.
- Liniile pare apar de două ori în rezultat.

---

## Utilizarea 3 – Afișarea liniilor care NU conțin un cuvânt

**Problemă:** - Afișarea exclusivă a liniilor care nu conțin cuvântul „error”.

**Comandă:**

```bash
printf "ok\nerror\nfatal\n" | sed -n '/error/!p'
```

**Explicație:**

- `printf` generează un flux de text.
- `/error/` este expresia regulată căutată.
- `!` inversează selecția (este un `not`).
- `p` afișează doar liniile care se potrivesc.
- `-n` oprește afișarea implicită.

---

## Utilizarea 4 – Înlocuirea unui cuvânt doar la final de linie

**Problemă:** - Înlocuirea cuvântului „end” doar dacă apare la sfârșitul liniei.

**Comandă:**

```bash
printf "the end\nend game\nhappy end\n" | sed 's/end$/stop/'
```

**Explicație:**

- `printf` generează mai multe linii de text.
- `end$` caută cuvântul „end” doar la final de linie.
- `s` este comanda de substituție.
- Înlocuirea se face doar când condiția este îndeplinită.

---

## Utilizarea 5 – Inserarea unei linii după o potrivire

**Problemă:** - Inserarea unei linii informative după fiecare linie care conține „START”.

**Comandă:**

```bash
printf "START\nproces\nSTART\n" | sed '/START/a Linie adaugata'
```

**Explicație:**
- `printf` generează un flux de date.

- `/START/` identifică liniile dorite.
- `a` (append) adaugă o linie nouă după linia potrivită.
- Textul este inserat imediat după fiecare potrivire.
