- EC2 → Launch Templates → Create launch template
- <img width="1305" height="804" alt="Képernyőfotó 2026-07-24 - 23 30 02" src="https://github.com/user-attachments/assets/0585c878-17dd-40ee-b556-5e9e6e498fc5" />

  - Standard (AWS által adott) AMI kiválasztása
  - <img width="1302" height="803" alt="Képernyőfotó 2026-07-24 - 23 30 13" src="https://github.com/user-attachments/assets/5b3c4cd6-a60e-4cc5-b532-c2b88828bb49" />

  - Instance type, security group, key pair megadása
  - <img width="873" height="477" alt="Képernyőfotó 2026-07-24 - 23 30 44" src="https://github.com/user-attachments/assets/78a93c0a-4772-4176-a3e9-fb395e1434b0" />

  - Advanced Network Settings → Auto-assign public IP → Enable
  - <img width="868" height="568" alt="Képernyőfotó 2026-07-24 - 23 31 12" src="https://github.com/user-attachments/assets/ecf903c0-c4ce-47e3-b36b-0f0c549a5708" />

  - User data script megadása (bootstrap/telepítés induláskor)
  - <img width="1468" height="870" alt="Képernyőfotó 2026-07-24 - 23 37 11" src="https://github.com/user-attachments/assets/f3e6cdfc-a810-40a5-99ec-6b2317f07ce0" />

- EC2 → Target Groups → Create target group (health check beállítása)
- <img width="1311" height="795" alt="Képernyőfotó 2026-07-24 - 23 38 08" src="https://github.com/user-attachments/assets/2f25f66c-2631-477b-a301-b42ac22f5edd" />

- EC2 → Load Balancers → Create load balancer (ALB/NLB) → target group hozzárendelése
- <img width="1307" height="791" alt="Képernyőfotó 2026-07-24 - 23 39 09" src="https://github.com/user-attachments/assets/7105705d-05e0-4e4b-8355-4661aff5d571" />

<img width="1305" height="437" alt="Képernyőfotó 2026-07-24 - 23 39 28" src="https://github.com/user-attachments/assets/c4c45e79-519a-49af-8363-c7fc7d3108cf" />

- EC2 → Auto Scaling Groups → Create Auto Scaling group - Launch template kiválasztása
- <img width="1301" height="795" alt="Képernyőfotó 2026-07-24 - 23 43 07" src="https://github.com/user-attachments/assets/24f30a14-4623-49cf-86f4-19f8fc1c379b" />

  - VPC + subnetek megadása
  - <img width="943" height="673" alt="Képernyőfotó 2026-07-24 - 23 43 26" src="https://github.com/user-attachments/assets/12cb973b-53ae-4a8e-ae49-6536243fb7d7" />

  - Existing load balancer target group csatolása
  - <img width="962" height="608" alt="Képernyőfotó 2026-07-24 - 23 43 44" src="https://github.com/user-attachments/assets/f51cfcac-70cc-42df-a66b-f6633244a7e8" />

  - Min/Max/Desired capacity beállítása - Scaling policy beállítása
  - <img width="927" height="628" alt="Képernyőfotó 2026-07-24 - 23 44 17" src="https://github.com/user-attachments/assets/8807a97f-a3d9-4ccb-85d2-6567f630d22e" />
Create Auto Scaling group
<img width="1273" height="257" alt="Képernyőfotó 2026-07-24 - 23 45 04" src="https://github.com/user-attachments/assets/02c9a16b-7757-4941-8e75-0d9f4f36daff" />

Átállítottam a AS min/max-ot - elindultak a szerverek
<img width="1070" height="439" alt="Képernyőfotó 2026-07-25 - 0 02 31" src="https://github.com/user-attachments/assets/27a9a76e-f100-4d87-8898-577097af84a7" />

További még két szervert indítottam el - de itt is az a problémám hogy nem állítja le az ASG. 
<img width="1058" height="457" alt="Képernyőfotó 2026-07-25 - 0 03 18" src="https://github.com/user-attachments/assets/0480bb0f-2de7-490b-9498-d90a28e01c9b" />

Ha kikapcsolom akkor újra indít, az itt is működik. 
<img width="1043" height="278" alt="Képernyőfotó 2026-07-25 - 0 13 20" src="https://github.com/user-attachments/assets/a1bd9527-7548-414f-84df-28f1b3061cab" />

