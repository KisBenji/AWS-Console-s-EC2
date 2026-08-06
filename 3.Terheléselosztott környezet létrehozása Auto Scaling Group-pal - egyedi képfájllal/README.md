# Terheléselosztott környezet létrehozása Auto Scaling Group-pal - egyedi képfájllal

Az előző munkafolyamatban leírtak szerint képfájlból dolgozva egy AMI-t készítünk.

Ennek a neve: <mark>3.feladat</mark>

<img width="1310" height="800" alt="Képernyőfotó 2026-07-24 - 22 48 20" src="https://github.com/user-attachments/assets/8df514a9-92df-4189-aa84-6e2668d9f6af" />

Amint elkészültünk az AMI-val az `EC2 → Launch Templates → Create launch template` soron tudjuk indítani a mintát és konfigurálását. 

Ennek a neve: <mark>1stTamplate</mark>

<img width="1303" height="793" alt="Képernyőfotó 2026-07-24 - 22 52 53" src="https://github.com/user-attachments/assets/0a6a95f4-8fd5-4509-a549-8bf1736b3038" />

Ezután kiválaszthatjuk az előbb elkészített AMI-t - <mark>3.feladat</mark>

<img width="1306" height="801" alt="Képernyőfotó 2026-07-24 - 22 53 15" src="https://github.com/user-attachments/assets/7b79c9ef-d8d5-4e8c-8f8b-420d7762fb60" />

Instance típusa szintén a <mark>t3.micro</mark>

Security beállatások a korábban generált beállítást használom, hogy az internet felől elérhető legyen.

Key pair <mark>kulcs-2026</mark>

<img width="1300" height="801" alt="Képernyőfotó 2026-07-24 - 22 53 50" src="https://github.com/user-attachments/assets/e629738b-4296-4a41-8f31-7b2fab44aa24" />

<img width="1303" height="794" alt="Képernyőfotó 2026-07-24 - 22 54 16" src="https://github.com/user-attachments/assets/b07dc641-1590-495c-9fcd-23e5553f66eb" />

A megadot adatok után már rá is kattinthatunk a `Create launch template`

<img width="1309" height="805" alt="Képernyőfotó 2026-07-24 - 22 54 47" src="https://github.com/user-attachments/assets/eae03f38-418c-4b0f-80b7-533fa7036b9f" />

Ezután célcsoportot hozunk létre a `EC2 → Target Groups → Create target group`, hogy a terheléselosztó később tudja melyik szerverre irányítsa a forgalmat.

Név: <mark>1stTG</mark>

Instance opciót választottam, hogy az ASG tudja kezelni a szervereket. 

<img width="1308" height="805" alt="Képernyőfotó 2026-07-24 - 22 55 19" src="https://github.com/user-attachments/assets/eaf5c104-0ccb-4128-93df-e9d0376d69d2" />

Health check beállítása. Itt az alapbeállítást használtam, de konfigurálni lehet, hogy hány másodpercenként küldjön kérést a szerverre. 
<img width="1307" height="797" alt="Képernyőfotó 2026-07-24 - 22 56 01" src="https://github.com/user-attachments/assets/45fac1af-8db3-471f-9ac0-ac4b84a74930" />

Az adatok megadása után létre is jön az első célcsoportunk.

<img width="1305" height="801" alt="Képernyőfotó 2026-07-24 - 22 57 35" src="https://github.com/user-attachments/assets/85257a44-bf00-4a9b-9ba8-6fd16a959ad7" />

A következő lépésben létre kell hozni a terheléselosztót, amihez hozzá kell rendelnünk az előbb létrehozott célcsoportot.

Ehhez a következő menüsoron jutunk el: `EC2 → Load Balancers → Create load balancer (ALB/NLB)` 

Név: <mark>1stLB</mark>

<img width="1307" height="802" alt="Képernyőfotó 2026-07-24 - 22 58 09" src="https://github.com/user-attachments/assets/2afb3efb-0178-442b-8a58-c62aa6586a78" />

A magas rendelkezésre álláshoz több subnetet - elérhetőségi zónát választunk ki:

<img width="1306" height="797" alt="Képernyőfotó 2026-07-24 - 22 58 33" src="https://github.com/user-attachments/assets/aef3a39a-3d71-43d3-8853-5ab9dc7fb60a" />

Security beállítások a korábban beállítottak kiválasztása:

<img width="1307" height="330" alt="Képernyőfotó 2026-07-24 - 22 58 54" src="https://github.com/user-attachments/assets/9d03ed8e-5aea-4e6a-bc77-df97b12110ee" />

Célcsoport hozzárendelése a következő lépés, hogy melyik szerverekre küldjön kérést. Itt a korábban létrehozott <mark>1stTG</mark> rendeljük hozzá.

<img width="1306" height="661" alt="Képernyőfotó 2026-07-24 - 22 59 13" src="https://github.com/user-attachments/assets/7a46c0ac-5c2d-4bae-9bcb-57ce8db1275f" />

Az adatok megadása és célcsoport hozzáadása után létrehozhatjuk az első terheléselosztónkat. 

Név: <mark>1stLB</mark>

<img width="1309" height="800" alt="Képernyőfotó 2026-07-24 - 23 02 14" src="https://github.com/user-attachments/assets/f8432297-348e-4725-b0e3-a406a4eaac3e" />

Ha már mindennel kész vagyunk akkor az utolsó lépésben létrehozhatunk egy ASG (Auto Scaling Group) a következő menüsoron: 

`EC2 → Auto Scaling Groups → Create Auto Scaling group`

Az ASG fogja nekünk felügyelni, hogy a szerverek rendben működnek és igény esetén ki és vagy leállítja őket. 

A konfiguráció első lépésében elnevezzük: <mark>1stAS</mark>

Launch template kiválasztásánál hozzá rendeljük a korábban létrehozottat <mark>1stTemplate</mark>

<img width="1305" height="800" alt="Képernyőfotó 2026-07-24 - 23 08 25 1" src="https://github.com/user-attachments/assets/d1c49fba-292e-40a6-b1d5-9c40729bcdb4" />

VPC esetén alapbeállítást használunk - nyilvánosan elérhető

Kiválasztjuk a rendelkezésre álló zónákat, itt megint a több kiválasztása esetén a magas rendelkezésre állást tudjuk támogatni:

<img width="1311" height="805" alt="Képernyőfotó 2026-07-24 - 23 08 56" src="https://github.com/user-attachments/assets/d59d2833-e865-44ec-815e-14badf87ad8f" />

A meglévő és eddig felépített terheléselosztót hozzá rendeljük az ASG-hez.

`Existing load balancer target group` csatolása

<img width="1308" height="799" alt="Képernyőfotó 2026-07-24 - 23 09 27" src="https://github.com/user-attachments/assets/dda05521-2a63-47bb-9b16-a9991e8039a2" />

Min/Max/Desired capacity beállítása választásánál konfigurálhatjuk, hogy mennyi a kívánt/minimum/maximum szerver szám, amit szeretnénk működtetni.

<img width="1309" height="680" alt="Képernyőfotó 2026-07-24 - 23 09 54" src="https://github.com/user-attachments/assets/68ff33fe-02cc-4993-bbfa-cfff983a60f1" />

Scaling policy beállítása. 
<img width="1304" height="499" alt="Képernyőfotó 2026-07-24 - 23 10 08" src="https://github.com/user-attachments/assets/86a83f06-2356-4a5b-bc06-4e4e9a6494ac" />

`Create Auto Scaling group` kattintva létre is hozzuk az első ASG-t. A minimumot a konfiguráció esetén 3-ra állítottam és itt látszik is, hogy 3/3 healty rendelkezésre áll.


<img width="1309" height="470" alt="Képernyőfotó 2026-07-24 - 23 10 53" src="https://github.com/user-attachments/assets/8215c6f9-6741-45c3-b41b-53709cb9a08b" />


Skálázási beállítások gyakorlása. Itt a jobban láthatóság kedvéért felemeltem a minimum szerverek számát.

Létrejöttek a kívánt mennyiségű szerverek:

<img width="1067" height="444" alt="Képernyőfotó 2026-07-24 - 23 13 57" src="https://github.com/user-attachments/assets/b150b1cc-4740-4291-a8cb-76bce97e99da" />

Kézzel leállítottam egyet és az ASG újraindította azt.

<img width="1062" height="438" alt="Képernyőfotó 2026-07-24 - 23 14 49" src="https://github.com/user-attachments/assets/a7229147-571d-4e5a-bfe5-1ea2c6d97092" />

Indítottam egy extraszervert is amelyet később az ASG egy másik leállításával korrigál. 

<img width="1057" height="419" alt="Képernyőfotó 2026-07-24 - 23 25 09" src="https://github.com/user-attachments/assets/da9d2084-910d-4ecc-9056-f144a4258aa4" />

