## Istoricul shell-urilor UNIX
Independența shell-ului față de sistemul de operare UNIX în sine a dus la dezvoltarea a zeci de shell-uri de-a lungul istoriei UNIX - deși doar câteva au atins o utilizare pe scară largă. Primul shell major a fost Bourne shell (numit după inventatorul său, Steven Bourne); a fost inclus în prima versiune populară de UNIX, versiunea 7, începând cu 1979. Bourne shell-ul este cunoscut pe sistem sub numele de sh. Deși UNIX a trecut prin multe, multe schimbări, Bourne shell-ul este încă popular și în esență neschimbat. Mai multe utilitare și funcții de administrare UNIX depind de acesta. Primul shell alternativ utilizat pe scară largă a fost shell-ul C sau csh. Acest text a fost scris de Bill Joy la Universitatea din California, Berkeley, ca parte a versiunii Berkeley Software Distribution (BSD) a UNIX, lansată la câțiva ani după versiunea 7. Shell-ul C își primește numele de la asemănarea comenzilor sale cu instrucțiunile din limbajul de programare C, ceea ce face shell-ul mai ușor de învățat pentru programatori pe sistemele UNIX.

Acesta acceptă o serie de caracteristici ale sistemului de operare (de exemplu, controlul joburilor; vezi Capitolul 8) care erau unice pentru BSD UNIX, dar care până acum au migrat la majoritatea celorlalte versiuni moderne.

De asemenea, are câteva caracteristici importante (de exemplu, aliasuri; vezi Capitolul 3) care fac mai ușoară utilizarea în general. În ultimii ani, o serie de alte shell-uri au devenit populare. Cea mai notabilă dintre acestea este shell-ul Korn. Acest shell este un produs comercial care încorporează cele mai bune caracteristici ale shell-urilor Bourne și C, plus multe caracteristici proprii.[1] Shell-ul Korn este similar cu bash în majoritatea aspectelor; ambele au o abundență de caracteristici care le fac ușoare de utilizat. Avantajul lui bash este că este gratuit. Pentru mai multe informații despre shell-ul Korn, consultați Anexa A.

## Caracteristicile (lui) bash
Deși shell-ul Bourne este încă cunoscut sub numele de shell-ul „standard”, bash devine din ce în ce mai popular. Pe lângă compatibilitatea sa cu shell-ul Bourne, include cele mai bune caracteristici ale shell-urilor C și Korn, precum și câteva avantaje proprii.

Modurile de editare din linia de comandă ale bash sunt caracteristicile care tind să atragă oamenii către acestaîn primul rând. Cu editarea din linia de comandă, este mult mai ușor să te întorci și să corectezi greșelile sau
să modifici comenzile anterioare decât este cu mecanismul istoric al shell-ului C - iarshell-ul Bourne nu îți permite deloc să faci acest lucru.Cealaltă caracteristică majoră a bash, destinată în principal utilizatorilor interactivi, este controlul joburilor.După cum explică Capitolul 8, controlul joburilor îți oferă posibilitatea de a opri, porni și pune în pauză
orice număr de comenzi în același timp. Această caracteristică a fost împrumutată aproape textual
din shell-ul C.Restul avantajelor importante ale bash sunt destinate în principal persoanelor care personalizează shell-ul șiprogramatorilor. Are multe opțiuni și variabile noi pentru personalizare, iar caracteristicile sale de programareau fost extinse semnificativ pentru a include definirea funcțiilor, mai multe structuri de control, aritmetică întreagă, control avansat I/O și multe altele.

## Obținerea (lui) bash
Este posibil să utilizați sau nu bash în acest moment. Administratorul dvs. de sistem probabil ți-a configurat contul cu orice shell pe care îl folosește ca „standard” pe sistem.
Este posibil să nici nu fi știut că există mai mult de un shell disponibil. Totuși, este ușor pentru dvs. să determinați ce shell utilizați. Conectați-vă la sistem și tastați **echo $SHELL** la prompt. Veți vedea un răspuns care conține sh, csh, ksh sau bash; acestea denotă shell-urile Bourne, C, Korn și bash, respectiv.
(Există, de asemenea, posibilitatea să utilizați un alt shell, cum ar fi tcsh.) Dacă nu utilizați bash și doriți să îl utilizați, atunci trebuie mai întâi să aflați dacă există pe sistemul dvs. Tastați pur și simplu **bash**. Dacă primiți un nou prompt constând din câteva informații urmate de un semn dolar (de exemplu, **bash3 $**), atunci totul este în regulă; tastați **exit** pentru a reveni la shell-ul dvs. normal.

Dacă primiți un mesaj „negăsit”, este posibil ca sistemul dumneavoastră să nu îl aibă. Întrebați administratorul de sistem
sau un alt utilizator cu experiență; există posibilitatea să aveți
o versiune de bash instalată pe sistem într-un loc (director) care în mod normal nu vă este
accesibil. Dacă nu, citiți Capitolul 11 ​​pentru a afla cum puteți obține o versiune
de bash.

Odată ce știți că aveți bash pe sistem, îl puteți invoca din oricealtă shell pe care o utilizați tastând bash ca mai sus. Cu toate acestea, este mult mai bine să îl instalați ca
shell de conectare, adică shell-ul pe care îl primiți automat de fiecare dată când vă conectați.
Este posibil să puteți face instalarea singur. Iată instrucțiuni care sunt conceputesă funcționeze pe cea mai largă varietate de sisteme UNIX. Dacă ceva nu funcționează (de exemplu,tastați o comandă și primiți un mesaj de eroare „negăsit” sau o linie goală carăspuns), va trebui să abandonați procesul și să consultați administratorul de sistem. Alternativ,consultați Capitolul 12, unde demonstrăm o modalitate mai puțin simplă dea înlocui carcasa actuală.


Trebuie să aflați unde se află bash pe sistemul dvs., adică în ce director este instalat. Puteți găsi locația tastând **whereis bash** (mai ales dacă folosiți shell-ul C); dacă aceasta nu funcționează, încercați **whence bash**, **which bash** sau această
comandă complexă:

```bash
grep bash /etc/passwd | awk -F: '{print $7}' | sort -u
```

Ar trebui să vedeți un răspuns care arată ca **/bin/bash** sau **/usr/local/bin/bash**.
Pentru a instala bash ca shell de conectare, tastați **chsh *nume-bash***, unde *nume-bash* este răspunsul pe care l-ați primit la comanda whereis (sau orice altceva care a funcționat). De exemplu: 

```bash
chsh /usr/local/bin/bash
```

Veți primi fie un mesaj de eroare care spune că shell-ul este invalid, fie vi se va solicita parola. Tastați parola, apoi deconectați-vă și conectați-vă din nou pentru a începe să utilizați bash.

## Utilizarea interactiva shell

Când utilizați shell-ul interactiv, intrați într-o sesiune de autentificare care începe atunci când vă conectați și se termină atunci când tastați exit sau logout sau apăsați `CTRL-D`. În timpul unei sesiuni de autentificare,
tastați linii de comandă în shell; acestea sunt linii de text care se termină în RETURN pe care le tastați în terminal sau pe stația de lucru.
În mod implicit, shell-ul vă solicită fiecare comandă cu un șir de informații urmat de un semn dolar, deși, așa cum veți vedea în Capitolul 3, întregul prompt poate fi modificat.

## Comenzi, argumente si optiuni

Liniile de comandă shell constau dintr-unul sau mai multe cuvinte, care sunt separate pe o linie de comandăprin spații sau TAB-uri. Primul cuvânt de pe linie este comanda. Restul (dacă
există) sunt argumente (numite și parametri) ale comenzii, care sunt nume alelucrurilor asupra cărora va acționa comanda.
De exemplu, linia de comandă 

```bash
lp myfile
```

constă din comanda **lp** (print a file) și argumentul unic **myfile**. lp tratează myfile ca nume de fișier de imprimat. Argumentele sunt adesea nume de fișiere, dar nu neapărat: în linia de comandă 

```bash
mail cam
```

programul de mail tratează cam ca nume de utilizator către care va fi trimis un mesaj.

O opțiune este un tip special de argument care oferă comenzii informații specifice despre ceea ce ar trebui să facă. Opțiunile constau de obicei dintr-o cratimă urmată de o literă; spunem „de obicei” deoarece aceasta este o convenție mai degrabă decât o regulă strictă.
Comanda 

```bash
lp -h myfile
```

 conține opțiunea **-h**, care îi spune lui lp să nu imprime „pagina banner” înainte de a imprima fișierul.
Uneori, opțiunile au propriile argumente. De exemplu, **lp -d lp1 -h myfile** are două opțiuni și un argument. Prima opțiune este **-d lp1**, ceea ce înseamnă „Trimiteți ieșirea către imprimanta (destinația) numită lp1”. A doua opțiune și argumentul sunt aceleași ca în exemplul anterior.

