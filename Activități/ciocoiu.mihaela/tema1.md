
# Istoria Shell-urilor UNIX

Independența shell-ului față de sistemul de operare UNIX în sine a dus la dezvoltarea a zeci de shell-uri de-a lungul istoriei UNIX — deși doar câteva au avut o utilizare pe scară largă.

Primul shell important a fost shell-ul Bourne (numit după inventatorul său, Steven Bourne); a fost inclus în prima versiune populară de UNIX, Versiunea 7, începând cu 1979. Bourne Shell  este cunoscut în sistem ca *sh*. Deși UNIX a trecut prin multe schimbări, shell-ul Bourne este încă popular și esențial nealterat. Mai multe utilitare și funcții de administrare UNIX depind de el.

Primul shell alternativ utilizat pe scară largă a fost shell-ul C, sau *csh*. Acesta a fost scris de Bill Joy la Universitatea din California, Berkeley, ca parte a distribuției Berkeley Software Distribution (BSD) a UNIX-ului, care a apărut la câțiva ani după Versiunea 7.

Shell-ul C își trage numele din asemănarea comenzilor sale cu declarațiile din limbajul de programare C, ceea ce îl face mai ușor de învățat pentru programatorii de sisteme UNIX. El suportă un număr mare de funcții ale sistemului de operare (de ex. controlul job-urilor; vezi Capitolul 8) care erau unice în BSD UNIX, dar care acum au fost preluate de majoritatea versiunilor moderne. De asemenea, are câteva funcții importante (de ex. aliasurile; vezi Capitolul 3) care îl fac în general mai ușor de utilizat.

În ultimii ani, un număr de alte shell-uri au devenit populare. Cel mai notabil dintre acestea este *Korn shell*. Acesta este un produs comercial care înglobează cele mai bune caracteristici ale shell-urilor Bourne și C, plus multe funcții proprii.  
Shell-ul Korn poate fi descărcat gratuit, dar vine cu o licență care poate solicita plată în cazul utilizării sale în anumite situații.

Shell-ul Korn este similar cu *bash* în majoritatea privințelor; ambele au o multitudine de funcții care le fac ușor de utilizat. Avantajul lui *bash* este că este gratuit. Pentru informații suplimentare despre shell-ul Korn, vezi Anexa A.



# Caracteristicile bash

Deși shell-ul Bourne este încă considerat „shell-ul standard”, bash devine din ce în ce mai popular. Pe lângă compatibilitatea sa cu shell-ul Bourne, acesta include cele mai bune funcționalități ale shell-urilor C și Korn, precum și mai multe avantaje proprii. GNU este un acronim recursiv, provenind de la „GNU’s Not UNIX”.

Unul dintre aspectele care atrag cel mai mult utilizatorii către bash este modul său de editare a liniei de comandă. Cu editarea liniei de comandă, este mult mai ușor să revii și să corectezi greșeli sau să modifici comenzi anterioare comparativ cu mecanismul de istoric al shell-ului C — iar shell-ul Bourne nu permite deloc acest lucru.

O altă caracteristică importantă a bash, destinată în special utilizatorilor interactivi, este controlul joburilor (job control). După cum explică Capitolul 8, controlul joburilor îți oferă posibilitatea de a opri, porni și întrerupe orice număr de comenzi în același timp. Această funcționalitate a fost preluată aproape identic din shell-ul C.

Restul avantajelor importante ale bash sunt destinate în principal persoanelor care doresc să își customizeze shell-ul sau programatorilor. Bash oferă numeroase opțiuni și variabile noi pentru personalizare, iar funcționalitățile sale de programare au fost semnificativ extinse pentru a include definirea de funcții, mai multe structuri de control, aritmetică pe numere întregi, control avansat al I/O și altele.

# Obținerea shell-ului *bash*

Este posibil să folosești sau nu *bash* în acest moment. Administratorul tău de sistem probabil ți-a configurat contul cu shell-ul pe care îl utilizează el ca “standard” pe sistem. Este posibil nici măcar să nu fi știut că există mai multe shell-uri disponibile.

Totuși, este foarte ușor să afli ce shell folosești. Autentifică-te și tastează:

```bash
echo $SHELL
```

Vei vedea un răspuns care conține sh, csh,sh sau bash; acestea reprezintă shell-urile Bourne, C, Korn și bash, respectiv. (Există și posibilitatea să folosești un alt shell, cum ar fi tcsh.)


### Verificarea existenței bash pe sistem

Dacă nu folosești *bash* și vrei să îl folosești, trebuie mai întâi să verifici dacă există pe sistemul tău. Tastează: 

```bash
bash
```

Dacă primești un nou prompt ce conține unele informații urmate de un semn dolar (de exemplu bash3 $), atunci totul este în regulă. Tastează **exit** pentru a reveni la shell-ul tău obișnuit.

Dacă primești mesajul „not found”, este posibil ca sistemul tău să nu aibă bash instalat. Întreabă administratorul de sistem sau un utilizator experimentat: e posibil ca bash să fie instalat într-un director care nu este accesibil în mod normal. Dacă nu există, consultă *Capitolul 11* pentru a afla cum poți obține o versiune de bash.


### Folosirea bash ca shell de login

După ce știi sigur că bash este instalat, îl poți porni din orice alt shell tastând bash. Totuși, este mult mai bine să îl setezi ca *shell de login*, adică shell-ul care pornește automat la autentificare.

Este posibil să poți face această schimbare singur. Următoarele instrucțiuni sunt concepute pentru a funcționa pe cât mai multe sisteme UNIX. Dacă ceva nu funcționează (de exemplu primești un mesaj „not found”), întrerupe procesul și consultă administratorul. Alternativ, poți consulta *Capitolul 12*, unde este descrisă o metodă mai puțin directă pentru a înlocui shell-ul curent.


### Găsirea locației în care este instalat bash

Trebuie să afli unde este instalat bash, adică în ce director se află. Poți încerca: whereis bash(în special dacă folosești C shell). Dacă nu funcționează, încearcă:
**whence bash**, **which bash** sau comanda mai complexă:

```bash
grep bash /etc/passwd | awk -F: '{print $7}' | sort -u
```

Ar trebui să vezi un răspuns de forma:

```bash
/bin/bash
/usr/local/bin/bash
```

### Setarea bash ca shell de login

Pentru a seta bash ca shell de login, tastează: **chsh bash-name**,
unde *bash-name* este calea completă găsită mai devreme. De exemplu: 

```bash
chsh /usr/local/bin/bash
```

Vei primi fie un mesaj de eroare care spune că shell-ul este invalid, fie ți se va cere parola. Introdu parola, apoi deloghează-te și autentifică-te din nou pentru a începe să folosești bash.

# Utilizarea interactivă a shell-ului

Atunci când folosești shell-ul în mod interactiv, intri într-o sesiune de autentificare care începe în momentul în care te loghezi și se termină când tastezi exit sau logout sau când apeși `CTRL-D`. 
În timpul unei sesiuni de lucru, tastezi *linii de comandă* pentru shell — acestea sunt linii de text care se încheie cu tasta *RETURN* și pe care le introduci în terminalul sau stația ta de lucru.

În mod implicit, shell-ul îți afișează un *prompt* pentru fiecare comandă, alcătuit dintr-un șir de informații urmat de simbolul dolar `$`. Totuși, așa cum vei vedea în Capitolul 3, întregul prompt poate fi modificat.



# Comenzi, argumente și opțiuni

Liniile de comandă din shell sunt alcătuite din unul sau mai multe cuvinte, separate pe linia de comandă prin spații sau TAB-uri. *Primul cuvânt* de pe linie este *comanda. Restul cuvintelor (dacă există) sunt **argumente* (numite și parametri) ale comenzii, reprezentând nume ale obiectelor asupra cărora acționează comanda.

De exemplu, linia de comandă: 

```bash
lp myfile
```

conține comanda lp (care imprimă un fișier) și argumentul myfile. Comanda lp tratează myfile ca fiind numele fișierului de imprimat.
Argumentele sunt adesea nume de fișiere, dar nu întotdeaun în comanda: 

```bash
mail cam
```

programul mail tratează cam ca fiind numele utilizatorului către care va fi trimis mesajul.



### Opțiuni

O *opțiune* este un tip special de argument care oferă comenzii informații specifice despre ce ar trebui să facă. Opțiunile constau, de obicei, dintr-o cratimă urmată de o literă. Spunem „de obicei”, deoarece aceasta este o convenție, nu o regulă strictă.

Comanda: 

```bash
lp -h myfile
```

conține opțiunea -h, care îi spune comenzii lp *să nu tipărească pagina de antet* înainte de a tipări fișierul.

Uneori, opțiunile au propriile lor argumente. De exemplu:

```bash
lp -d lp1 -h myfile
```

conține *două opțiuni* și *un argument*. Prima opțiune este: **-d lp1**,

care înseamnă „Trimite ieșirea către imprimanta (destinația) numită lp1”. A doua opțiune și argumentul sunt identice cu cele din exemplul anterior.

