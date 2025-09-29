---
title: Anexo C — Integración de la Solución con el Marco ISO/IEC 27001
version: "1.0"
last_review: "2025-09-26"
owner: "RSI"
status: "Vigente"
next_review: "2026-09-26"
---

# Anexo C — Integración de la Solución con el Marco ISO/IEC 27001

**Versión:** 1.0  
**Fecha de última revisión:** 26/09/2025  
**Responsable:** Responsable de Seguridad de la Información (RSI)

## Objetivo
Este anexo tiene como finalidad mostrar de forma estructurada cómo la plataforma **Wizor** (Backend, Cloud en AWS y aplicaciones Web/Mobile) implementa controles alineados con los requisitos del **Anexo A de la norma ISO/IEC 27001:2013**.  
Sirve como mapa de cumplimiento para auditores, clientes y partes interesadas, facilitando la trazabilidad entre los controles de la norma y las medidas técnicas y organizativas adoptadas.

## Alcance
Incluye los servicios en la nube de AWS utilizados por Wizor, el desarrollo y despliegue del backend y las aplicaciones móviles y web, así como los mecanismos de seguridad y control de acceso a información sensible.  
Quedan fuera de este alcance otros sistemas internos no relacionados con el backend y la infraestructura cloud de la plataforma.

## Periodicidad de revisión
Este documento se revisa al menos una vez al año y cada vez que existan cambios significativos en la arquitectura, los servicios críticos o en la normativa aplicable.

> **Nota sobre estructura organizativa:**  
> Actualmente, dado que **Wizor** es una startup en etapa temprana, algunos roles definidos (p. ej., Responsable de Seguridad de la Información —RSI—, DevOps, Backend Lead, Frontend Lead) son desempeñados por una única persona. Esta asignación centralizada se encuentra documentada y será revisada conforme el equipo crezca para asegurar segregación de funciones y cumplimiento continuo.

---

## Mapeo de controles ISO/IEC 27001 con implementación en Wizor

| Dominio ISO/IEC 27001                                         | Control relevante                                     | Implementación en Wizor                                                                                                                                           |
|---------------------------------------------------------------|-------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **A.5 Política de seguridad de la información**               | **A.5.1.1 Política de seguridad de la información**   | Política formal publicada y aprobada por la Dirección (Anexo A). Revisión anual y comunicación a todo el personal.                                                |
| **A.6 Organización de la seguridad de la información**        | **A.6.1 Roles y responsabilidades**                   | Nombramiento de Responsable de Seguridad de la Información (RSI). Roles definidos y documentados; revisión periódica.                                             |
| **A.8 Gestión de activos**                                    | **A.8.1 Inventario de activos**                       | Inventario de sistemas críticos (AWS EC2, RDS, S3, Lambda, Auth0, PostHog) y clasificación según sensibilidad.                                                    |
| **A.9 Control de acceso**                                     | **A.9.1 Control de acceso a sistemas y aplicaciones** | IAM con principio de menor privilegio, MFA obligatorio para cuentas críticas, Auth0 como IdP centralizado para apps Web/Mobile. Revisión trimestral de permisos.  |
| **A.10 Criptografía**                                         | **A.10.1 Uso de controles criptográficos**            | Cifrado en tránsito (TLS 1.2/1.3) y en reposo (AES-256 mediante KMS). Gestión de claves y secretos en AWS KMS y Secrets Manager.                                  |
| **A.12 Seguridad de las operaciones**                         | **A.12.1 Procedimientos operativos documentados**     | Despliegues controlados vía CI/CD, revisión por pares y cambios aprobados antes de pasar a producción. Logs centralizados y retención mínima de 12 meses.         |
| **A.12.4 Registros y monitoreo**                              | **A.12.4.1 Eventos y logs de auditoría**              | CloudTrail, WAF, GuardDuty y PostHog integrados para detectar accesos anómalos y eventos críticos. Alertas configuradas en CloudWatch/Security Hub.               |
| **A.12.6 Gestión de vulnerabilidades técnicas**               | **A.12.6.1 Gestión de vulnerabilidades**              | Escaneo continuo de dependencias (SAST/SCA), revisiones de hardening y registro de excepciones de remediación según riesgo documentado en el SGSI.                |
| **A.13 Seguridad en las comunicaciones**                      | **A.13.1 Gestión de redes y seguridad**               | VPCs privadas, subredes segregadas, uso de WAF, Security Groups y monitoreo de tráfico para detectar amenazas.                                                    |
| **A.14 Seguridad en el desarrollo y soporte**                 | **A.14.2 Principios de desarrollo seguro**            | Clean Architecture, control de dependencias, testing automatizado, análisis SAST en CI, ambientes separados (dev/staging/prod).                                   |
| **A.15 Relación con proveedores**                             | **A.15.1 Seguridad en la relación con proveedores**   | Evaluación de seguridad de servicios clave (Auth0, PostHog). Acuerdos y contratos de procesamiento de datos (DPA) cuando corresponde.                             |
| **A.16 Gestión de incidentes de seguridad de la información** | **A.16.1 Gestión de incidentes**                      | Procedimiento documentado para reporte y análisis de incidentes. Canales internos definidos y notificación a clientes según impacto.                              |
| **A.17 Aspectos de continuidad del negocio**                  | **A.17.1 Planificación de continuidad**               | Despliegue multi-AZ en AWS, respaldos automáticos y pruebas periódicas de restauración. Objetivos RTO/RPO definidos internamente.                                 |

---

## Ciclo de mejora continua (PDCA)

- Los controles descritos se revisan de forma periódica, considerando resultados de auditorías, incidentes, cambios tecnológicos y evaluaciones de proveedores.
- La **matriz de riesgos (Anexo B)** es actualizada como insumo para priorizar acciones de mitigación.

## Evidencia disponible

- Configuraciones de AWS IAM, KMS y WAF.
- Reportes de escaneo de vulnerabilidades (SAST/SCA).
- Procedimientos de gestión de incidentes y restauración de backups.
- Contratos y DPA con proveedores críticos como Auth0 y PostHog.