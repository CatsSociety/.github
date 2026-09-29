# CatsSociety
Read this file

# Bienvenido a la organización
```text
  /\_/\   +---------------------------------------+   /\_/\
 ( o.o )  |             CATS                      |   ( -.- )
  > ^ <   |                SOCIETY                |   > ^ <
  /   \   |              ORGANIZATION             |   /   \
 (     )  +---------------------------------------+  (     )
  `---'                                               `---'
```

Este es el espacio donde cada quien trae sus proyectos, y todos podemos ayudarnos sin pisar el trabajo de nadie.

## Cómo agregar tu repositorio
```text
       /\_/\                                              /\_/\
      ( o.o )                                            ( -.- )
       > ^ <                                              > ^ <
   +-----------+--------------------------------------+-----------+
   |  GitHub   |    github.com/cat/repo               |   Linux   |
   |   /\_/\   |                                      |   .--.    |
   |  ( o.o )  |   $ git push origin main             |  |o_o |   |
   |   > ^ <   |   [+] 3 files changed, 42 insertions |  |:_/ |   |
   | Octocat   |   [OK] Everything up-to-date         | //   \ \  |
   +-----------+--------------------------------------+-(|     | )+
                                                        /'\_   _/`
                                                        \___)=(___/
          /\_/\                                    /\_/\
         ( °.° )                                  ( =^.^= )
         />  <\                                    >   <
```
1. Ve a **Repositories → New repository**.
2. En **Owner**, selecciona esta organización (no tu cuenta personal).
3. Elige si será **público** o **privado** según tu proyecto.
4. Ya tienes un repo en tu cuenta personal? Puedes transferirlo:
   `Settings del repo → Transfer ownership → Agregar de Owner a CatsSociety`
5. Listo, habras agregado un repo en esta organizacion.

Al crear tu repo, tú quedas como dueño/admin de ese repositorio específico. Nadie más puede pushear directo ahí a menos que tú se lo permitas.

## Regla obligatoria al crear tu repo: protege tu rama `main`
```text
  /\_/\                                                  /\_/\
 ( o.o )                   .---.                         ( -.- )
  > ^ <                   /  .  \                         > ^ <
 /     \                 |  | |  |                       /     \
(       )               .--+-----+--.                   (       )
 `-----'                |   (O)     |                    `-----'
                        '-----------'
   +-----------------------------------------------------------------+
   |  NEW REPO SETUP: MAIN BRANCH PROTECTION                         |
   |                                                                 |
   |  $ gh repo create my-repo --public                              |
   |  $ gh api -X PUT repos/:owner/:repo/branches/main/protection \  |
   |     -F required_status_checks=true \                            |
   |     -F enforce_admins=true                                      |
   |                                                                 |
   |  [OK] Main branch is now fully locked & secure.                 |
   |  [!] Direct commits to 'main' are DISABLED.                     |
   +-----------------------------------------------------------------+
            \_____________________________________________/
```

Esto evita que se rompa el proyecto por accidente (incluso a ti mismo):

1. `Settings` del repo → `Branches` → `Add rule`
2. Ir hacia `Target branches` Nombre de la rama: `main` o por la que este por defecto.
3. Activa:
   - [!] Require a pull request before merging
   - [!] Require approvals (mínimo 1)
4. Ademas de todo eso, hay que hacer un acceso especial
   - En la misma pagina anterior, ir hacia `Bypass lis`
   - `Add bypass` y seleccionar a su perfil `No fallen en eso`
5. Una vez tenga todo lo anterior, ir hacia abajo y `create`.

Esto se configura **una sola vez por repo** y queda para siempre.
Asegurate que este en publico para que la regla se aplique.

## Cómo ayudar en el proyecto de otro
```text
          /\_/\               /\_/\               /\_/\
         ( o.o )             ( °.° )             ( -.- )
          > ^ <               > ^ <               > ^ <
     +-------------------------------------------------------+
     |  FORKED FROM: upstream/cat-project                    |
     |                                                       |
     |  $ git clone https://github.com/my-cat/repo           |
     |  $ vim main.c                                         |
     |                                                       |
     |  -  printf("Gatos + Linux + GitHub = Perfection");    |
     |  +  printf("Forked & Improved by Feline Contributor");|
     |                                                       |
     |  $ git push && gh pr create --title "Fix code"        |
     +-------------------------------------------------------+
      \_____________________________________________________/
         \_____________________________________________|_/
```

Por defecto, todos podemos **ver y clonar** cualquier repo de la organización, pero no pushear directo. Así se hace una contribución correcta:

1. Entra al repo que quieres ayudar.
2. Dale a **Fork** (funciona incluso en repos privados).
3. Clona **tu fork**, no el original.
4. Crea una rama para tu cambio.
5. Sube tus cambios a tu fork.
6. Abre un **Pull Request** hacia el repo original.
7. El dueño del repo revisa y decide si lo aprueba y mergea.

## Reglas básicas que no se rompen
```text
  /\_/\                                                 /\_/\
 ( o.o )                 / \                           ( -.- )
  > ^ <                 /   \                           > ^ <
 /     \               /  !  \                         /     \
(       )             /______\                        (       )
 `-----'            WARNING ZONE                       `-----'
   +-------------------------------------------------------+
   |  GITHUB / LINUX SECURITY SYSTEM                       |
   |                                                       |
   |  [!] ATTENTION: Unauthorized Feline Access Detected   |
   |  [!] ACCESS: GRANTED (Because they are cute)          |
   |                                                       |
   |  $ git status --cats                                  |
   +-------------------------------------------------------+
            \___________________________________/
```

- Nunca pidas ni des permiso de **Write** directo sobre el repo de otra persona. Todo pasa por PR.
- No se borra ni transfiere ningún repo sin avisar al grupo — esa acción está restringida solo a los Owners de la organización.
- Toda rama `main` debe tener protección activada (PR + aprobación) antes de empezar a trabajar en serio.
- Si haces un PR a un repo ajeno, describe brevemente **qué cambia y por qué**.
- Si algo no queda claro, se pregunta antes de tocar el código de otro.

## Resumen del espíritu del grupo
```text
               /\_/\                                     /\_/\
              ( o.o )                                   ( -.- )
               > ^ <                                     > ^ <
             /       \                                 /       \
  /\_/\     /  OCTO   \   +-------------------------+ /  KITTY  \     /\_/\
 ( °.° )   |   CAT     |  | GITHUB.COM/LINUX        | |         |   ( =^.^= )
  > ^ <   /|           |\ |                         | |         |\   > ^ <
 /     \ / |   /\_/\   | \| init() {                | |  /\_/\  | \ /     \
(  CAT  )  |  ( o.o )  |  |   print("hello Linux"); | | ( o.o ) |  (  TUX  )
 `-----'   |   > ^ <   |  | }                       | |  > ^ <  |   `-----'
           +-----------+  +-------------------------+ +---------+
            |  ______ |   /                       \   | ______  |
            | |  ..  ||  /_________________________\  ||  ..   ||
            | |______| | |__________________________| ||_______||
```

> Puedes ver y clonar todo. Puedes proponer ayuda a todo. Pero solo el dueño de un repo decide qué entra en el suyo.
