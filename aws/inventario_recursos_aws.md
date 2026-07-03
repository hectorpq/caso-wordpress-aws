# Inventario de Recursos AWS

## Red
- VPC: nova-vpc | 10.0.0.0/16
- IGW: nova-igw
- Subred pública 1: nova-public-1 | 10.0.1.0/24 | us-east-1a
- Subred pública 2: nova-public-2 | 10.0.2.0/24 | us-east-1b
- Subred privada 1: nova-private-1 | 10.0.10.0/24 | us-east-1a
- Subred privada 2: nova-private-2 | 10.0.11.0/24 | us-east-1b

## Cómputo
- nova-wordpress-1 | t3.micro | 52.23.215.92 | us-east-1a
- nova-wordpress-2 | t3.micro | 44.195.89.101 | us-east-1b

## Base de Datos
- nova-wordpress-db | MySQL 8.0 | db.t3.micro
- Endpoint: nova-wordpress-db.crrrpvqf3vvd.us-east-1.rds.amazonaws.com

## Almacenamiento
- S3: comercial-nova-backups-2024 | Versionado ON

## Load Balancer
- nova-alb | DNS: nova-alb-1822451503.us-east-1.elb.amazonaws.com

## Auto Scaling
- Template: nova-wordpress-template
- ASG: nova-wordpress-asg | min 2 | max 4 | CPU 70%

## Monitoreo
- Alarma 1: nova-cpu-alta (CPU > 80%)
- Alarma 2: nova-cpu-alta-2 (CPU > 80%)
- Alarma 3: nova-rds-storage (Storage < 2GB)
