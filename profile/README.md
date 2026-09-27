# CatsSociety
Read this file

# Bienvenido a la organización

Este es el espacio donde cada quien trae sus proyectos, y todos podemos ayudarnos sin pisar el trabajo de nadie.

## Cómo agregar tu repositorio

1. Ve a **Repositories → New repository**.
2. En **Owner**, selecciona esta organización (no tu cuenta personal).
3. Elige si será **público** o **privado** según tu proyecto.
4. Ya tienes un repo en tu cuenta personal? Puedes transferirlo:
   `Settings del repo → Transfer ownership → escribe el nombre de la organización`

Al crear tu repo, tú quedas como dueño/admin de ese repositorio específico. Nadie más puede pushear directo ahí a menos que tú se lo permitas.

## Regla obligatoria al crear tu repo: protege tu rama `main`

Esto evita que se rompa el proyecto por accidente (incluso a ti mismo):

1. `Settings` del repo → `Branches` → `Add rule`
2. Nombre de la rama: `main`
3. Activa:
   - [!] Require a pull request before merging
   - [!] Require approvals (mínimo 1)

Esto se configura **una sola vez por repo** y queda para siempre.

## Cómo ayudar en el proyecto de otro

Por defecto, todos podemos **ver y clonar** cualquier repo de la organización, pero no pushear directo. Así se hace una contribución correcta:

1. Entra al repo que quieres ayudar.
2. Dale a **Fork** (funciona incluso en repos privados).
3. Clona **tu fork**, no el original.
4. Crea una rama para tu cambio.
5. Sube tus cambios a tu fork.
6. Abre un **Pull Request** hacia el repo original.
7. El dueño del repo revisa y decide si lo aprueba y mergea.

## Reglas básicas que no se rompen

- Nunca pidas ni des permiso de **Write** directo sobre el repo de otra persona. Todo pasa por PR.
- No se borra ni transfiere ningún repo sin avisar al grupo — esa acción está restringida solo a los Owners de la organización.
- Toda rama `main` debe tener protección activada (PR + aprobación) antes de empezar a trabajar en serio.
- Si haces un PR a un repo ajeno, describe brevemente **qué cambia y por qué**.
- Si algo no queda claro, se pregunta antes de tocar el código de otro.

## Resumen del espíritu del grupo

> Puedes ver y clonar todo. Puedes proponer ayuda a todo. Pero solo el dueño de un repo decide qué entra en el suyo.
