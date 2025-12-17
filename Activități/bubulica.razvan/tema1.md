# 1.History of UNIX Shells


Istoria shell-urilor UNIX

Independența shell-ului față de sistemul de operare UNIX propriu-zis a dus la dezvoltarea multor shell-uri de-a lungul istoriei UNIX — deși doar câteva au ajuns la utilizare largă.

Primul shell important a fost Bourne shell (numit după inventatorul său, Steven Bourne); acesta a fost inclus în prima versiune populară de UNIX, Version 7, începând cu 1979. Bourne shell este cunoscut în sistem sub numele sh. Deși UNIX a trecut prin foarte multe schimbări, Bourne shell este încă popular și practic neschimbat. Numeroase utilitare UNIX și elemente de administrare depind de el.

Primul shell alternativ utilizat pe scară largă a fost C shell, sau csh. Acesta a fost scris de Bill Joy la Universitatea California din Berkeley, ca parte a distribuției BSD (Berkeley Software Distribution) apărută câțiva ani după Version 7.

C shell își ia numele de la asemănarea comenzilor sale cu instrucțiunile din limbajul C, ceea ce îl face mai ușor de învățat pentru programatorii de pe sisteme UNIX. El suportă o serie de funcționalități ale sistemului de operare (de ex. job control; vezi Capitolul 8) care au fost inițial specifice BSD UNIX, dar care între timp au migrat în majoritatea versiunilor moderne. De asemenea, are câteva facilități importante (de ex. aliases; vezi Capitolul 3) care, în general, îl fac mai ușor de folosit.

În ultimii ani, mai multe alte shell-uri au devenit populare. Cel mai notabil este Korn shell. Acesta este un produs comercial care înglobează cele mai bune caracteristici ale Bourne shell și C shell, plus multe facilități proprii. Korn shell este similar cu bash în multe privințe; ambele oferă numeroase funcții care le fac ușor de utilizat. Avantajul lui bash este că este gratuit.

# 2. Features of bash 

Caracteristici ale bash

Deși Bourne shell este încă cunoscut drept „shell-ul standard”, bash devine din ce în ce mai popular. Pe lângă compatibilitatea cu Bourne shell, bash include cele mai bune caracteristici ale C shell și Korn shell, precum și câteva avantaje proprii.

Funcțiile de editare a liniei de comandă sunt cele care tind să atragă cel mai mult utilizatorii. Cu acestea, este mult mai ușor să revii și să corectezi greșeli sau să modifici comenzi anterioare decât cu mecanismul de istoric al C shell — iar Bourne shell nu îți permite deloc acest lucru.

O altă caracteristică importantă a bash, destinată în special utilizatorilor interactivi, este job control. Așa cum explică Capitolul 8, job control îți oferă posibilitatea de a opri, porni și pune în pauză oricâte comenzi simultan. Această funcționalitate a fost preluată aproape identic din C shell.

Restul avantajelor importante ale bash sunt destinate în principal personalizatorilor de shell și programatorilor. Are numeroase opțiuni și variabile noi pentru personalizare, iar capacitățile sale de programare au fost extinse semnificativ pentru a include:definirea de funcții,mai multe structuri de control,aritmetică cu numere întregi,mecanisme avansate de I/O,și multe altele.

# 3. Getting bash 
Folosirea bash

Este posibil să folosești sau nu bash în acest moment. Administratorul sistemului probabil ți-a setat contul cu acel shell pe care îl consideră „standard”. S-ar putea chiar să nu fi fost conștient că există mai multe shell-uri disponibile.

Este totuși ușor să verifici ce shell folosești. Autentifică-te și tastează:

 ``` 
echo $SHELL
 ``` 

Răspunsul va conține sh, csh, ksh sau bash, corespunzătoare shell-urilor Bourne, C, Korn și bash. (Este posibil și să folosești un alt shell, cum ar fi tcsh.)

Dacă nu folosești bash și vrei să îl folosești, mai întâi verifică dacă există pe sistem. Tastează: 

```
bash
```
Dacă primești un prompt nou, cu informații urmate de un simbol dolar 

```
bash3 $
```

atunci totul este în regulă; 
tastează 

```
exit 
```

pentru a reveni la shell-ul tău obișnuit.

Dacă primești mesajul „not found”, este posibil ca sistemul tău să nu aibă instalat bash. Întreabă administratorul sau un utilizator experimentat; este posibil să existe o versiune de bash instalată într-un director care nu îți este accesibil. Dacă nu există deloc, consultă Capitolul 11 pentru a afla cum poți obține o versiune bash.
Odată ce știi că ai bash pe sistemul tău, îl poți porni din orice alt shell pe care îl folosești tastând `bash` așa cum am arătat mai sus. Totuși, este mult mai bine să îl instalezi ca login shell, adică shell-ul pe care îl primești automat de fiecare dată când te autentifici. Este posibil să poți face instalarea chiar tu. Iată instrucțiuni concepute să funcționeze pe cea mai largă varietate de sisteme UNIX. Dacă ceva nu funcționează (de ex., tastezi o comandă și primești mesajul „not found” sau ca răspuns apare o linie goală), va trebui să întrerupi procesul și să vorbești cu administratorul sistemului. Alternativ, consultă Capitolul 12, unde prezentăm o metodă mai puțin directă de a înlocui shell-ul tău actual.

Ai nevoie să afli unde se află bash pe sistemul tău, adică în ce director este instalat. Poți afla locația tastând:

```
whereis bash
```

(în special dacă folosești C shell). Dacă aceasta nu funcționează, încearcă:

```
whence bash
```

```
which bash
```

sau această comandă mai complexă:

```
grep bash /etc/passwd | awk -F: '{print $7}' | sort -u
```

Ar trebui să obții un rezultat de forma:/bin/bash sau /usr/local/bin/bash.
Pentru a instala bash ca login shell, tastează `chsh` bash-name unde bash-name este răspunsul pe care l-ai obținut din comanda `whereis` (sau oricare a funcționat). De exemplu:

```
% chsh /usr/local/bin/bash
```

Vei primi fie un mesaj de eroare care spune că shell-ul este invalid, fie vei fi întrebat de parolă.† Tastează parola, apoi deloghează-te și autentifică-te din nou pentru a începe să folosești bash.

# 4. Interactive Shell Use 

Utilizarea interactivă a shell-ului

Când folosești shell-ul în mod interactiv, participi la o sesiune de login care începe în momentul în care te autentifici și se încheie atunci când tastezi `exit` , `logout` sau apeși `CTRL-D`. În timpul unei sesiuni de login, tastezi linii de comandă în shell; acestea sunt linii de text care se termină cu tasta `RETURN` și pe care le introduci la terminalul sau stația ta de lucru.

În mod implicit, shell-ul îți afișează un prompt pentru fiecare comandă, constând într-un șir de informații urmat de un simbol dolar `$`. Totuși, după cum vei vedea în Capitolul 3, întregul prompt poate fi modificat.

# 5. Commands, Arguments, and Options 

Comenzi, argumente și opțiuni

Liniile de comandă din shell constau din unul sau mai multe cuvinte, care sunt separate între ele prin spații sau TAB-uri. Primul cuvânt de pe linie este comanda. Restul cuvintelor (dacă există) sunt argumente (numite și parametri) pentru acea comandă — adică nume ale lucrurilor asupra cărora comanda va acționa.

De exemplu, linia de comandă: lp myfile este alcătuită din comanda lp (care imprimă un fișier) și singurul argument myfile. Comanda lp tratează myfile ca fiind numele fișierului de tipărit. Argumentele sunt adesea nume de fișiere, dar nu neapărat: în linia de comandă: 

```
mail cam
```

programul mail tratează cam ca numele utilizatorului căruia i se va trimite un mesaj.

O opțiune este un tip special de argument care oferă comenzii informații specifice despre cum ar trebui să se comporte. De obicei, opțiunile constau dintr-o liniuță urmată de o literă; spunem „de obicei” deoarece aceasta este o convenție, nu o regulă strictă.

Linia:

```
lp -h myfile
```

conține opțiunea `-h` , care îi spune comenzii `lp` să nu tipărească pagina de antet („banner page”) înaintea fișierului propriu-zis.

Uneori, opțiunile au propriile lor argumente. De exemplu:

```
lp -d lp1 -h myfile
```

are două opțiuni și un argument. Prima opțiune este `-d lp1` , ceea ce înseamnă „Trimite ieșirea către imprimanta (destinația) numită `lp1` .” A doua opțiune și argumentul sunt aceleași ca în exemplul anterior.
