# Praktikum 12 aruanne

Selles praktikumis õppisime skriptimist linuxis

Ülesanne 3
```
#!/bin/sh

printf "Sisesta enda nimi: "
read nimi

printf "Sisesta enda eriala: "
read eriala

printf "Sisesta matriklinumber: "
read number

echo "\nNimi: $nimi"
echo "Eriala: $eriala"
echo "Matriklinumber: $number"
```

<img width="491" alt="ül3 väljund" src="https://github.com/user-attachments/assets/116b01b8-960e-4542-bea9-7b1665ba231c">
<br>
<br>

Ülesanne 4
```
#!/bin/bash

# Saan kasutajalt lainedite sisendid

laiend1=$1
laiend2=$2

# Muudan vastavad extensionid ära

failid=$(ls)

for fail in $failid
do
        if [ "${fail##*.}" = $laiend1 ]
        then
                uus_fail=$(echo $fail | sed -e s/".${laiend1}"/".${laiend2}"/g)
                mv $fail $uus_fail
        fi
done
```

<img width="491" alt="ül4 väljund" src="https://github.com/user-attachments/assets/0e335827-8a20-4ce5-bc88-6ae38b4eb998">
<br>
<br>

Ülesanne 5
```
#!/bin/bash

protsess=$1

IFS=$'\n'
for line in $(ps -A)
do
        name=$( echo $line | tr -s ' ' | cut -d ' ' -f5)

        if [ $protsess = $name ]
        then
                pid=$( echo $line | tr -s ' ' | cut -d ' ' -f2)
                echo "Name: $name"
                echo "PID: $pid"
        fi
done
```

<img width="491" alt="ül5 väljund" src="https://github.com/user-attachments/assets/16bda2f4-c9eb-4d26-8c3c-d66858c30fa5">
<br>
<br>

Ülesanne 6
```
#!/bin/bash

aste () {
        if [ $2 = 0 ]
        then
                echo 1
        else
                echo $(($1 * $(aste $1 $(($2 - 1)))))
        fi
}

echo "9 astmel 5 on: $(aste 9 5)"
```

<img width="491" alt="ül6 väljund" src="https://github.com/user-attachments/assets/00982d15-4637-445b-81e6-2c89dcf07a1d">
<br>
<br>

Ülesanne 7

<br>
<img width="491" alt="ül7 pilt 1" src="https://github.com/user-attachments/assets/122ece3e-acf0-40bb-92e0-9fba07e8d8d4">
<br>
<img width="491" alt="ül7 pilt 2" src="https://github.com/user-attachments/assets/4005e01b-fb80-4004-ab8f-07a49be302cf">
<br>
<img width="491" alt="ül7 pilt 3" src="https://github.com/user-attachments/assets/d4769615-a5d7-4ccf-b1fa-af38f91d40fb">
<br>
