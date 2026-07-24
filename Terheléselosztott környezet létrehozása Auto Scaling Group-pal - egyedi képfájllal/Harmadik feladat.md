- Custom AMI elkészítése (lásd fentebb: instance → Create image → AMI)
- <img width="1310" height="800" alt="Képernyőfotó 2026-07-24 - 22 48 20" src="https://github.com/user-attachments/assets/8df514a9-92df-4189-aa84-6e2668d9f6af" />

- EC2 → Launch Templates → Create launch template
  - Saját Custom AMI kiválasztása
  - Instance type, security group, key pair megadása
- EC2 → Target Groups → Create target group (health check beállítása)
- EC2 → Load Balancers → Create load balancer (ALB/NLB) → target group hozzárendelése
- EC2 → Auto Scaling Groups → Create Auto Scaling group
  - Launch template kiválasztása
  - VPC + subnetek megadása
  - Existing load balancer target group csatolása
  - Min/Max/Desired capacity beállítása
  - Scaling policy beállítása
- Create Auto Scaling group

Gyakorold a skálázási beállításokat. Állíts le szervert kézzel és figyeld meg, hogy az ASG újraindítja-e a leállított gépet. Indíts el több gépet, és figyeld meg, hogy az ASG leállítja-e a felesleges gépeket.

