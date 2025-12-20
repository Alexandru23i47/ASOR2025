# Tema 2 – Editorul de fluxuri sed

## Problema 1: Corectarea automată a unui cuvânt greșit într-un fișier text

### Enunțul problemei
Într-un fișier text apar mai multe linii care conțin cuvântul scris greșit erorr.
Este necesară corectarea tuturor aparițiilor în error, fără a edita manual fișierul.

### Rezolvare
```bash
sed 's/erorr/error/g' fisier.txt
``` 
Explicație
+	sed procesează fișierul linie cu linie
+	s este comanda de substituție definită în manualul oficial
+	erorr reprezintă expresia regulată căutată
+	error este textul corect
+	g aplică substituția pentru toate aparițiile din fiecare linie
+	rezultatul este afișat la ieșirea standard

⸻

Problema 2: Afișarea unei singure linii pentru verificare

Enunțul problemei

Un fișier conține un număr mare de linii, iar utilizatorul dorește să verifice
doar conținutul liniei a 8-a.

Rezolvare
```bash 
sed -n '8p' fisier.txt
``` 
Explicație
+	-n dezactivează afișarea implicită a tuturor liniilor
+	8 este adresa liniei
+	p afișează linia indicată
+	doar linia a 8-a este tipărită

⸻

Problema 3: Eliminarea liniilor goale dintr-un fișier de configurare

Enunțul problemei

Un fișier de configurare conține linii goale care îngreunează citirea și procesarea
automată a acestuia.

Rezolvare
```bash
sed '/^$/d' configurare.txt
```

Explicație
+	/^$/ este o expresie regulată standard ce identifică liniile goale
+	^ marchează începutul liniei
+	$ marchează sfârșitul liniei
+	d șterge liniile care corespund expresiei
+	liniile rămase sunt afișate

⸻

Problema 4: Extragerea unui interval de linii dintr-un fișier jurnal

Enunțul problemei

Pentru analiză, este necesară afișarea doar a liniilor cuprinse între 15 și 25
dintr-un fișier de tip log.

Rezolvare
```bash
sed -n '15,25p' log.txt
```

Explicație
+	15,25 reprezintă intervalul de linii
+	p afișează liniile din interval
+	-n oprește afișarea implicită
+	doar liniile selectate sunt tipărite

⸻

Problema 5: Inserarea unei linii explicative într-un fișier

Enunțul problemei

Este necesară inserarea unui comentariu explicativ înaintea liniei a 4-a
dintr-un fișier text, fără modificarea manuală a acestuia.

Rezolvare
```bash
sed '4i\# Linie explicativă' fisier.txt
``` 
Explicație
+	4 este adresa liniei
+	i (insert) inserează text înaintea liniei specificate
+	textul inserat este afișat în rezultatul final
+	fișierul original rămâne nemodificat
