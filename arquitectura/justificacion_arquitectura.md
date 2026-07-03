# Justificación de Arquitectura - Comercial Nova

## Diseño de Red (VPC)
- VPC propia (10.0.0.0/16) para control total de red
- 2 AZs (us-east-1a y us-east-1b) para alta disponibilidad
- Subredes públicas para ALB y EC2
- Subredes privadas para RDS (sin acceso internet)

## Cómputo (EC2)
- 2 instancias t3.micro en AZs diferentes
- Auto Scaling (2-4 instancias, CPU 70%)
- Amazon Linux 2023 + Apache + PHP 8.5

## Base de Datos (RDS)
- MySQL 8.0 en subred privada
- Solo accesible desde nova-ec2-sg
- Backup automático 7 días
- Cifrado en reposo (AWS KMS)

## Balanceo de Carga (ALB)
- Distribuye tráfico entre 2 EC2s
- Health checks automáticos
- Internet-facing para acceso público

## Almacenamiento (S3)
- Versionado habilitado
- Bloqueo de acceso público
- Para backups y logs

## Monitoreo (CloudWatch)
- 5 alarmas activas
- CPU EC2 > 80%
- RDS Storage < 2GB
