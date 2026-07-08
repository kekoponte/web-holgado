# Web Holgado

Sitio estatico oficial del proyecto musical Holgado.

## Estructura

```
.
├── index.html
├── robots.txt
├── .well-known/
├── assets/
│   ├── audio/
│   ├── images/
│   └── vendor/
└── .github/
    ├── copilot-instructions.md
    └── workflows/
```

## Edicion local

1. Abre la carpeta en VS Code.
2. Edita `index.html`.
3. Sirve en local con cualquier servidor estatico (opcional), por ejemplo:

```bash
python3 -m http.server 8000
```

Luego abre `http://localhost:8000`.

## Recomendaciones de mantenimiento

- Guarda imagenes e iconos en `assets/images/`.
- Guarda previews de canciones en `assets/audio/`.
- Evita subir archivos temporales (`.DS_Store`, etc.).

## Despliegue automatico

Este repo incluye un workflow para desplegar por SSH cuando haces push a `main`:

- Archivo: `.github/workflows/deploy-ssh.yml`
- Guia paso a paso: `docs/deploy-ssh-github-actions.md`
