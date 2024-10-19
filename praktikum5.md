# Praktikum 5 aruanne 

Selles praktikumis õppisin linuxi failiõigusi.

<br>
Ülesanne 5.1

a) lugemiseks -r--------
b) kustutamiseks -r--------

<br>
Ülesanne 5.2

chmod a=x Kaust3/script.sh eemaldab lugemisõiguse ja lugemisõigus on vajalik käivitamiseks

<br>
Ülesanne 5.3

Et lihtsustada õiguste jagamisi. Näiteks kui user loob uue faili, antakse juurdepääs sellelel failile useri nimelisele grupile

<br>
Ülesanne 5.4
<br>
<img width="491" alt="OS24_5.4" src="https://github.com/user-attachments/assets/6ae5be68-d097-4ef2-9189-be179b46eb5d">
<br>
<br>
Ülesanne 5.5
<br>
<img width="491" alt="OS24_5.5" src="https://github.com/user-attachments/assets/ebffd3f8-d3c1-4063-a148-e16c9c868436">

Setuid õigused võimaldavad teistel kasutajatel täita ülesandeid teise kasutaja õigustes

<br>
Ülesanne 5.6

Jah, kui seda ei kasutata õigesti ja tekivad turvaaugud. Üks kasutaja võib teise kasutaja õigustes omandada kõrgendatud ligipääsu ja teha pahatahtlikke asju.

<br>
Ülesanne 5.7

peeter
root
opetaja

<br>
Ülesanne 5.8
<br>
<img width="491" alt="OS24_5.8" src="https://github.com/user-attachments/assets/085b5c61-8f78-43eb-a2a3-3134df626d76">
<br>
<br>
Ülesanne 5.9

Mitte keegi ei saa chattr +i-parameetriga faili sisu modifitseerida.

Et kustutada tuleb sisesestada
$sudo chattr -i testfail-2
$rm testfail-2
