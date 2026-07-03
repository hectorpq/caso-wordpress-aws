# Análisis de Costos - Comercial Nova

## Costo Mensual Actual
| Servicio | Costo |
|---|---|
| EC2 2x t3.micro | $12.14 |
| RDS db.t3.micro | $17.86 |
| ALB | $16.20 |
| S3 | $0.23 |
| Data Transfer | $3.00 |
| **TOTAL** | **$49.43** |

## Optimizaciones

### 1. Reserved Instances (ahorro 25%)
- EC2 + RDS con RI 1 año
- Ahorro: ~$7.50/mes

### 2. S3 Intelligent-Tiering
- Backups antiguos a Glacier
- Ahorro: ~$2/mes

### 3. Shutdown automático
- Apagar fuera de horario pico
- Ahorro: ~$6/mes

## Total Optimizado: ~$34/mes (ahorro 31%)
