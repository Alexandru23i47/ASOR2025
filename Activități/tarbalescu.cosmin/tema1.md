## Istoria shell-urilor UNIX
Independen&#539;a shell-ului fat&#259; de sistemul de operare windows propriu-zis a adus la dezvoltarea de zeci de shell-uri de-a lungul istoriei UNIX, de&#537;i doar c&#226;teva au ajuns sa fie utilizate pe scara larg&#259;.
Primul shell important a fost shell-ul Bourne (numit după inventatorul său, Steven Bourne); acesta a fost inclus în prima versiune populară de UNIX, Versiunea 7, începând din 1979. Shell-ul Bourne este cunoscut în sistem sub numele de sh. Deși UNIX a trecut prin foarte multe schimbări, shell-ul Bourne este încă popular și practic neschimbat. Mai multe utilitare UNIX și funcții de administrare depind de el.

Primul shell alternativ utilizat pe scară largă a fost shell-ul C, sau *csh*. Acesta a fost scris de Bill Joy la Universitatea din California, Berkeley, ca parte a distribuției BSD (Berkeley Software Distribution) a UNIX, apărută la câțiva ani după Versiunea 7.

Shell-ul C își ia numele de la asemănarea comenzilor sale cu instrucțiunile limbajului de programare C, ceea ce îl face mai ușor de învățat pentru programatorii care folosesc sisteme UNIX. Acesta suportă o serie de funcționalități ale sistemului de operare (de ex. controlul job-urilor; vezi Capitolul 8) care erau unice pentru BSD UNIX, dar care între timp au migrat în majoritatea versiunilor moderne. De asemenea, are câteva caracteristici importante (de ex. alias-uri; vezi Capitolul 3) care îl fac mai ușor de utilizat în general.

În ultimii ani, o serie de alte shell-uri au devenit populare. Cel mai remarcabil dintre acestea este shell-ul Korn. Acest shell este un produs comercial care încorporează cele mai bune caracteristici ale shell-urilor Bourne și C, plus multe funcții proprii.*
Shell-ul Korn este similar cu *bash* în majoritatea privințelor; ambele au o abundență de funcții care le fac ușor de utilizat. Avantajul lui *bash* este că este gratuit. Pentru informații suplimentare despre shell-ul Korn, vezi Anexa A.

## Caracteristici ale bash

Deși shell-ul Bourne este încă cunoscut ca „shell-ul standard”, *bash* devine din ce în ce mai popular. Pe lângă compatibilitatea sa cu shell-ul Bourne, acesta include cele mai bune caracteristici ale shell-urilor C și Korn, precum și câteva avantaje proprii.

Modurile de editare a liniei de comandă din bash sunt caracteristicile care tind să atragă oamenii în primul rând. Cu editarea liniei de comandă, este mult mai ușor să te întorci și să corectezi greșelile sau să modifici comenzile anterioare decât cu mecanismul de istoric al shell-ului C — iar shell-ul Bourne nu îți permite deloc acest lucru.

Cealaltă caracteristică majoră a lui *bash*, destinată în principal utilizatorilor interactivi, este controlul job-urilor. Așa cum explică Capitolul 8, controlul job-urilor îți oferă posibilitatea de a opri, porni și întrerupe orice număr de comenzi în același timp. Această funcție a fost împrumutată aproape identic din shell-ul C.

Restul avantajelor importante ale lui *bash* sunt destinate în principal celor care personalizează shell-ul și programatorilor. Acesta are multe opțiuni și variabile noi pentru personalizare, iar caracteristicile sale de programare au fost extinse semnificativ pentru a include definirea de funcții, mai multe structuri de control, aritmetică pe numere întregi, control I/O avansat și multe altele.


## Obținerea shell-ului bash

Este posibil să folosești sau să nu folosești *bash* chiar acum. Administratorul tău de sistem probabil ți-a configurat contul cu shell-ul pe care îl folosește el ca „standard” pe sistem. S-ar putea nici măcar să nu fi fost conștient că există mai multe shell-uri disponibile.

Totuși, este ușor să determini ce shell folosești. Conectează-te la sistem și tastează `echo $SHELL` la prompt. Vei vedea un răspuns care conține **sh**, **csh**, **ksh** sau **bash**; acestea reprezintă shell-urile Bourne, C, Korn și bash, respectiv. (Există și șansa să folosești un alt shell, cum ar fi **tcsh**.)

Dacă nu folosești bash și vrei să îl folosești, trebuie mai întâi să vezi dacă există pe sistemul tău. Tastează pur și simplu `bash`. Dacă obții un prompt nou care conține ceva informații urmate de un semn dolar (de ex., bash3 $), atunci totul este în regulă; tastează `exit` pentru a te întoarce la shell-ul tău normal.

Dacă primești un mesaj de tipul „**not found**”, este posibil ca sistemul tău să nu îl aibă. Întreabă administratorul de sistem sau un alt utilizator avansat; există șansa ca o anumită versiune de bash să fie instalată într-un loc (director) care nu este accesibil în mod normal pentru tine. Dacă nu, citește Capitolul 11 pentru a afla cum poți obține o versiune de bash.

Odată ce știi că ai bash pe sistemul tău, îl poți apela din orice alt shell ai folosi tastând `bash` ca mai sus. Totuși, este mult mai bine să îl setezi ca *login shell*, adică shell-ul pe care îl primești automat de fiecare dată când te conectezi. Este posibil să poți face instalarea singur. Iată instrucțiuni concepute pentru a funcționa pe cea mai largă varietate de sisteme UNIX. Dacă ceva nu funcționează (de ex., tastezi o comandă și primești un mesaj „not found” sau o linie goală ca răspuns), va trebui să întrerupi procesul și să îți consulți administratorul de sistem. Alternativ, consultă Capitolul 12, unde prezentăm o metodă mai puțin directă de a înlocui shell-ul tău curent.

Trebuie să afli unde se află **bash** pe sistemul tău, adică în ce director este instalat. Ai putea găsi locația tastând `whereis bash` (mai ales dacă folosești shell-ul C); dacă acest lucru nu funcționează, încearcă `whence bash`, `which bash` sau această comandă complexă:*
```bash
grep bash /etc/passwd | awk -F: '{print $7}' | sort -u
```

Ar trebui să vezi un răspuns care arată ca **/bin/bash** sau **/usr/local/bin/bash**.
Pentru a instala bash ca shell de login, tastează `chsh bash-name`, unde *bash-name* este răspunsul pe care l-ai obținut de la comanda `whereis` (sau orice altă comandă care a funcționat). De exemplu:
```bash
% chsh /usr/local/bin/bash
```
Vei primi fie un mesaj de eroare care spune că shell-ul este invalid, fie ți se va cere parola.† Tastează parola, apoi deloghează-te și loghează-te din nou pentru a începe să folosești *bash*.


## Utilizarea interactivă a shell-ului
Atunci când folosești shell-ul în mod interactiv, intri într-o sesiune de *login* care începe în momentul în care te conectezi și se încheie când tastezi `exit` sau `logout` sau când apeși **CTRL-D**.‡ În timpul unei sesiuni de login, tastezi linii de comandă pentru shell; acestea sunt linii de text care se termină cu **RETURN** și pe care le introduci în terminalul sau stația ta de lucru.

În mod implicit, shell-ul îți afișează un prompt pentru fiecare comandă, constând într-un șir de informații urmat de un semn dolar, deși, așa cum vei vedea în Capitolul 3, întregul prompt poate fi modificat.


## Comenzi, Argumente și Opțiuni

Liniile de comandă shell constau dintr-unul sau mai multe cuvinte, care sunt separate pe o linie de comandă prin spații sau TAB-uri. Primul cuvânt de pe linie este *comanda*. Restul (dacă există) sunt *argumente* (numite și *parametri*) ale comenzii, care sunt nume de lucruri asupra cărora va acționa comanda.

De exemplu, linia de comandă `lp myfile` constă din comanda *lp* (tipărire fișier) și argumentul unic **myfile**. *lp* tratează **myfile** ca numele unui fișier de tipărit. Argumentele sunt adesea nume de fișiere, dar nu neapărat: în linia de comandă `mail cam`, programul de mail tratează **cam** ca numele de utilizator către care va fi trimis un mesaj.

O *opțiune* este un tip special de argument care oferă comenzii informații specifice despre ceea ce ar trebui să facă. Opțiunile constau de obicei dintr-o cratimă urmată de o literă; spunem „de obicei” deoarece aceasta este o convenție și nu o regulă strictă. Comanda `lp -h myfile` conține opțiunea **-h**, care îi spune lui *lp* să nu imprime „pagina banner” înainte de a imprima fișierul.

Uneori, opțiunile au propriile argumente. De exemplu, `lp -d lp1 -h myfile` are două opțiuni și un argument. Prima opțiune este **-d lp1**, ceea ce înseamnă „*Trimiteți ieșirea către imprimanta (destinația) numită **lp1***”. A doua opțiune și argumentul sunt aceleași ca în exemplul anterior.

