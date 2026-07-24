- Custom AMI elkészítése (lásd fentebb: instance → Create image → AMI)
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

