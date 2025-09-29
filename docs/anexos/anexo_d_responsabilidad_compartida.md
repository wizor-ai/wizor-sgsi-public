---
title: Anexo D — Responsabilidad Compartida
version: "1.0"
last_review: "2025-09-26"
owner: "RSI"
status: "Vigente"
next_review: "2026-09-26"
---

# Anexo D — Responsabilidad Compartida

**Versión:** 1.0  
**Fecha de última revisión:** 26/09/2025  
**Responsable:** Responsable de Seguridad de la Información (RSI)

## Objetivo
Definir de manera clara la distribución de responsabilidades en materia de **seguridad de la información** entre **Amazon Web Services (AWS)** y **Wizor**, bajo el modelo de **responsabilidad compartida**.  
Este anexo busca garantizar transparencia en los límites de control y facilitar el cumplimiento de **ISO/IEC 27001** frente a clientes, auditores y terceros.

## Alcance
Aplica a todos los servicios backend, la infraestructura cloud utilizada por la plataforma Wizor, y los procesos de autenticación y autorización integrados con **Auth0**.  
Quedan excluidos sistemas **on-premise** y cualquier infraestructura física que es responsabilidad exclusiva de AWS.

> **Nota sobre estructura organizativa:**  
> Actualmente, dado que **Wizor** es una startup en etapa temprana, algunos roles (p. ej., RSI, DevOps, Backend Lead, Frontend Lead) son desempeñados por una única persona. Esta asignación se encuentra documentada y será revisada conforme el equipo crezca para garantizar segregación de funciones y cumplimiento continuo.

## Modelo de Responsabilidad Compartida

| Área de Control                                                               | AWS        | Wizor      |
|-------------------------------------------------------------------------------|------------|------------|
| **Infraestructura física y hardware**                                         | ✔️         | —          |
| **Red y virtualización base**                                                 | ✔️         | —          |
| **Servicios administrados (EC2, RDS, S3, Lambda, VPC, KMS, WAF, CloudTrail)** | ✔️         | —          |
| **Configuración segura de servicios**                                         | —          | ✔️         |
| **Gestión de identidades y accesos en la nube (IAM, Auth0)**                  | —          | ✔️         |
| **Protección de datos en tránsito y en reposo (TLS, KMS, claves)**            | Compartido | Compartido |
| **Monitoreo, logging y auditoría (CloudWatch, GuardDuty, PostHog)**           | Compartido | Compartido |
| **Gestión de cambios y despliegues**                                          | —          | ✔️         |
| **Respuesta a incidentes y notificación a clientes**                          | Compartido | ✔️         |
| **Cumplimiento normativo y contratos con clientes**                           | —          | ✔️         |
| **Evaluación y gestión de proveedores externos (Auth0, PostHog, CDN)**        | —          | ✔️         |

## Controles específicos gestionados por Wizor

- **Autenticación segura**: login con usuario/contraseña, passwordless (link mágico o código OTP) y Single Sign-On (SSO).
- **Autenticación multifactor (MFA)**: SMS, email, TOTP, aplicaciones de autenticación y WebAuthn.
- **Gestión centralizada de identidades**: integración de Auth0 para web, mobile y APIs.
- **Protocolos estándar de seguridad**: OAuth 2.0, OpenID Connect y SAML para interoperabilidad con terceros.
- **Seguridad avanzada de accesos**: detección de intentos sospechosos, bloqueo de IPs, throttling y análisis de patrones de login.
- **Gestión de secretos**: AWS Secrets Manager y Parameter Store para credenciales y llaves.
- **Control de cambios y despliegues**: revisión por pares, pipelines CI/CD y aprobación antes de pasar a producción.
- **Retención de logs de seguridad y auditoría**: mínimo de 12 meses para análisis forense y cumplimiento regulatorio.

## Controles exclusivos de AWS

- Seguridad física y ambiental de los centros de datos.
- Infraestructura global de red y virtualización.
- Cumplimiento de normas internacionales (ISO/IEC 27001, SOC, PCI DSS, etc.) disponible a través de **AWS Artifact**.
- Monitoreo de amenazas a nivel de plataforma y protección frente a ataques DDoS con AWS Shield.

---

Este modelo asegura que la **seguridad física y de la infraestructura subyacente** está cubierta por **AWS**, mientras que **Wizor** gestiona la **seguridad de la configuración, los datos, los accesos y el cumplimiento en la capa de aplicación**.