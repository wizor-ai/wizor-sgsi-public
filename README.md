# Wizor • SGSI (Sitio público)

Este repositorio publica documentación **pública** del SGSI de Wizor mediante **GitHub Pages**.
Las evidencias y documentos **sensibles** no se alojan aquí; se entregan bajo NDA a solicitud.

## Cómo usar
1. Coloca tus anexos *ya redactados* en `docs/anexos/` (formato Markdown).
2. Ajusta navegación en `mkdocs.yml` si cambias nombres.
3. Activa GitHub Pages: Settings → Pages → *Deploy from a branch* → `main` / `docs`.
4. (Opcional) Usa MkDocs Material mediante GitHub Actions (ver `.github/workflows/pages.yml`).

## Estructura
```
docs/
  index.md
  sgsi/
    alcance.md
    roles.md
    metodologia.md
  changelog/
    index.md
  evidencias/
    como-solicitar-evidencias.md
  anexos/        # coloca aquí tus anexos públicos (A, B, C, D, E, ...)
  assets/
.github/
  workflows/pages.yml
CHANGELOG.md
SECURITY.md
mkdocs.yml
```

## Convenciones
- **Front-matter** en cada archivo con `version`, `last_review`, `owner`, `status`.
- **Conventional Commits** en mensajes de commit.
- **CODEOWNERS** obliga revisión del RSI en cambios de `docs/`.

## Contacto
- compliance@wizor.io
