# Tema 2 – **Cinci** utilizări în linie de comandă ale editorului `sed`

## Studiu

`sed` (stream editor) este un editor de fluxuri utilizat în sistemele de operare **Linux** și **Unix**
pentru procesarea textului primit prin intrarea standard. Acesta funcționează linie cu linie
și permite **selectarea**, **ștergerea**, **modificarea** și **filtrarea** textului cu ajutorul expresiilor
regulate. Datorită integrării sale cu mecanismul de conducte (**pipes**), `sed` este frecvent
folosit în linia de comandă pentru prelucrarea rapidă a fluxurilor de date.

---

## Utilizarea 1 – Afișarea unei linii specifice din fluxul de date

**Problemă:** - Afișarea exclusivă a primei linii dintr-un text generat în linia de comandă.

**Comandă:**
```bash
printf "unu\ndoi\ntrei\n" | sed -n '1p'
```

**Explicație:**
- `printf` generează un flux de text format din mai multe linii.
- Operatorul `|` transmite fluxul către comanda `sed`.
- Opțiunea `-n` dezactivează afișarea implicită a tuturor liniilor.
- Comanda `1p` afișează doar prima linie din flux.

---

## Utilizarea 2 – Eliminarea unei linii din text

**Problemă:** - Eliminarea liniei a doua dintr-un flux de date text.

**Comandă:**
```bash
printf "unu\ndoi\ntrei\n" | sed '2d'
```

**Explicație:**
- `printf` generează textul cu trei linii.
- `|` transmite fluxul către comanda `sed`.
-  `2` indică a doua linie din flux.
- `d` este comanda de ștergere (delete).

---

## Utilizarea 3 – Înlocuirea unui cuvânt folosind `sed`

**Problemă:** - Înlocuirea primei apariții a cuvântului „linux” cu „gnu/linux” într-o linie de text.

**Comandă:**
```bash
echo "linux este un sistem linux" | sed 's/linux/gnu\/linux/'
```

**Explicație:**
- `echo` generează un flux de text.
- `|` transmite fluxul către comanda `sed`.
- `s` reprezintă comanda de substituție.
- `linux` este șirul căutat.
- `gnu\/linux` este șirul de înlocuire, caracterul `/` fiind escap-at, adică tratat ca un delimitator normal și nu ca delimitator al comenzii `sed`.

---

## Utilizarea 4 – Înlocuire globală folosind expresii regulate

**Problemă:** - Înlocuirea tuturor aparițiilor unui cuvânt dintr-o linie de text.

**Comandă:**
```bash
echo "ana are ana si ana" | sed 's/ana/maria/g'
```

**Explicație:**
-`echo` genereaza textul cu mai multe apariții ale cuvântului `ana`.
- `|` transmite fluxul către comanda `sed`.
- Opțiunea `g` (global) determină înlocuirea tuturor aparițiilor. Fără `g`, ar fi înlocuită doar prima apariție.

---

## Utilizarea 5 – Filtrarea liniilor pe baza unei expresii regulate

**Problemă:** - Afișarea exclusivă a liniilor care conțin cuvântul „error”.

**Comandă:**
```bash
printf "ok\nerror\nfatal error\nsuccess\n" | sed -n '/error/p'
```

**Explicație:**
-`printf` generează mai multe linii de text.
- `|` transmite fluxul către comanda `sed`.
- `/error/` este o expresie regulată care identifică liniile relevante.
- `p` afișează liniile care corespund expresiei.
- `-n` previne afișarea celorlalte linii.
