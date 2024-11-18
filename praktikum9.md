# Praktikum 9 aruanne

Selles praktikumis õppisime arvuti protsesse ja resursside haldust

<table border="1">
  <thead>
    <tr>
      <th>Küsimus</th>
      <th>Linux</th>
      <th>Windows</th>
      <th>Linuxis kasutatud käsklus</th>
      <th>Windowsis kasutatud tööriist</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Mitu protsessi kokku arvutis käib?</td>
      <td>209</td>
      <td>237</td>
      <td>ps -aux | wc -l</td>
      <td>Task Manager -> Jõudlus</td>
    </tr>
    <tr>
      <td>Milline on kõige esimesena käivitatud protsess?</td>
      <td>/sbin/init splash</td>
      <td>smss.exe</td>
      <td>ps axo pid,cmd,comm,etime</td>
      <td>Process Explorer -> Start Time</td>
    </tr>
    <tr>
      <td>Milliste kasutajate protsesse arvutis käib?</td>
      <td>avahi, colord, jurgen, kernoops, message+, polkitd, root, rtkit, systemd+, USER</td>
      <td>koosapoj, SYSTEM, NETWORK SERVICE, LOCAL SERVICE, DWM-1</td>
      <td>ps aux | awk '{print $1}' | sort | uniq</td>
      <td>Task Manager > Users</td>
    </tr>
    <tr>
      <td>Kui kaua on arvuti järjest töötanud</td>
      <td>7 minutit</td>
      <td>7:21:27:42</td>
      <td>uptime -p</td>
      <td>Task Manager > Performance  > CPU</td>
    </tr>
    <tr>
      <td>Milline protsess käivitati kõige hiljem</td>
      <td>[kworker/0:1H-kblockd]</td>
      <td>procexp.exe</td>
      <td>ps axo pid,etime,cmd</td>
      <td>Process Explorer -> Start Time</td>
    </tr>
    <tr>
      <td>Milline on kõige rohkem protsessoriaega võttev protsess ja kui mitu protsenti protsessoriajast ta tarbib</td>
      <td>gnome-shell</td>
      <td>Google Chrome 3.1%</td>
      <td>ps -eo pid,pcpu,comm --sort=-pcpu</td>
      <td>Task Manager -> Processes -> CPU</td>
    </tr>
    <tr>
      <td>Milline on kõige rohkem virtuaalmälu (aadressiruumi, commit, Virtual Size) võttev protsess</td>
      <td>gnome-shell</td>
      <td>SearchHost.exe</td>
      <td>ps -eo pid,vsz,comm --sort=-vsz | head -n 1</td>
      <td>Task Manager -> Details -> Commit size</td>
    </tr>
    <tr>
      <td>Milline on kõige rohkem füüsilist mälu (working set) võttev protsess?</td>
      <td>gnome-shell</td>
      <td>Google Chrome</td>
      <td>ps -eo pid,rss,comm --sort=-rss</td>
      <td>Task Manager -> Details -> Memory</td>
    </tr>
    <tr>
      <td>Kui palju füüsilisest mälust (Physical Memory) on vaba ja kui palju hõivatud?</td>
      <td>hõivatud 1.4GB, saadaval 1.4GB</td>
      <td>56% kasutuses</td>
      <td>free -h</td>
      <td>Task Manager -> Processes -> Memory</td>
    </tr>
    <tr>
      <td>Kui palju on põhikettal (C:, /) vaba ruumi mahult (GB) ja protsentuaalselt?</td>
      <td>kasutusel 11GB ja 60%</td>
      <td>237 GB ja 57% on vaba</td>
      <td>df -h /</td>
      <td>File Explorer -> This PC</td>
    </tr>
    <tr>
      <td>Milline on kõige suurem arvutis olev fail ja kõige rohkem andmemahtu hõivav kaust (arvesse võta ka alamkaustade mahtu, ja jätta juurkaust / või C: välja)?</td>
      <td>suurim fail: /swap.img. Kaust: /usr</td>
      <td>Suurim kaust Users ja suurim fail tava.vhdx</td>
      <td>fail: find / -type f -exec ls -sh {} + | sort -rh | head -n 1. Kaust: du -h / --max-depth=1 | sort -rh | head -n 2</td>
      <td>WinDirStat</td>
    </tr>
    <tr>
      <td>Võrrelge terminali käskude: sha1sum /dev/zero | sha1sum /dev/zero ja sha1sum /dev/urandom | sha1sum /dev/urandom protsessori kasutust.</td>
      <td>sha1sum /dev/urandom | sha1sum /dev/urandom käsuga kulub CPU alamtegevusele sy kõige rohkem aega. sha1sum /dev/zero | sha1sum /dev/zero käsule kulub CPU alamtegevusele si kõige rohkem aega.</td>
      <td></td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>Milline protsess kõige rohkem salvestusseadmele kirjutab?</td>
      <td></td>
      <td>System</td>
      <td></td>
      <td>Resource Monitor > Disk -> Write</td>
    </tr>
    <tr>
      <td>Millisesse faili eelmise küsimuse protsess kõige rohkem kirjutab?</td>
      <td></td>
      <td>C:\Windows\System32\LogFiles\WMI\WifiDriverIHVSession.etl.004</td>
      <td></td>
      <td>Resource Monitor > Disk -> file</td>
    </tr>
    <tr>
      <td>Milline protsess kõige rohkem salvestusseadmelt loeb?</td>
      <td></td>
      <td>chrome.exe</td>
      <td></td>
      <td>Resource Monitor > Disk -> read</td>
    </tr>
    <tr>
      <td>Millisest failist eelmise küsimuse protsess kõige rohkem loeb?</td>
      <td></td>
      <td>C:\Windows\ServiceProfiles\LocalService\AppData\Local\FontCache\~FontCache-S-1-12-1-2112585780-1181321052-4011372951-300675797a7.dat</td>
      <td></td>
      <td>Resource Monitor > Disk -> file</td>
    </tr>
    <tr>
      <td>Millise protsessi poolt tekitatud võrguliiklus on suurima mahuga?</td>
      <td></td>
      <td>chrome.exe tekitatud võrguliiklus on suurima mahuga. Kohalik iP 192.168.1.130, kohalik port 443. Teise poole IP aadress 157.240.205.55, teise poole port 443. Latens 52. Kogumaht 163874.</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>Sõber kurdab, et tema arvuti on oluliselt aeglasemaks muutunud.</td>
      <td></td>
      <td>Ava task manager. Vaata milline programm võtab kõige rohkem CPUd ja milline mälu kõige rohkem. Võimalusel sulge need programmid mille rida on punanes juba, see tähendab et liiga palju võtab. Vajuta task manageris performance ja vaata et CPU ei oleks pidevalt 100%. Kui on siis miski tarbib seda liialt palju.</td>
      <td></td>
      <td></td>
    </tr>
  </tbody>
</table>

<br>

Ülesanne 12
<br>
<img width="491" alt="sha1sum /dev/urandom" src="https://github.com/user-attachments/assets/e87ceace-e62d-4a6f-9a34-8ad59b1c18b2">
<br>
<img width="491" alt="sha1sum /dev/zero" src="https://github.com/user-attachments/assets/2bc1898a-e955-4691-b702-bd3f7f9d7cd2">
<br>

Ülesanne 14
<br>
<img width="491" alt="suurim võrguliiklus" src="https://github.com/user-attachments/assets/61ab0230-8db5-4685-ac55-8243e6be39f3">
