# 1. Înlocuirea globală a textului într-un fișier

**Problemă:** Trebuie să înlocuiești toate aparițiile unui cuvânt cu altul într-un fișier de configurare.

**Comandă:**
```bash
sed -i 's/oldapp/newapp/g' config.txt
```

**Explicație:**
- `sed` - invocă stream editor
- `-i` - modifică fișierul direct (in-place)
- `s` - comanda de substituire
- `oldapp` - pattern-ul de căutat
- `newapp` - textul de înlocuire
- `g` - flag global (înlocuiește toate aparițiile din fiecare linie, nu doar prima)
- `config.txt` - fișierul care va fi modificat

---

# 2. Ștergerea liniilor care conțin un pattern

**Problemă:** Ai un fișier de log cu multe linii de debug și vrei să le ștergi.

**Comandă:**
```bash
sed '/^DEBUG:/d' application.log > clean.log
```

**Explicație:**
- `sed` - stream editor
- `/^DEBUG:/` - pattern regex (linii care încep cu "DEBUG:")
- `^` - ancora de început de linie
- `d` - comanda delete (șterge liniile care se potrivesc)
- `application.log` - fișierul sursă
- `> clean.log` - redirectează output-ul într-un fișier nou

---

# 3. Inserarea de text la începutul fiecărei linii

**Problemă:** Trebuie să adaugi un prefix la fiecare linie dintr-o listă.

**Comandă:**
```bash
sed 's/^/server: /' ip_list.txt > servers.conf
```

**Explicație:**
- `sed` - stream editor
- `s` - comanda de substituire
- `^` - ancora de început de linie (poziția unde va fi inserat textul)
- `server: ` - textul care va fi adăugat la începutul fiecărei linii
- `ip_list.txt` - fișierul de input
- `> servers.conf` - salvează rezultatul într-un fișier nou

---

# 4. Înlocuirea textului doar pe anumite linii

**Problemă:** Vrei să modifici o valoare doar într-o anumită secțiune a fișierului (de exemplu, liniile 10-20).

**Comandă:**
```bash
sed '10,20s/port=8080/port=9090/g' config.ini
```

**Explicație:**
- `sed` - stream editor
- `10,20` - adresare (range): aplică comanda doar pe liniile 10-20
- `s` - comanda de substituire
- `port=8080` - pattern-ul de căutat
- `port=9090` - textul de înlocuire
- `g` - flag global
- `config.ini` - fișierul de modificat

---

# 5. Afișarea doar a liniilor modificate

**Problemă:** Vrei să vezi doar liniile care au fost efectiv modificate, fără să afișezi tot fișierul.

**Comandă:**
```bash
sed -n 's/EROARE/ERROR/gp' raport.txt
```

**Explicație:**
- `sed` - stream editor
- `-n` - suprimă afișarea automată a tuturor liniilor (quiet mode)
- `s` - comanda de substituire
- `EROARE` - pattern-ul de căutat
- `ERROR` - textul de înlocuire
- `g` - flag global (toate aparițiile din linie)
- `p` - flag print (afișează linia doar dacă substituirea a reușit)
- `raport.txt` - fișierul sursă
- **Combinația `-n` cu `p`** face ca sed să afișeze doar liniile unde s-a făcut înlocuirea
