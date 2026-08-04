# Virtuális gép (EC2) létrehozása AWS felületén

AWS Console bejelentkezés után meg kell keresnünk az -> EC2, amire kattintva elérhető a `New instance`, amivel megtudjuk kezdeni a virtuális gépünk konfigurálását. 

Kötelező adatok megadása:

A példa esetén a szerver neve: <mark>1stWebserver<mark>

Kiválasztható milyen szervert szeretnénk elindítani: <mark>AWS Linux<mark>

<img width="1309" height="800" alt="Képernyőfotó 2026-07-24 - 22 23 10" src="https://github.com/user-attachments/assets/27a9988f-474c-4f73-9e0b-2e365ac3a74d" />

A szerver típusa, ahol a példához elegendő teljesítményű és ingyenes verzió került kiválasztásra: <mark>t3.micro<mark>

A kulcs megadása kötelező, ezt előzetesen generáltam és letöltöttem a gépemre <mark>kulcs-2026</mark> 

Amennyiben még nincs kulcsod, itt tudsz generálni is. 

<img width="1309" height="800" alt="Képernyőfotó 2026-07-24 - 22 23 26" src="https://github.com/user-attachments/assets/bde1eb70-31f8-46e2-8839-64b5e7a29b17" />



Security beállításoknál létre lehet hozni új alapbeállítást. Itt, hogy a szerver elérhető legyen az internet felől javasolt a `Allow HTTP traffic from internet` lehetőséget engedélyezni. 

<img width="1305" height="800" alt="Képernyőfotó 2026-07-24 - 22 24 52" src="https://github.com/user-attachments/assets/a47188fd-2af4-4c79-88c6-50c75ae86599" />


Az Advanced részben a User Data script megadásánál írhatunk be kódot ha telepíteni szeretnénk valamit induláskor. Ebbe a kódba belemódosítottam a példa készítésekor, hogy névként a <mark>1stWebserver</mark> jelenjen meg. Az eredeti itt található és másolható ki:

```
#!/bin/bash
yum update -y
yum install -y httpd.x86_64
systemctl start httpd.service
systemctl enable httpd.service
echo "<html><head><style>body{font-family: Verdana, Geneva, Tahoma, sans-serif;background-image: url('https://github.com/cloudsteak/azurestaticwebsite/blob/main/assets/images/wallpaper-2025-01.jpeg?raw=true');background-repeat: no-repeat;background-size: cover; background-position: center;color: white; text-align: center; padding-top: 1%;}</style></head><body><h1>Web:<br>$(hostname)</h1></body></html>" > /var/www/html/index.html
```

<img width="1307" height="799" alt="Képernyőfotó 2026-07-24 - 22 27 19" src="https://github.com/user-attachments/assets/c2fc8cd1-6b02-492c-a7b4-676df4168813" />


Ha minden adat megadásával készen vagyunk már csak rá kell kattintani a `Launch instance`

Innét már csak pár perc amíg megjelenik az AWS oldalán, hogy a szerver elindult és működik amit a Status-nál látunk: 

>3/3 checks passed


<img width="1305" height="794" alt="Képernyőfotó 2026-07-24 - 22 29 18" src="https://github.com/user-attachments/assets/908ef471-4ea2-4b9d-b560-74c42d6c349d" />

Webserver elkészült és a nyilvános IP-címről elérhető, kimásolva és a böngészőnkbe beírva a következőt fogjuk látni:

<img width="1306" height="799" alt="Képernyőfotó 2026-07-24 - 22 30 10" src="https://github.com/user-attachments/assets/97129a87-596b-4464-b9a1-ca07581c5630" />
