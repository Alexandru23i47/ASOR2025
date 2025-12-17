# Istoria shell-urilor UNIX

Independența shell-ului față de sistemul de operare UNIX per se a dus la dezvoltarea a zeci de shell-uri de-a lungul istoriei UNIX — deși doar câteva au ajuns să fie utilizate pe scară largă.

Primul shell important a fost **Bourne shell** (denumit după inventatorul său, Steven Bourne); acesta a fost inclus în prima versiune populară de UNIX, Versiunea 7, începând cu 1979. Bourne shell este cunoscut în sistem sub numele `sh`. Deși UNIX a trecut prin multe schimbări, Bourne shell a rămas popular și, în esență, neschimbat. Mai multe utilitare UNIX și funcții de administrare depind de acesta.

Primul shell alternativ larg utilizat a fost **C shell**, sau `csh`. Acesta a fost scris de Bill Joy la Universitatea din California, Berkeley, și a apărut ca parte a distribuției Berkeley Software Distribution (BSD) a UNIX, care a apărut la câțiva ani după Versiunea 7.

C shell își ia numele de la asemănarea comenzilor sale cu instrucțiunile din limbajul de programare C, ceea ce îl face mai ușor de învățat pentru programatorii de pe sistemele UNIX. Acesta suportă mai multe caracteristici ale sistemului de operare (de exemplu, controlul joburilor; vezi Capitolul 8) care erau specifice UNIX BSD, dar care, între timp, au fost preluate și de majoritatea versiunilor moderne. De asemenea, are câteva funcții importante (de exemplu, alias-uri; vezi Capitolul 3) care îl fac, în general, mai ușor de utilizat.

În ultimii ani, un număr de alte shell-uri au devenit populare. Cel mai notabil dintre acestea este **Korn shell**. Acest shell este un produs comercial care încorporează cele mai bune caracteristici ale Bourne shell și ale C shell, precum și multe funcții proprii. Korn shell este similar cu bash în majoritatea privințelor; ambele au o abundență de caracteristici care le fac ușor de folosit. Avantajul lui bash este că este gratuit. Pentru mai multe informații despre Korn shell, vezi Anexa A.

## Caracteristici ale bash

Deși Bourne shell este încă cunoscut ca fiind shell-ul „standard", bash devine din ce în ce mai popular. Pe lângă compatibilitatea cu Bourne shell, acesta include cele mai bune caracteristici ale C shell și ale Korn shell, precum și câteva avantaje proprii. Funcțiile de editare a liniei de comandă ale lui bash sunt caracteristicile care tind să-i atragă cel mai mult pe utilizatori. Cu editarea liniei de comandă, este mult mai ușor să te întorci și să corectezi greșelile din comenzile tastate anterior decât este cu istoricul shell-ului C — iar shell-ul Bourne nu îți permite deloc acest lucru.

Cealaltă caracteristică majoră a lui bash, destinată în principal utilizării interactive, este **controlul job-urilor**. Așa cum explică Capitolul 8, controlul job-urilor îți oferă abilitatea de a opri, porni, staționa și gestiona mai multe comenzi în același timp. Această funcție a fost împrumutată aproape integral din shell-ul C.

Restul funcțiilor importante ale lui bash sunt destinate în principal personalizatorilor de shell și programatorilor. Are multe opțiuni și variabile pentru personalizare, iar caracteristicile sale de programare au fost extinse semnificativ pentru a include definirea funcțiilor, structuri de control mai complexe, aritmetică internă, control avansat al I/O și multe altele.

## Obținerea bash

Este posibil să folosești sau să nu folosești bash chiar acum. Administratorul tău de sistem probabil ți-a configurat contul cu shell-ul pe care îl folosește el ca „standard" pe sistem. Poate nici măcar nu ai fost conștient că există mai multe shell-uri disponibile.

Totuși, este ușor să determini ce shell folosești. Autentifică-te în sistem și tastează:

```bash
echo $SHELL
```

la prompt. Vei vedea un răspuns care conține `sh`, `csh`, `ksh` sau `bash`; acestea denotă shell-urile Bourne, C, Korn și respectiv bash.

(Există și șansa să folosești un alt shell precum `tcsh`.)

Dacă nu folosești bash și vrei să o faci, trebuie mai întâi să afli dacă există pe sistemul tău. Tastează doar:

```bash
bash
```

Dacă primești un prompt nou care conține unele informații urmate de un semn dolar (de ex. `bash3$`), atunci totul este bine; tastează `exit` pentru a reveni la starea normală.

Dacă primești un mesaj de tip „not found", este posibil ca sistemul tău să nu îl aibă. Întreabă-ți administratorul de sistem sau o persoană mai experimentată; este posibil să existe o versiune de bash instalată într-un loc (director) care nu este accesibil în mod normal pentru tine. Dacă nu, consultă Capitolul 11 pentru a afla cum poți obține o versiune de bash.

Odată ce știi că ai bash pe sistem, îl poți activa ca shell implicit, tastând în sistem:

```bash
chsh bash-name
```

unde `bash-name` este răspunsul primit când ai tastat whereis command (sau orice a funcționat). De exemplu:

```bash
% chsh /usr/local/bin/bash
```

Vei primi fie un mesaj de eroare care spune că shell-ul este invalid, fie vei fi întrebat de parola ta. Tasteaz-o, apoi deloghează-te și loghează-te din nou pentru a începe să folosești bash.

## Utilizarea interactivă a shell-ului

Când folosești shell-ul interactiv, intri într-o sesiune de login care începe când te conectezi și se termină când tastezi `exit` sau `logout` ori apeși `CTRL-D`. Într-o sesiune interactivă, tastezi linii de comandă în shell; acestea sunt linii de text care se termină cu `ENTER` și pe care le trimiți terminalului sau stației de lucru.

Implicit, shell-ul îți afișează pentru fiecare comandă un șir informativ urmat de un semn dolar, deși așa cum vei vedea în Capitolul 3, acest prompt poate fi schimbat.

### Comenzi, argumente și opțiuni

Liniile de comandă ale shell-ului sunt compuse din unul sau mai multe cuvinte, separate prin spații sau taburi. Primul cuvânt de pe linie este **comanda**. Restul (dacă există) sunt **argumente** (numite și parametri) pentru comandă, care sunt moduri prin care comanda știe ce să facă.

De exemplu, linia de comandă:

```bash
lp myfile
```

conține comanda `lp` (tipărește un fișier) și argumentul `myfile`. `lp` tratează `myfile` ca numele fișierului care trebuie tipărit. Argumentele sunt deseori nume de fișiere, dar nu neapărat; în comanda:

```bash
line mail
```

programul `mail` folosește numele de utilizator ca argument pentru a trimite un mesaj.

### Opțiuni

O **opțiune** este un tip special de argument care oferă comenzii informații specifice despre ce trebuie să facă. Opțiunile constau de obicei dintr-o cratimă urmată de o literă, deși spunem „de obicei" pentru că aceasta este o convenție și nu o regulă strictă. Comanda:

```bash
lp -h myfile
```

conține opțiunea `-h`, care îi spune lui `lp` să nu tipărească „pagina-banner" înainte de a tipări fișierul.

Uneori, opțiunile își au propriile argumente. De exemplu:

```bash
lp -d lp1 -h myfile
```

are două opțiuni și un argument. Prima opțiune este:

```bash
-d lp1
```

care înseamnă „Trimite ieșirea către imprimanta (destinația) numită lp1". A doua opțiune și argumentul sunt aceleași ca în exemplul anterior.
