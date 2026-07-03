# caso-wordpress-aws
# Comercial Nova - WordPress en AWS
## Universidad Peruana Unión - Ingeniería de Sistemas

**Estudiante:** Hector Robert Pacompia Quispe  
**Curso:** Virtualización de Servicios Tecnológicos  
**Fecha:** 3 de Julio de 2026

## Problema Planteado
Comercial Nova necesita un portal web corporativo escalable, seguro y de alta disponibilidad en AWS.

## Arquitectura
- VPC nova-vpc (10.0.0.0/16) con subredes públicas y privadas en 2 AZs
- 2 EC2 t3.micro con WordPress (us-east-1a y us-east-1b)
- Application Load Balancer distribuyendo tráfico
- RDS MySQL en subred privada con backup 7 días
- S3 para backups con versionado
- Auto Scaling Group (min 2, max 4, CPU 70%)
- CloudWatch con 5 alarmas activas

## Servicios AWS Utilizados
| Servicio | Recurso | Propósito |
|---|---|---|
| VPC | nova-vpc | Red segmentada |
| EC2 | 2x t3.micro | Capa de aplicación |
| RDS | MySQL 8.0 | Base de datos |
| S3 | comercial-nova-backups | Almacenamiento |
| ALB | nova-alb | Balanceo de carga |
| Auto Scaling | nova-wordpress-asg | Escalabilidad |
| CloudWatch | 5 alarmas | Monitoreo |

## URL WordPress
- Instancia 1: http://52.23.215.92
- Instancia 2: http://44.195.89.101
- ALB (Alta Disponibilidad): http://nova-alb-1822451503.us-east-1.elb.amazonaws.com

## Costos Estimados
| Servicio | Costo/mes |
|---|---|
| EC2 (2x t3.micro) | $12.14 |
| RDS MySQL | $17.86 |
| ALB | $16.20 |
| S3 | $0.23 |
| Data Transfer | $3.00 |
| **TOTAL** | **$49.43** |

## Optimizaciones de Costos
1. Reserved Instances 1 año (ahorro 25%)
2. S3 Intelligent-Tiering para backups
3. Shutdown automático en horarios no críticos

## Seguridad
- Security Groups con mínimo privilegio
- RDS en subred privada (sin acceso público)
- S3 con bloqueo de acceso público
- IAM con LabInstanceProfile (AWS Academy)
- Cifrado en reposo en RDS (AWS KMS)

## Monitoreo
- 5 alarmas CloudWatch activas
- CPU EC2 > 80% → alerta
- RDS FreeStorageSpace < 2GB → alerta
- Auto Scaling alarmas de escalado

## Limitaciones AWS Academy
- No permite crear roles IAM personalizados → se usa LabInstanceProfile
- CloudWatch Dashboards bloqueados (política voc-cancel-cred) → se usan alarmas

## Lecciones Aprendidas
- Amazon Linux 2023 usa php-mysqli (no php-mysql)
- Security Groups son críticos para conectividad
- Multi-AZ garantiza alta disponibilidad real
- ALB simplifica balanceo de carga entre instancias

## Mejoras Futuras
- HTTPS con AWS Certificate Manager
- EFS para archivos compartidos entre instancias
- WAF para protección web
- RDS Multi-AZ
- CloudFront como CDN
