---
title: Anexo B — Gestión de Riesgos de la Información
version: "1.1"
last_review: "2025-09-26"
owner: "RSI"
status: "Vigente"
next_review: "2026-09-26"
---

# Anexo B: Gestión de Riesgos de la Información

**Versión:** 1.0  
**Fecha de última revisión:** 26/09/2025  
**Responsable:** Responsable de Seguridad de la Información (RSI)

## Objetivo
Definir el proceso mediante el cual **Wizor** identifica, evalúa, trata y monitorea los riesgos que pueden afectar la **confidencialidad, integridad y disponibilidad** de la información dentro del alcance de este informe (Backend, Cloud, Frontend y Aplicaciones Web/Mobile).

Este anexo respalda el cumplimiento de los requisitos de **ISO/IEC 27001** y se alinea con la norma complementaria **ISO/IEC 27005** para gestión de riesgos de seguridad de la información.

## Alcance
Incluye los servicios backend, infraestructura en **AWS** (EC2, RDS, S3, Lambda, VPC), autenticación y autorización con **Auth0**, aplicaciones móviles y web (incluida la capa de presentación y distribución de contenido mediante CDN).  
No abarca sistemas administrativos internos no vinculados al servicio.

## Marco de referencia
El proceso sigue el ciclo de mejora continua **PDCA (Plan-Do-Check-Act)** y se actualiza ante cambios significativos en la infraestructura, aplicaciones o proveedores críticos.  
Este proceso cubre controles de la **ISO/IEC 27001** asociados a los dominios **A.5 Seguridad Organizacional**, **A.8 Gestión de Activos**, **A.12 Seguridad de Operaciones** y **A.18 Cumplimiento**.

## 1. Identificación de activos
- Datos sensibles de clientes (información personal y credenciales).
- Infraestructura Cloud: EC2, RDS, S3, Lambda, VPC.
- Servicios de autenticación y autorización: Auth0.
- Código fuente y repositorios.
- Aplicaciones Web y Mobile (frontend y clientes móviles).
- CDN y distribución de recursos estáticos.
- Herramientas de monitoreo y telemetría (PostHog, CloudWatch).
- Configuraciones y secretos.

## 2. Identificación de amenazas y vulnerabilidades
- Acceso indebido o escalamiento de privilegios.
- Errores de configuración en AWS y en la capa de red.
- Exposición accidental de secretos.
- Inyección de código (SQL, XSS, CSRF).
- Fuga de datos en aplicaciones mobile (almacenamiento inseguro, debugging no autorizado).
- Interrupción de servicios (DoS, fallos de proveedor).
- Alteración de recursos estáticos servidos desde CDN.
- Dependencia de terceros críticos sin respaldo.
- Manejo inadecuado de mensajes de error y logging.

## 3. Valoración de riesgos

| Nivel | Impacto                                                            | Probabilidad               |
|-------|--------------------------------------------------------------------|----------------------------|
| Alto  | Compromiso total de datos sensibles, caída prolongada de servicio. | Alta ocurrencia probable.  |
| Medio | Afecta disponibilidad parcial o datos no críticos.                 | Posible pero no frecuente. |
| Bajo  | Impacto limitado o mitigable con facilidad.                        | Ocurrencia poco probable.  |

La combinación de impacto y probabilidad define el **Nivel de Riesgo** (Alto, Medio, Bajo).

**Criterios de aceptación de riesgo:**  
Los riesgos clasificados como *Bajos* y *Medios* pueden aceptarse cuando el costo de mitigación supera el beneficio de reducir el riesgo, previa aprobación del **Responsable de Seguridad de la Información (RSI)** y la Dirección.

## 4. Tratamiento de riesgos
Los riesgos identificados se gestionan a través de:

- **Controles técnicos:**
   - Cifrado en tránsito (TLS 1.2/1.3) y reposo (AES-256).
   - IAM con **least privilege**, MFA, WAF y GuardDuty.
   - SAST/SCA en CI, revisión de permisos en buckets S3, controles de CSP y SRI para frontend.
   - Almacenamiento seguro de credenciales y tokens en dispositivos móviles (Keychain, Keystore).
   - Políticas de seguridad para recursos servidos vía CDN.

- **Controles organizativos:**
   - Políticas de seguridad y control de cambios.
   - Procesos de gestión de incidentes y revisiones de accesos.
   - Capacitación a personal sobre buenas prácticas de seguridad (incluyendo OWASP para desarrollo web y mobile).

- **Controles contractuales:**
   - DPA y evaluaciones de seguridad de proveedores externos (Auth0, PostHog, CDN).

Cada riesgo queda registrado en la **Matriz de Riesgos** con responsable asignado y estado de tratamiento (aceptado, mitigado, transferido o eliminado).

## 5. Roles y responsabilidades

| Rol                                                  | Responsabilidad principal                                                                |
|------------------------------------------------------|------------------------------------------------------------------------------------------|
| **RSI (Responsable de Seguridad de la Información)** | Mantener y actualizar la matriz de riesgos, aprobar aceptación de riesgos residuales.    |
| **DevOps**                                           | Configuración segura de AWS, CI/CD y monitoreo.                                          |
| **Backend Lead**                                     | Seguridad en APIs, manejo de datos y cumplimiento de buenas prácticas de codificación.   |
| **Frontend Lead**                                    | Implementación de controles de seguridad en Web y Mobile (CSP, SRI, manejo de sesiones). |
| **Dirección**                                        | Aprobación de políticas y aceptación de riesgos de alto impacto.                         |

## 6. Monitoreo y mejora continua

| Actividad                     | Frecuencia                        |
|-------------------------------|-----------------------------------|
| Revisión de matriz de riesgos | Trimestral                        |
| Auditoría interna             | Anual                             |
| Actualización de activos      | Cuando hay cambios significativos |

- Los hallazgos de revisiones de seguridad, análisis de vulnerabilidades y cambios tecnológicos alimentan la matriz.
- Las excepciones y riesgos aceptados se documentan y revisan periódicamente.

---

> **Nota:** La Matriz de Riesgos completa y detallada se mantiene como documento interno confidencial y se presenta bajo demanda durante auditorías (ver **Anexo E** para un extracto de ejemplo).
> **Nota sobre estructura organizativa:**  
> Actualmente, dado que **Wizor** es una startup en etapa temprana, los roles definidos (por ejemplo, Responsable de Seguridad de la Información —RSI—, DevOps, Backend Lead, Frontend Lead) son desempeñados por una única persona en cada caso.  
> Esta asignación centralizada se encuentra documentada y es revisada periódicamente. Conforme el equipo crezca, estos roles serán delegados y reasignados para garantizar una adecuada segregación de funciones y mantener el cumplimiento con los requisitos de **ISO/IEC 27001**.