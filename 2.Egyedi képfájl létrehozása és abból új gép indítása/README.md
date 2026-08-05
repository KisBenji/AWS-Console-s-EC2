# Egyedi képfájl létrehozása és abból új gép indítása


Az egyedi képfájlhoz a meglévő EC2 instance kiválasztjuk vagy újat is létre tudunk hozni és abból konfigurálás után a következő úton érhetjük el:

`Actions → Image and templates → Create image`

<img width="1309" height="794" alt="Képernyőfotó 2026-07-24 - 22 37 05" src="https://github.com/user-attachments/assets/5fb315a4-aa93-4327-b49d-e7ae324bc3d3" />

Kötelező adatok megadása következik.
Image name : <mark>1stWebserverAMI</mark>


Az adatok megadása után a `Create image` kattintva létre jön az egyedi AMI (Amazon Machine Images) 
Pár perc kell a rendszernek amíg létrehozza az AMI-t. 

<img width="1308" height="798" alt="Képernyőfotó 2026-07-24 - 22 36 47" src="https://github.com/user-attachments/assets/bb4fe466-7053-4ecd-9244-94461a390a79" />

Az oldalsó menüsorban az AMIs kattintva látjuk a statust, amit megvárunk amíg elérhető - `available` lesz.

<img width="1305" height="799" alt="Képernyőfotó 2026-07-24 - 22 39 07" src="https://github.com/user-attachments/assets/5ba2ca53-0847-4428-b59b-0aa4083adca5" />

Amint rendelkezésre áll az elkészített AMI, kiválasztjuk és rákattintunk a → `Launch instance from AMI`
Itt meg kell adnunk az újonnan indítani kívánt szerver nevét és kötelező adatait.

Szerver név: <mark>1stWebserverAMI</mark>

<img width="1304" height="797" alt="Képernyőfotó 2026-07-24 - 22 40 05" src="https://github.com/user-attachments/assets/410a87b1-7dc9-4d61-8390-6515b567d869" />

További adatok megadásánál, mint az előző munkafolyamatban ki lehet választani a szerver típusát, ami a példa igényéhez igazítva maradt a <mark>t3.micro</mark> 

Kulcspár esetén a mentett korábban használt vagy újonnan generált kulcs megadását kiválasztjuk.

Subnet esetén az elérhetőségnél kiválasztunk egy másik zónát a korábbitól eltérően. Ennek oka a magas rendelkezésre állás 
`High Availability` illetve ha e két szerver mögé egy terheléselosztót teszünk akkor is a két zóna között tudja elosztani a forgalmat és így a túlterhelést kockázatát csökkentve. 

Security group esetén a meglévő beállítást kiválasztom, hogy az internet felől elérhető legyen. Itt megadható új beállítás is, igény szerint.

<img width="1308" height="796" alt="Képernyőfotó 2026-07-24 - 22 41 46" src="https://github.com/user-attachments/assets/5364aee2-a5ed-4c36-81fb-800479d069ff" />

Ha elkészültünk az adatok megadásával a `Launch instance`-ra kattintva létrehozhatjuk a képfájlból a gépünket, amelyet az Instance menüben látjuk, hogy rendelkezésre áll, amint elérte a status a 3/3-at. 

<img width="1306" height="801" alt="Képernyőfotó 2026-07-24 - 22 46 35" src="https://github.com/user-attachments/assets/d32ddf40-fba7-405f-97c5-73dc8e817e9b" />


