```6502
;PROGRAMUL 4
          lda #$07
          ldx #$0
          ldy #$03
memorare: sta $10,x
          inx
          dey
          bne memorare

;PROGRAMUL 5
        lda #$38
        sta $00
        and #$0f
        tay
        lda $00
        and #$f0
        beq mutare
calcul: sec
        inx
        sbc #$10
        beq mutare
        bne calcul
mutare: clc
        sta $00

;PROGRAMUL 7
define  numarul $7
define  cifrele $10
        lda # cifrele
        sta $00
        lda # numarul
        sta $01
calcul: dec $00
        eor $00
        beq final
        lda $01
        bne calcul
final:  ldx $01
        lda #$00
        sta $00
        sta $01

;PROGRAMUL 8
define numarul1 $ae
define numarul2 $ae
       lda      #numarul1
       sta      $00
       lda      #numarul2
       sta      $01
       ldx      #$0
       stx      $02
       lda      $00
       cmp      $01
       bne      final
       inx
final: stx      $02

;PROGRAMUL 9
define numarul1 $ae
define numarul2 $f
       lda      #numarul1
       sta      $00
       lda      #numarul2
       sta      $01
       cmp      $00
       bcs      final
       ldx      $00
       sta      $00
       stx      $01
final: brk

PROGRAMUL 10
define          comparat   $ae
define          comparator $f
                lda        #comparat
                cmp        #comparator
                bcs        maimaresauegal
                sta        $00
                jmp        final
maimaresauegal: bne        maimare
                sta        $01
                jmp        final
maimare:        sta        $02
final:          brk

PROGRAMUL 11
lda # % 01 11 11 00
           sta $00
           lda # % 01 10 01 11
           sta $01
           lda #$00
           ldx #$08
           ldy $01
bitul_urm: lsr $01
           bcc aliniez
           clc
           adc $00
aliniez:   lsr a
           ror $02
           dex
           bne bitul_urm
           sta $03
           sty $01
```
