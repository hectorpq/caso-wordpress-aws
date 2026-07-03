# Matriz de Accesos - Comercial Nova

## Security Groups

### nova-alb-sg (ALB)
| Puerto | Protocolo | Origen | Propósito |
|---|---|---|---|
| 80 | HTTP | 0.0.0.0/0 | Acceso público |
| 443 | HTTPS | 0.0.0.0/0 | Acceso público |

### nova-ec2-sg (EC2)
| Puerto | Protocolo | Origen | Propósito |
|---|---|---|---|
| 80 | HTTP | nova-alb-sg | Desde ALB |
| 22 | SSH | 0.0.0.0/0 | Administración |

### nova-rds-sg (RDS)
| Puerto | Protocolo | Origen | Propósito |
|---|---|---|---|
| 3306 | MySQL | nova-ec2-sg | Solo desde EC2 |

## IAM
- Rol: LabInstanceProfile (AWS Academy)
- Permisos: S3, CloudWatch, EC2 metadata
- No se usaron credenciales root

## Cifrado
- RDS: AWS KMS (en reposo)
- S3: Bloqueo público total
