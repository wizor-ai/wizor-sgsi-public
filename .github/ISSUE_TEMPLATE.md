name: Solicitud de cambio documental
description: Proponer, corregir o actualizar contenido en el sitio de SGSI
title: "[docs]: "
labels: ["docs"]
body:
  - type: textarea
    attributes:
      label: Descripción del cambio
      description: ¿Qué se debe agregar/modificar/eliminar?
    validations:
      required: true
  - type: dropdown
    attributes:
      label: Sección afectada
      options:
        - SGSI/Alcance
        - SGSI/Roles
        - SGSI/Metodología
        - Anexos
        - Changelog
        - Evidencias
    validations:
      required: true
  - type: input
    attributes:
      label: Impacto (minor/major)
  - type: textarea
    attributes:
      label: Notas adicionales
