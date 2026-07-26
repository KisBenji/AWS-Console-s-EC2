Custom AMI elkészítése (lásd fentebb: instance → Create image → AMI)
<img width="1310" height="800" alt="Képernyőfotó 2026-07-24 - 22 48 20" src="https://github.com/user-attachments/assets/8df514a9-92df-4189-aa84-6e2668d9f6af" />

EC2 → Launch Templates → Create launch template
<img width="1303" height="793" alt="Képernyőfotó 2026-07-24 - 22 52 53" src="https://github.com/user-attachments/assets/0a6a95f4-8fd5-4509-a549-8bf1736b3038" />

Saját Custom AMI kiválasztása
<img width="1306" height="801" alt="Képernyőfotó 2026-07-24 - 22 53 15" src="https://github.com/user-attachments/assets/7b79c9ef-d8d5-4e8c-8f8b-420d7762fb60" />

Instance type, security group, key pair megadása
<img width="1300" height="801" alt="Képernyőfotó 2026-07-24 - 22 53 50" src="https://github.com/user-attachments/assets/e629738b-4296-4a41-8f31-7b2fab44aa24" />
<img width="1303" height="794" alt="Képernyőfotó 2026-07-24 - 22 54 16" src="https://github.com/user-attachments/assets/b07dc641-1590-495c-9fcd-23e5553f66eb" /><img width="1309" height="805" alt="Képernyőfotó 2026-07-24 - 22 54 47" src="https://github.com/user-attachments/assets/eae03f38-418c-4b0f-80b7-533fa7036b9f" />

EC2 → Target Groups → Create target group
<img width="1308" height="805" alt="Képernyőfotó 2026-07-24 - 22 55 19" src="https://github.com/user-attachments/assets/eaf5c104-0ccb-4128-93df-e9d0376d69d2" />

Health check beállítása
<img width="1307" height="797" alt="Képernyőfotó 2026-07-24 - 22 56 01" src="https://github.com/user-attachments/assets/45fac1af-8db3-471f-9ac0-ac4b84a74930" />
<img width="1305" height="801" alt="Képernyőfotó 2026-07-24 - 22 57 35" src="https://github.com/user-attachments/assets/85257a44-bf00-4a9b-9ba8-6fd16a959ad7" />

EC2 → Load Balancers → Create load balancer (ALB/NLB) → target group hozzárendelése
<img width="1307" height="802" alt="Képernyőfotó 2026-07-24 - 22 58 09" src="https://github.com/user-attachments/assets/2afb3efb-0178-442b-8a58-c62aa6586a78" />
<img width="1306" height="797" alt="Képernyőfotó 2026-07-24 - 22 58 33" src="https://github.com/user-attachments/assets/aef3a39a-3d71-43d3-8853-5ab9dc7fb60a" />
<img width="1307" height="330" alt="Képernyőfotó 2026-07-24 - 22 58 54" src="https://github.com/user-attachments/assets/9d03ed8e-5aea-4e6a-bc77-df97b12110ee" />
<img width="1306" height="661" alt="Képernyőfotó 2026-07-24 - 22 59 13" src="https://github.com/user-attachments/assets/7a46c0ac-5c2d-4bae-9bcb-57ce8db1275f" />
<img width="1309" height="800" alt="Képernyőfotó 2026-07-24 - 23 02 14" src="https://github.com/user-attachments/assets/f8432297-348e-4725-b0e3-a406a4eaac3e" />

EC2 → Auto Scaling Groups → Create Auto Scaling group
Launch template kiválasztása
<img width="1305" height="800" alt="Képernyőfotó 2026-07-24 - 23 08 25 1" src="https://github.com/user-attachments/assets/d1c49fba-292e-40a6-b1d5-9c40729bcdb4" />

VPC + subnetek megadása
<img width="1311" height="805" alt="Képernyőfotó 2026-07-24 - 23 08 56" src="https://github.com/user-attachments/assets/d59d2833-e865-44ec-815e-14badf87ad8f" />

Existing load balancer target group csatolása
<img width="1308" height="799" alt="Képernyőfotó 2026-07-24 - 23 09 27" src="https://github.com/user-attachments/assets/dda05521-2a63-47bb-9b16-a9991e8039a2" />

Min/Max/Desired capacity beállítása
<img width="1309" height="680" alt="Képernyőfotó 2026-07-24 - 23 09 54" src="https://github.com/user-attachments/assets/68ff33fe-02cc-4993-bbfa-cfff983a60f1" />

Scaling policy beállítása
<img width="1304" height="499" alt="Képernyőfotó 2026-07-24 - 23 10 08" src="https://github.com/user-attachments/assets/86a83f06-2356-4a5b-bc06-4e4e9a6494ac" />

Create Auto Scaling group
<img width="1309" height="470" alt="Képernyőfotó 2026-07-24 - 23 10 53" src="https://github.com/user-attachments/assets/8215c6f9-6741-45c3-b41b-53709cb9a08b" />


Skálázási beállítások gyakorlása. Állíts le szervert kézzel és figyeld meg, hogy az ASG újraindítja-e a leállított gépet. Indíts el több gépet, és figyeld meg, hogy az ASG leállítja-e a felesleges gépeket.
Létrejöttek szerverek
<img width="1067" height="444" alt="Képernyőfotó 2026-07-24 - 23 13 57" src="https://github.com/user-attachments/assets/b150b1cc-4740-4291-a8cb-76bce97e99da" />
Kézzel leállítottam és az ASG újraindította
<img width="1062" height="438" alt="Képernyőfotó 2026-07-24 - 23 14 49" src="https://github.com/user-attachments/assets/a7229147-571d-4e5a-bfe5-1ea2c6d97092" />

Indítottam egy extraszervert
<img width="1057" height="419" alt="Képernyőfotó 2026-07-24 - 23 25 09" src="https://github.com/user-attachments/assets/da9d2084-910d-4ecc-9056-f144a4258aa4" />

