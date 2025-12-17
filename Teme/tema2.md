# Tema 2:

## Studiu

- Din 
  [manualul oficial](https://www.gnu.org/software/sed/manual/sed.html) 
  de 
  [sed](https://www.gnu.org/software/sed/),
  documentați-vă în privința acestui 
  **editor de fluxuri** (în limba engleză, *stream editor*).
- Testați comenzile studiate folosind emulatorul de Linux al
  dlui. Fabrice Bellard:
  [bit.ly/alpine_jslinux](https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192).
- Familiarizați-vă cu 
  [expresiile regulate](https://www.gnu.org/software/sed/manual/sed.html#sed-regular-expressions)
  înțelese de `sed`.

## Compoziție

Găsiți **cinci** utilizări în 
[linie de comandă](https://en.wikipedia.org/wiki/Command-line_interface) 
ale editorului `sed`. Construiți:

- enunțul utilizării (ce **problemă** se 
  rezolvă prin respectiva utilizare șamd.)
- forma completă, verificată în emulator, 
  a comenzii `sed`
- descrierea amănunțită a fiecărei 
  etape/componente/pas a(l) comenzii respective.

> Un exemplu (de problemă, **nu** de tratare!):
>
> Pentru a afla **momentul curent** de timp, 
> trebuie *ținut minte* 😟 
> un dublet de opțiuni ale comenzii `date` din 
> *shell*-ul `bash`:
>
> ```bash
> bash
> date +%R:%S
> ```
>
> Dacă am uitat opțiunile, atunci putem folosi 
> următoarea comandă
> [pe un rând](https://en.wikipedia.org/wiki/One-liner_program):
> 
> ```bash
> date | tr ' ' '\n' | sed -n '5p'
> ```
> Aici,
>
> - `date` nu necesită 
>   [opțiuni](https://www.gnu.org/software/coreutils/manual/html_node/date-invocation.html)
>   memorate
> - `tr` [traduce](https://www.gnu.org/software/coreutils/manual/html_node/tr-invocation.html) 
>   *spațiile goale* în *treceri* pe linia următoare
> - `sed` tipărește în terminal *numai* linia a cincea 
>   a rezultatului.

## Editare

În proiectul dvs. ASOR2025 (**fork**-ul din 
contul dvs. al **repository**-ului meu cu 
același nume), de pe platforma GitHub:

- construiți un fișier intitulat `tema2.md`
  în directorul `Activități/nume.prenume`
- editați [compoziția](#compoziție)
  realizată la cerința anterioară în **Markdown**
- introduceți codul-sursă Markdown în fișierul 
  `tema2.md`
- realizați **commit**-ul rezultatului în proiect
- faceți un **PR** către proiectul meu ASOR2025.

## Termen-limită

Pentru ca tema să fie luată în considerare,
cererea (PR-ul) va trebui realizată până în 
data de `17.12.2025` la orele `23:59:59`.
