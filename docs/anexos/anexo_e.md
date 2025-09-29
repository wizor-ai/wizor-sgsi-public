---
title: Anexo E — Gestión de Riesgos (Resumen y Ejemplos)
version: "1.0"
last_review: "2025-09-26"
owner: "RSI"
status: "Vigente"
next_review: "2026-09-26"
---

# Anexo E — Gestión de Riesgos

**Versión:** 1.0  
**Fecha de última revisión:** 26/09/2025  
**Responsable:** Responsable de Seguridad de la Información (RSI)

## Objetivo
Proveer un resumen de la gestión de riesgos de la información en **Wizor**, detallando cómo se identifican, evalúan, tratan y monitorean los riesgos, sin exponer información sensible.  
Este anexo complementa el apartado **6. Gestión de riesgos** del informe y referencia la **Matriz de Riesgos y Plan de Tratamiento** mantenida internamente.

## Alcance
Incluye los servicios backend, infraestructura en **AWS**, autenticación con **Auth0**, aplicaciones móviles y web (frontend), repositorios de código y herramientas de monitoreo.  
Excluye sistemas administrativos internos no vinculados al servicio ofrecido a clientes.

## Periodicidad de revisión
Este documento se revisa al menos una vez al año y también cada vez que existan cambios significativos en la arquitectura, servicios críticos, procesos o normativa aplicable.

> **Nota sobre estructura organizativa:**  
> Actualmente, dado que **Wizor** es una startup en etapa temprana, los roles definidos (por ejemplo, Responsable de Seguridad de la Información —RSI—, DevOps, Backend Lead, Frontend Lead) son desempeñados por una única persona.  
> Esta asignación centralizada se encuentra documentada y es revisada periódicamente. Conforme el equipo crezca, estos roles serán delegados y reasignados para garantizar una adecuada segregación de funciones y mantener el cumplimiento con los requisitos de **ISO/IEC 27001**.

---

## Metodología aplicada

Wizor gestiona riesgos de acuerdo con la norma **ISO/IEC 27005** y el ciclo **PDCA (Plan–Do–Check–Act)**:

- **Identificación de activos:** datos sensibles de clientes, infraestructura en AWS (EC2, RDS, S3, Lambda), servicios de autenticación y autorización (Auth0), aplicaciones web y mobile, repositorios de código y herramientas de monitoreo (CloudWatch, PostHog).
- **Identificación de amenazas y vulnerabilidades:** accesos indebidos, errores de configuración cloud, exposición de secretos, ataques de inyección (SQL/XSS/CSRF), interrupción de servicio, dependencia de proveedores externos.
- **Valoración de riesgos:** análisis de impacto (alto, medio, bajo) y probabilidad de ocurrencia para priorizar los riesgos críticos.
- **Tratamiento de riesgos:** controles técnicos (cifrado, MFA, IAM, WAF, segregación de ambientes), organizativos (políticas y procedimientos) y contractuales (evaluación de proveedores y DPA).
- **Monitoreo y revisión:** actualización periódica de la matriz de riesgos, revisión de controles y documentación de incidentes para retroalimentar la mejora continua.

---

## Ejemplos de riesgos y controles aplicados

| Riesgo identificado                       | Control implementado                                                                     |
|-------------------------------------------|------------------------------------------------------------------------------------------|
| Exposición de secretos en repositorios    | Uso de AWS Secrets Manager y escaneo automático para detección de credenciales.          |
| Acceso indebido a cuentas críticas        | Auth0 con MFA obligatorio y principio de mínimo privilegio en IAM.                       |
| Fuga de datos en entornos de prueba       | Segregación de ambientes (dev/staging/prod) y anonimización de datos sensibles.          |
| Vulnerabilidades en dependencias externas | Análisis SAST/SCA en CI y procesos de actualización con plazos definidos por criticidad. |
| Interrupción del servicio                 | Despliegue multi-AZ y planes de recuperación (RTO/RPO) definidos y probados.             |

---

## Nota sobre la matriz completa

Wizor mantiene una **Matriz de Riesgos y Plan de Tratamiento** detallada (ver **Anexo B**), que incluye todos los activos, amenazas, valoraciones y responsables de tratamiento.  
Por motivos de seguridad, esta matriz se entrega solo bajo acuerdo de confidencialidad (NDA) o durante auditorías formales.