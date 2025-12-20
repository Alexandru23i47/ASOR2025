# 1. Înlocuirea globală a textului într-un fișier

**Problemă:** Trebuie să înlocuim toate aparițiile unui cuvânt cu altul într-un fișier de configurare.

**Comandă:**

```bash
sed -i 's/oldapp/newapp/g' config.txt
```

**Explicație:**

- `sed` - invocă *stream editor*-ul (editorul de flux)
- `-i` - modifică fișierul direct (*in-place*), fără folosirea de copii temporare
- `s` - comanda de substituire
- `oldapp` - *pattern*-ul (șablonul) de căutat
- `newapp` - textul de înlocuire
- `g` - *flag* (fanionul) global (înlocuiește toate aparițiile din fiecare linie, nu doar prima)
- `config.txt` - fișierul care va fi modificat

---

# 2. Ștergerea liniilor care conțin un pattern

**Problemă:** Avem un fișier de jurnal cu multe linii conținând informații de depanare și dorim să ștergem aceste linii.

**Comandă:**

```bash
sed '/^DEBUG:/d' application.log > clean.log
```

**Explicație:**

- `sed` - *stream editor*-ul
- `/^DEBUG:/` - expresia regulată introdusă de depanare (linii care încep cu "DEBUG:")
- `^` - ancora de început de linie
- `d` - comanda *delete* (șterge liniile care se potrivesc)
- `application.log` - fișierul sursă
- `> clean.log` - redirectează *output*-ul (ieșirea) într-un fișier nou (dacă dorim să
  păstrăm informațiile rezultate după mai multe operații de depanare trebuie folosit
  operatorul `>>`)

---

# 3. Inserarea de text la începutul fiecărei linii

**Problemă:** Trebuie să adaugăm un prefix (static) fiecărei linii dintr-o listă textuală de informații.

**Comandă:**

```bash
sed 's/^/server: /' ip_list.txt > servers.conf
```

**Explicație:**

- `sed` - *stream editor*-ul
- `s` - comanda de substituire
- `^` - ancora de început de linie (poziția unde va fi inserat textul)
- `server: ` - textul care va fi adăugat la începutul fiecărei linii
- `ip_list.txt` - fișierul de *input* (fișierul cu date de intrare)
- `> servers.conf` - salvează rezultatul într-un fișier nou

---

# 4. Înlocuirea textului doar pe anumite linii

**Problemă:** Vrem să modificăm o valoare anume  doar într-o secțiune precizată a unui fișier (de exemplu, secțiunea constând din liniile 10-20).

**Comandă:**

```bash
sed '10,20s/port=8080/port=9090/g' config.ini
```

**Explicație:**

- `sed` - *stream editor*-ul
- `10,20` - plaja de adrese (*range*): aplică comanda doar pe liniile 10-20
- `s` - comanda de substituire
- `port=8080` - șablonul de căutat
- `port=9090` - textul de înlocuire
- `g` - *flag* (fanionul) *global*
- `config.ini` - fișierul de modificat

---

# 5. Afișarea doar a liniilor modificate

**Problemă:** Vrem să vizualizăm doar liniile care au fost modificate în mod efectiv dintr-un fișier cu rezultate de calcul, fără să fie afișat întreg fișierul.

**Comandă:**

```bash
sed -n 's/EROARE/ERROR/gp' raport.txt
```

**Explicație:**

- `sed` - *stream editor*-ul
- `-n` - suprimă afișarea automată a tuturor liniilor (*quiet mode*, modul *în tăcere*, neinteractiv)
- `s` - comanda de substituire
- `EROARE` - șablonul de căutat
- `ERROR` - textul de înlocuire
- `g` - fanionul global (toate aparițiile din linie)
- `p` - *flag print* (afișează o linia doar dacă substituirea din aceasta a reușit)
- `raport.txt` - fișierul sursă
- **Combinația `-n` cu `p`** face ca sed să afișeze doar liniile în care s-a făcut înlocuirea
