# Praktikum 13 aruanne

Selles praktikumis õppisime skriptimist Windowsis

```
$outputFile = "TestArvutiInfo.txt"

function KirjutaFaili {
    param([string]$data)
    Add-Content -Path $outputFile -Value $data
}

# 1
$masinaNimi = (Get-WmiObject -Class Win32_ComputerSystem).Name
$psVersioon = $PSVersionTable.PSVersion
$windowsVersioon = (Get-WmiObject -Class Win32_OperatingSystem).Caption
KirjutaFaili "Masina nimi: $masinaNimi"
KirjutaFaili "PowerShelli versioon: $psVersioon"
KirjutaFaili "Windowsi versioon: $windowsVersioon"
KirjutaFaili ""

# 2
$netConfig = Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled = 'True'"
$ip = $netConfig.IPAddress
$mask = $netConfig.IPSubnet
$gateway = $netConfig.DefaultIPGateway
$dhcp = $netConfig.DHCPEnabled
$mac = $netConfig.MACAddress
KirjutaFaili "Võrgu konfiguratsioon:"
KirjutaFaili "IP: $ip"
KirjutaFaili "Mask: $mask"
KirjutaFaili "Gateway: $gateway"
KirjutaFaili "DHCP: $dhcp"
KirjutaFaili "MAC: $mac"
KirjutaFaili ""

# 3
$protsessor = (Get-WmiObject -Class Win32_Processor).Description
$ram = [math]::round((Get-WmiObject -Class Win32_ComputerSystem).TotalPhysicalMemory / 1GB, 2)
KirjutaFaili "Protsessor: $protsessor"
KirjutaFaili "RAM: $ram GB"
KirjutaFaili ""

# 4
$video = Get-WmiObject -Class Win32_VideoController
$videoNimi = $video.Name
$videoVersioon = $video.DriverVersion
$videoKuupaev = $video.DriverDate
$lahutus = ($video.CurrentHorizontalResolution).ToString() + "x" + $video.CurrentVerticalResolution
KirjutaFaili "Graafikakaart:"
KirjutaFaili "Nimi: $videoNimi"
KirjutaFaili "Versioon: $videoVersioon"
KirjutaFaili "Kuupäev: $videoKuupaev"
KirjutaFaili "Lahutus: $lahutus"
KirjutaFaili ""

# 5
$diskid = Get-WmiObject -Class Win32_LogicalDisk -Filter "DriveType = 3" # Kõvakettad
foreach ($disk in $diskid) {
    $ketas = $disk.DeviceID
    $mahtGB = [math]::round($disk.Size / 1GB, 2)
    $vabaGB = [math]::round($disk.FreeSpace / 1GB, 2)
    KirjutaFaili "Ketas ${ketas}:"
    KirjutaFaili "Maht: $mahtGB GB"
    KirjutaFaili "Vaba: $vabaGB GB"
}
KirjutaFaili ""

# 6
$video = Get-WmiObject -Class Win32_VideoController
$videoNimi = $video.Name
$videoVersioon = $video.DriverVersion
$videoKuupaev = $video.DriverDate

# Kui CurrentHorizontalResolution ja CurrentVerticalResolution on arvud, siis veendu, et need on enne liitmist õigesti tekstiks konverteeritud
$lahutus = ($video.CurrentHorizontalResolution).ToString() + "x" + $video.CurrentVerticalResolution

KirjutaFaili "Graafikakaart:"
KirjutaFaili "Nimi: $videoNimi"
KirjutaFaili "Versioon: $videoVersioon"
KirjutaFaili "Kuupäev: $videoKuupaev"
KirjutaFaili "Lahutus: $lahutus"
KirjutaFaili ""



# 7
$kasutajad = Get-WmiObject -Class Win32_UserAccount
foreach ($kasutaja in $kasutajad) {
    $kasutajaNimi = $kasutaja.Name
    $kasutajaKirjeldus = $kasutaja.Description
    $lokaalne = $kasutaja.LocalAccount
    $keelatud = $kasutaja.Disabled
    KirjutaFaili "Kasutaja: $kasutajaNimi"
    KirjutaFaili "Kirjeldus: $kasutajaKirjeldus"
    KirjutaFaili "Lokaalne: $lokaalne"
    KirjutaFaili "Keelatud: $keelatud"
}
KirjutaFaili ""

# 8
$protsessideArv = (Get-Process).Count
KirjutaFaili "Protsesside arv: $protsessideArv"
KirjutaFaili ""

# 9
try{
$protsessid = Get-Process | Sort-Object StartTime | Select-Object -Last 10 Name, Id, StartTime
foreach ($protsess in $protsessid) {
    KirjutaFaili "Protsess: $($protsess.Name), PID: $($protsess.Id), Algusaeg: $($protsess.StartTime)"
}
KirjutaFaili ""
}
catch {
    Write-Host "error"
}

# 10
$kuupaev = Get-Date
KirjutaFaili "Kuupäev ja kellaaeg: $kuupaev"
KirjutaFaili ""

```
