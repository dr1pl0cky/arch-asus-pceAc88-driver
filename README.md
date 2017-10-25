# arch-asus-pceAc88-driver



download the firmware provided by ASUS

extract the squash image with p7zip: 7z X RT-AC88U_3.0.0.4_380_3341-g25420f5.trx

then you have to extract the firmware: dd if=lib/modules/2.6.36.4brcmarm/kernel/drivers/net/dhd/dhd.ko skip=1269516 ibs=1 count=935317 of=brcmfmac4366c-pcie.bin

resulted firmware should match following sha1sum: 9e5af3ce7ce9c358c773873734ffa5cdf1641de5

copy the firmware4 to the proper directory and reload the driver: sudo cp -v brcmfmac4366c-pcie.bin /usr/lib/firmware/brcm && 
sudo modprobe brcmfmac

Extraction log:

$ sha1sum *trx
4a8c36a920f7dba5d45c490503616085b70cf3e7  RT-AC88U_3.0.0.4_380_3341-g25420f5.trx

$ 7z X RT-AC88U_3.0.0.4_380_3341-g25420f5.trx

7-Zip [64] 16.02 : Copyright (c) 1999-2016 Igor Pavlov : 2016-05-21
p7zip Version 16.02 (locale=de_DE.utf8,Utf16=on,HugeFiles=on,64 bits,4 CPUs AMD Phenom(tm) 9650 Quad-Core Processor (100F23),ASM)

Scanning the drive for archives:
1 file, 42504192 bytes (41 MiB)

Extracting archive: RT-AC88U_3.0.0.4_380_3341-g25420f5.trx
         
WARNINGS:
There are data after the end of archive

--
Path = RT-AC88U_3.0.0.4_380_3341-g25420f5.trx
Type = SquashFS
WARNINGS:
There are data after the end of archive
Offset = 1784292
Physical Size = 40718336
Tail Size = 1564
Headers Size = 52657
File System = SquashFS 4.0
Method = XZ
Cluster Size = 131072
Big-endian = -
Created = 2016-05-18 08:56:36
Characteristics = DUPLICATES_REMOVED EXPORTABLE

Everything is Ok                                                    

Archives with Warnings: 1

Warnings: 1
Folders: 107
Files: 2428
Size:       91233560
Compressed: 42504192

 $ ls
   RT-AC88U_3.0.0.4_380_3341-g25420f5.trx 

$ dd if=lib/modules/2.6.36.4brcmarm/kernel/drivers/net/dhd/dhd.ko skip=1269516 ibs=1 count=935317 of=brcmfmac4366c-pcie.bin

$ sha1sum brcmfmac4366c-pcie.bin
9e5af3ce7ce9c358c773873734ffa5cdf1641de5  brcmfmac4366c-pcie.bin

$ sudo cp -v brcmfmac4366c-pcie.bin /usr/lib/firmware/brcm
'brcmfmac4366c-pcie.bin' -> '/usr/lib/firmware/brcm/brcmfmac4366c-pcie.bin'

$sudo modprobe brcmfmac
