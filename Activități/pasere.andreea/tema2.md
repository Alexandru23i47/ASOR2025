# Tema 2 – **Cinci** utilizări în linie de comandă ale editorului `sed`

## Studiu

`sed` (*stream editor*) este un editor de fluxuri utilizat în sistemele de operare **Linux** și **Unix**
pentru procesarea textului primit de la intrarea standard. Acesta prelucrează fluxul linie cu linie
și permite **selectarea**, **ștergerea**, **modificarea** și **filtrarea** acestuia cu ajutorul expresiilor
regulate. Datorită integrării sale cu mecanismul de canalizare (**pipes**), `sed` este frecvent
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
- `d` este comanda de ștergere (*delete*).

---

## Utilizarea 3 – Înlocuirea unui cuvânt folosind `sed`

**Problemă:** - Înlocuirea primei apariții a cuvântului „Linux” cu „GNU/Linux” într-o linie de text.

**Comandă:**
```bash
echo "Debian este un sistem de operare din familia Linux." | sed 's/Linux/GNU\/Linux/'
```

**Explicație:**

- `echo` generează un flux de text.
- `|` transmite fluxul către comanda `sed`.
- `s` reprezintă comanda de substituție.
- `Linux` este șirul căutat.
- `GNU\/Linux` este șirul de înlocuire, caracterul `/` fiind escapat (*escaped*, eludat), adică tratat ca un delimitator normal și nu ca delimitator al comenzii `sed`.

---

## Utilizarea 4 – Înlocuire globală folosind expresii regulate

**Problemă:** - Înlocuirea tuturor aparițiilor unui cuvânt dintr-o linie de text.

**Comandă:**

```bash
echo "Ana o are ca mamă pe Lana și ca bunică pe Nana." | sed 's/ana/ina/g'
```

**Explicație:**

- `echo` afișează șirul de caractere în care se găsesc mai multe instanțe ale subșirului de caractere `ana`.
- `|` transmite fluxul către comanda `sed`.
- Fanionul `g` (*global*) determină înlocuirea tuturor aparițiilor. Fără `g`, ar fi înlocuită doar prima apariție
  a lui `ana`.

---

## Utilizarea 5 – Filtrarea liniilor pe baza unei expresii regulate

**Problemă:** - Afișarea exclusivă a liniilor care conțin cuvântul „error”.

**Comandă:**

```bash
printf "ok\nerror\nfatal error\nsuccess\n" | sed -n '/error/p'
```

**Explicație:**

- `printf` generează mai multe linii de text.
- `|` transmite fluxul către comanda `sed`.
- `/error/` este o expresie regulată care identifică liniile relevante.
- `p` afișează liniile care corespund expresiei.
- `-n` previne afișarea imediată a celorlalte linii.
