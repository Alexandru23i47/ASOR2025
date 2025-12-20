# 1.Afișarea unei Singure Linii Specifică dintr-un Fișier
Această comandă rezolvă problema extragerii rapide a unei linii specifice (de exemplu, linia a 10-a) dintr-un fișier mare:
```
bash
seq 15 | sed -n '10p'
```
În JSLinux:
```
10
```
Descrierea amănunțită a fiecărei componente:
- `seq 15` generează numerele de la 1 la 15, câte unul pe linie;
- `sed` invocă editorul de fluxuri;
- `-n`Opțiunea -n dezactivează comportamentul implicit al `sed` de a tipări fiecare linie procesată
- `10p` Adresa 10 specifică linia a zecea, iar comanda p (print) tipărește conținutul acelei linii.

Comanda fără `-n`: seq 15 | sed `10p` :
```
1
...
9
10  <- (Tipărită automat)
10  <- (Tipărită explicit de '10p')
11
...
15
```

# 2.Inversarea Ordinii Cuvintelor sau a Datelor
Această comandă rezolvă problema restructurării rapide a datelor, în special inversarea ordinii a două sau mai multe câmpuri de text pe o linie. Este utilă, de exemplu, pentru a inversa formatul "Nume Prenume" în "Prenume, Nume".
```
bash
echo "Andrei Liviu" | sed -E 's/([^ ]+) (.*)/\2, \1/'
```
În JSLinux: 
```
Liviu, Andrei
```
Descrierea amănunțită a fiecărei componente:
- `echo "..."` creează un text simplu de intrare;
- `sed` invocă editorul de fluxuri;
- `-E` este opțiunea Extended Regular Expressions ,ce permite utilizarea parantezelor `()` fără a fi nevoie de `\(` și `\)` , simplificând sintaxa.
- `s` este comanda de substituție
- `s/([^ ]+) (.+)/\2, \1/` este Expresie Regulată 
- `([^ ]+)` captează primul cuvânt din linia de la început, unde operatorul de poziționare `^` forțează potrivirea expresiei regulate să înceapă exact de la primul caracter al liniei;
- `_(spațiu gol) ` acesta separă cuvintele;
- `(.*)` este a doua subexpresie ce captează al doilea cuvânt("Liviu") și devine \2
- `\2` tipărește al doilea cuvânt;
- `\1` tipărește primul cuvânt.

# 3. Unirea liniilor consecutive
Această comandă rezolvă problema combinării a două linii consecutive într-o singură linie, separându-le printr-un caracter specific (de exemplu, o virgulă și un spațiu). Este utilă pentru reformata textul sau listele împărțite pe linii.
```
bash
printf 'Nume\nAdresă\nOraș\nCodPoștal' | sed 'N; s/\n/, /'
```
În JSLinux: 
```
Nume, Adresă
Oraș, CodPoștal
```
Descrierea amănunțită a fiecărei componente:
- `printf '...'` Creează 4 linii separate pentru demonstrație;
- `sed` invocă editorul de fluxuri;
- `N` comanda NEXT LINE  , adaugă o linie nouă urmat de următoarea linie de intrare la spațiul de model;
- `s/\n/, /` comanda de substituție, se execută pe spațiul de model, care acum conține două linii unite printr-un newline ascuns (Linia1\nLinia2).
- `/\n/` caută caracterul newline `\n` în spațiul de model
- `/, /` caracterul newline este înlocuit cu o virgulă urmată de un spațiu.


# 4.Numărarea Totală a Liniilor
Această comandă rezolvă problema determinării numărului total de linii dintr-un fișier.
```
bash
printf 'Linia 1\nLinia 2\nLinia 3' | sed -n '$='
```
În JSLinux:
```
3
```
Descrierea amănunțită a fiecărei componente:
- `printf '...'` creează  textul de intrare (3 linii) 
- `sed` invocă editorul de fluxuri;
- `-n` suprimă tipărirea implicită a conținutului liniilor, asigurând că este afișat doar numărul;
- `$` sed execută comanda următoare ` = ` doar atunci când ajunge la ultima linie din fișier;
- `=` tipărește numărul liniei curente;
- `$=` prin combinarea $ cu =, se tipărește numărul liniei curente exact când aceasta este ultima linie, oferind astfel numărul total de linii.


# 5.Extragerea Ultimelor Linii

Această comandă rezolvă problema extragerii unui număr specific de linii de la sfârșitul fișierului (de exemplu, ultimele 3 linii).
Această tehnică folosește adresa ! (negarea) și comanda d (Delete) pe liniile procesate.
```
bash
seq 10 | sed -n '1,7d; p'
```
În JSLinux:
```
8
9
10
```
Descrierea amănunțită a fiecărei componente:
- `seq 10` creează linii numerotate de la 1 la 10;
- `sed` invocă editorul de fluxuri;
- `-n` suprimă tipărirea implicită a conținutului liniilor;
- `1,7d` se aplică liniilor de la 1 la 7 (ignorând 8, 9, 10). Comanda d șterge acele linii, ciclul fiind repornit imediat.
- `p` această comandă este executată pentru toate liniile care NU au fost șterse anterior de 1,7d.

Scriptul șterge primele 7 linii. Ultimele 3 linii rămân în flux și sunt tipărite de comanda universală p (deoarece -n este activ).
