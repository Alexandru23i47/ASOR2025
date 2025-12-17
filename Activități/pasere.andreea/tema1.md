# Istoria shell-urilor UNIX

Independența shell-ului față de sistemul de operare UNIX *per se* a dus la dezvoltarea a zeci de shell-uri de-a lungul istoriei UNIX — deși doar câteva au ajuns să fie utilizate pe scară largă.

Primul shell important a fost *shell-ul Bourne* (denumit după inventatorul său, Steven Bourne); acesta a fost inclus în prima versiune populară a UNIX, Versiunea 7, începând cu 1979. Shell-ul Bourne este cunoscut în sistem ca *sh*. Deși UNIX a trecut prin multe schimbări, shell-ul Bourne este încă popular și practic neschimbat. Mai multe utilitare UNIX și funcții de administrare depind de el.

Primul shell alternativ utilizat pe scară largă a fost shell-ul C, sau *csh*. Acesta a fost scris de Bill Joy la Universitatea din California, Berkeley, ca parte a versiunii UNIX Berkeley Software Distribution (BSD), care a apărut la câțiva ani după Versiunea 7.

Shell-ul C își ia numele de la asemănarea comenzilor sale cu instrucțiunile din limbajul de programare C, ceea ce îl face mai ușor de învățat pentru programatorii familiarizați cu sistemele UNIX. Acesta suportă o serie de funcții ale sistemului de operare (de exemplu, controlul job-urilor; vezi Capitolul 8) care erau unice pentru BSD UNIX, dar care au fost migrate în majoritatea versiunilor moderne. De asemenea, are câteva funcții importante (de exemplu, alias-uri; vezi Capitolul 3) care îl fac mai ușor de utilizat în general.

În ultimii ani, un număr de alte shell-uri au devenit populare. Cel mai notabil este shell-ul Korn. Acest shell este un produs comercial care încorporează cele mai bune caracteristici ale shell-urilor Bourne și C, plus multe caracteristici proprii.  
Shell-ul Korn este similar cu *bash* din multe puncte de vedere; ambele au numeroase caracteristici care le fac ușor de utilizat. Avantajul lui *bash* este că este gratuit. Pentru mai multe informații despre shell-ul Korn, vezi Anexa A.

# Caracteristici ale bash

Deși shell-ul Bourne este încă cunoscut ca shell-ul "standard", *bash* devine din ce în ce mai popular. Pe lângă compatibilitatea cu shell-ul Bourne, acesta include cele mai bune caracteristici ale shell-urilor C și Korn, precum și mai multe avantaje proprii. Modurile de editare în linia de comandă ale *bash* sunt caracteristicile care tind să atragă cel mai mult utilizatorii la început. Cu editarea liniei de comandă, este mult mai ușor să revii și să corectezi greșeli sau să modifici comenzi anterioare decât este cu mecanismul de istoric al shell-ului C—iar shell-ul Bourne nu îți permite deloc acest lucru.

Cealaltă caracteristică majoră a *bash*, destinată în principal utilizatorilor interactivi, este controlul joburilor. După cum explică Capitolul 8, controlul joburilor îți oferă posibilitatea de a opri, porni și întrerupe orice număr de comenzi în același timp. Această funcționalitate a fost împrumutată aproape mot-a-mot din shell-ul C.

Restul avantajelor importante ale *bash* sunt destinate în principal personalizatorilor de shell și programatorilor. Acesta are multe opțiuni și variabile noi pentru personalizare, iar caracteristicile sale de programare au fost extinse semnificativ pentru a include definirea de funcții, mai multe structuri de control, aritmetică pe numere întregi, control avansat al I/O și altele.

# Obținerea bash

Este posibil să folosești sau nu *bash* în acest moment. Administratorul sistemului tău probabil ți-a configurat contul cu shell-ul pe care îl folosește el ca “standard” pe sistem. Poate nici măcar nu ai fost conștient că există mai multe shell-uri disponibile.

Totuși, este ușor să determini ce shell folosești. Autentifică-te în sistem și tastează **echo $SHELL** la prompt. Vei vedea un răspuns care conține **sh**, **csh**, **ksh** sau **bash**; acestea corespund shell-urilor Bourne, C, Korn și *bash*. (Există și șansa să folosești un alt shell, precum *tcsh*.)

Dacă nu folosești *bash* și vrei să îl folosești, trebuie mai întâi să afli dacă există pe sistemul tău. Tastează pur și simplu **bash**. Dacă primești un nou prompt care conține o informație urmată de un semn al dolarului (de ex. **bash3 $**), atunci totul este în regulă; tastează **exit** pentru a te întoarce la shell-ul normal.

Dacă primești mesajul „not found”, este posibil ca sistemul tău să nu îl aibă. Întreabă administratorul de sistem sau un utilizator experimentat; există șansa ca o versiune de *bash* să fie instalată undeva într-un director la care nu ai acces de obicei. Dacă nu, consultă Capitolul 11 pentru a afla cum poți obține o versiune de *bash*.

Odată ce știi că ai bash pe sistem, îl poți porni din orice alt shell tastând **bash** ca mai sus. Totuși, este mult mai bine să îl instalezi ca *login shell*, adică shell-ul care pornește automat atunci când te autentifici. Este posibil să poți face instalarea singur. Instrucțiunile de mai jos sunt concepute să funcționeze pe cât mai multe sisteme UNIX. Dacă ceva nu funcționează (de exemplu, tastezi o comandă și primești „not found” sau doar o linie goală), va trebui să renunți la proces și să mergi la administratorul tău. Alternativ, consultă Capitolul 12, unde prezentăm o metodă mai puțin directă de înlocuire a shell-ului curent.

Trebuie să afli unde se află bash pe sistemul tău, adică în ce director este instalat. Poți găsi locația tastând **whereis bash** (în special dacă folosești C shell); dacă nu funcționează, încearcă **whence bash**, **which bash** sau această comandă mai complexă:
```bash
grep bash /etc/passwd | awk -F: '{print $7}' | sort -u
```

Ar trebui să vezi un răspuns de forma */bin/bash* sau */usr/local/bin/bash*.

Pentru a instala *bash* ca login shell, tastează **chsh** *bash-name*, unde *bash-name* este răspunsul obținut în urma comenzii **whereis** (sau oricare dintre metodele care au funcționat). De exemplu:
```bash
chsh /usr/local/bin/bash
```
Vei primi fie un mesaj de eroare care spune că shell-ul este invalid, fie ți se va cere parola. Tastează parola, apoi deloghează-te și loghează-te din nou pentru a începe să folosești *bash*.

# Utilizarea interactivă a shell-ului

Când folosești shell-ul în mod interactiv, intri într-o sesiune de autentificare care începe atunci când te conectezi și se încheie când tastezi **exit** sau **logout** sau apeși CTRL-D. În timpul unei sesiuni de autentificare, tastezi *linii de comandă* în shell; acestea sunt linii de text care se încheie cu RETURN și pe care le introduci în terminalul sau stația ta de lucru.

Implicit, shell-ul îți solicită fiecare comandă cu un șir informativ urmat de un semn dolar, deși, după cum vei vedea în Capitolul 3, întregul prompt poate fi modificat.

# Comenzi, argumente și opțiuni

Liniile de comandă shell sunt formate din unul sau mai multe cuvinte, separate prin spații sau TAB-uri. Primul cuvânt de pe linie este *comanda*. Restul (dacă există) sunt *argumente* (numite și *parametrii*) ale comenzii, reprezentând nume de lucruri asupra cărora comanda va acționa.

De exemplu, linia de comandă **lp myfile** constă din comanda *lp* (print a file) și argumentul unic **myfile**. *lp* tratează **myfile** ca numele unui fișier de imprimat. Argumentele sunt adesea nume de fișiere, dar nu neapărat: în comanda **mail cam**, programul *mail* tratează **cam** ca numele utilizatorului către care va fi trimis mesajul.

O *opțiune* este un tip special de argument care oferă comenzii informații specifice despre ceea ce trebuie să facă. Opțiunile constau de obicei dintr-o cratimă urmată de o literă; spunem "de obicei" deoarece aceasta este o convenție, mai degrabă decât o regulă strictă. Comanda **lp -h myfile** conține opțiunea **-h**, care îi spune lui *lp* să nu imprime "pagina banner" înainte de a imprima fișierul.

Uneori, opțiunile au propriile argumente. De exemplu, **lp -d lp1 -h myfile** are două opțiuni și un argument. Prima opțiune este **-d lp1** , ceea ce înseamnă "Trimiteți ieșirea către imprimanta (destinație) numită **lp1**". A doua opțiune și argumentul sunt aceleași ca în exemplul anterior.
