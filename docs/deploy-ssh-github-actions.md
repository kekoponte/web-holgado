# Guia: despliegue por SSH con GitHub Actions (paso a paso)

Esta guia esta pensada para principiantes y funciona con el workflow incluido en este proyecto.

## 1) Preparar el servidor

En tu servidor (VPS o hosting con SSH):

1. Crea la carpeta de despliegue, por ejemplo:

```bash
mkdir -p /var/www/holgado.band
```

2. Asegurate de que el usuario SSH tiene permisos de escritura sobre esa carpeta.

## 2) Crear una clave SSH para GitHub Actions

En tu Mac, genera una clave nueva (mejor separada de tu clave personal):

```bash
ssh-keygen -t ed25519 -C "github-actions-holgado" -f ~/.ssh/holgado_actions
```

Esto crea:
- clave privada: `~/.ssh/holgado_actions`
- clave publica: `~/.ssh/holgado_actions.pub`

## 3) Autorizar la clave publica en el servidor

1. Muestra la publica:

```bash
cat ~/.ssh/holgado_actions.pub
```

2. Copia todo el contenido (empieza por `ssh-ed25519 ...`).
3. Pegalo al final de `~/.ssh/authorized_keys` del usuario de despliegue en el servidor.

## 4) Guardar secretos en GitHub

En tu repositorio de GitHub:

1. Ve a Settings > Secrets and variables > Actions.
2. Crea estos secretos:

- `SSH_PRIVATE_KEY`: contenido completo de `~/.ssh/holgado_actions`
- `SSH_HOST`: dominio o IP del servidor (ejemplo: `holgado.band`)
- `SSH_USER`: usuario SSH (ejemplo: `deploy`)
- `SSH_PORT`: normalmente `22`
- `DEPLOY_PATH`: ruta remota de despliegue (ejemplo: `/var/www/holgado.band`)

## 5) Subir el repo y lanzar el primer despliegue

1. Haz push a la rama `main`.
2. Ve a la pestaña Actions de GitHub.
3. Entra en el workflow "Deploy por SSH".
4. Comprueba que termina en verde.

Si falla, abre el job y revisa el paso exacto que da error.

## 6) Verificacion final

1. Abre tu web en el navegador.
2. Fuerza recarga (Shift + Reload) para evitar cache.
3. Comprueba que cargan imagenes, audio y enlaces.

## Problemas comunes

- `Permission denied (publickey)`: clave publica no esta en `authorized_keys` correcto.
- `No such file or directory` en destino: `DEPLOY_PATH` incorrecto o sin permisos.
- Cambios no visibles: cache del navegador o CDN.
