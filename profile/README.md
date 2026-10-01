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

> **Todo en esta guía se hace desde la página de GitHub, en el navegador. No necesitas terminal.**

### Mini glosario
- **Repo (repositorio):** la carpeta de un proyecto en GitHub.
- **Rama (branch):** una versión paralela del proyecto. `main` es la principal.
- **Fork:** tu copia personal de un repo ajeno, donde sí puedes editar.
- **Commit:** guardar un cambio en el repo (en la web, el botón verde **Commit changes**).
- **Pull Request (PR):** una propuesta de cambio; el dueño la revisa y decide si la acepta.
- **Ruleset / Bypass:** las reglas que protegen una rama, y la excepción que permite al dueño saltarlas de forma controlada.

## Cómo agregar tu repositorio
```text
       /\_/\                                              /\_/\
      ( o.o )                                            ( -.- )
       > ^ <                                              > ^ <
   +-----------+--------------------------------------+-----------+
   |  GitHub   |    github.com/cat/repo               |   Linux   |
   |   /\_/\   |                                      |   .--.    |
   |  ( o.o )  |   [+] Owner: CatsSociety             |  |o_o |   |
   |   > ^ <   |   [+] Repositories > New repository  |  |:_/ |   |
   | Octocat   |   [OK] Repo creado en la org         | //   \ \  |
   +-----------+--------------------------------------+-(|     | )+
                                                        /'\_   _/`
                                                        \___)=(___/
          /\_/\                                    /\_/\
         ( °.° )                                  ( =^.^= )
         />  <\                                    >   <
```
1. Ve a **Repositories → New repository**.
2. En **Owner**, selecciona esta organización (no tu cuenta personal).
3. Elige si será **público** o **privado**. ⚠️ En el plan gratuito, la protección de `main` (ver más abajo) **solo funciona en repos públicos**; en uno privado no podrás protegerlo.
4. ¿Ya tienes un repo en tu cuenta personal? Puedes transferirlo:
   `Settings del repo → Transfer ownership → CatsSociety`
5. Listo, habrás agregado un repo a esta organización.

Al crear tu repo, tú quedas como dueño/admin de ese repositorio específico. Nadie más puede pushear directo ahí a menos que tú se lo permitas.

## Ramas de trabajo: `main` vs `beta`
```text
  /\_/\                                       /\_/\
 ( o.o )        MAIN  (protegida)            ( -.- )
  > ^ <    +------------------------+         > ^ <
 /     \   |  solo merges vía PR    |        /     \
(       )  |  nada de commits       |       (       )
 `-----'   |  directos aquí         |        `-----'
           +-----------+------------+
                       ^
                       |  PR  (beta -> main)
                       |
           +-----------+------------+
           |  BETA  (tu taller)     |
           |  aquí sí guardas todo  |
           |  todo lo experimental  |
           +------------------------+
                /\_/\         /\_/\
               ( o.o )       ( =^.^= )
                > ^ <         >   <
```

- `main` → solo recibe cambios vía PR. Es la versión estable.
- `beta` → tu taller. Aquí van los cambios en progreso o experimentales.
- `feature/*` o `fix/*` → opcionales, para cambios muy puntuales antes de pasar a `beta` o `main`.
- Crea `beta` **desde `main`**: selector de ramas → escribe `beta` → **Create branch**.
- Para editar en `beta`: en el selector de ramas elige `beta`, abre el archivo, pulsa el **lápiz** y **Commit changes** (queda guardado en `beta`).
- Cuando algo esté estable: pestaña **Pull requests** → **New pull request** → *base:* `main`, *compare:* `beta` → **Create pull request**.
- `beta` es para los **dueños** del repo. Quien colabora desde fuera trabaja en su propio fork (ver más abajo).

`beta` no es obligatoria, pero es la convención recomendada para mantener `main` limpia.

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
   |  Repo > Settings > Rules > Rulesets > New ruleset               |
   |  [x] Require a pull request before merging                      |
   |  [x] Bypass list: Repository admin (PR only)                    |
   |                                                                 |
   |  [OK] Main branch is now fully locked & secure.                 |
   |  [!] Direct commits to 'main' are DISABLED.                     |
   +-----------------------------------------------------------------+
            \_____________________________________________/
```

Esto evita que se rompa el proyecto por accidente (incluso a ti mismo). Se hace con un **Ruleset**:

1. En tu repo: `Settings` → `Rules` → `Rulesets` → `New ruleset` → `New branch ruleset`.
2. Ponle un nombre (por ejemplo `proteger-main`) y deja **Enforcement status** en `Active`.
3. En `Target branches` → `Add target` → `Include default branch` (o escribe `main`).
4. Activa:
   - [!] **Require a pull request before merging**
   - [!] **Required approvals** (ver tabla de abajo, depende de cuántos sean)
5. Bypass para el dueño (para no bloquearte a ti mismo):
   - En `Bypass list` → `Add bypass` y selecciona el rol **Repository admin** (la lista acepta roles, equipos o apps, no personas sueltas).
   - Elige el modo:

| Modo | Qué permite | Cuándo usarlo |
|------|-------------|---------------|
| `For pull requests only` | Saltarse las reglas **solo al mergear un PR** | **Recomendado**: mantiene la disciplina de PR |
| `Always allow` | Push directo a `main` sin PR | Solo si realmente lo necesitas |

6. Baja y pulsa **Create**.

Esto se configura **una sola vez por repo** y queda para siempre.

### ¿Cuántas aprobaciones pedir?

| Escenario | Configuración sugerida |
|-----------|------------------------|
| Repo de una sola persona | Solo "Require a pull request" (0 aprobaciones) o 1 aprobación + bypass `For pull requests only` para poder mergear tu propio PR |
| Repo con 2 o más personas | 1 aprobación. Nadie puede aprobar su propio PR, así que otra persona revisa |

> **Nota sobre el plan:** en el plan gratuito de GitHub, las reglas de protección (rulesets y branch protection) solo funcionan en repos **públicos**. En repos privados necesitas un plan de pago (Team o superior). Si tu repo es privado en plan gratuito, la regla no se aplicará.

## Cómo ayudar en el proyecto de otro
```text
          /\_/\               /\_/\               /\_/\
         ( o.o )             ( °.° )             ( -.- )
          > ^ <               > ^ <               > ^ <
     +-------------------------------------------------------+
     |  FORKED FROM: upstream/cat-project                    |
     |                                                       |
     |  [Fork] > [Edit file] > [Commit changes]              |
     |  Editas el archivo desde el navegador                 |
     |                                                       |
     |  -  printf("Gatos + Linux + GitHub = Perfection");    |
     |  +  printf("Forked & Improved by Feline Contributor");|
     |                                                       |
     |  [Contribute] > [Open pull request]                   |
     +-------------------------------------------------------+
      \_____________________________________________________/
         \_____________________________________________|_/
```

Por defecto, todos podemos **ver y clonar** cualquier repo público de la organización, pero no pushear directo. Así se hace una contribución correcta:

1. Entra al repo que quieres ayudar.
2. Dale al botón **Fork** (arriba a la derecha) → **Create fork**. Ahora estás en tu copia.
3. Abre el archivo que quieres cambiar y pulsa el **lápiz** (*Edit this file*).
4. Haz tu cambio y pulsa **Commit changes...** → elige **Create a new branch for this commit**, ponle un nombre (por ejemplo `fix-typo`) y confirma.
5. GitHub mostrará el botón **Compare & pull request** (o, en tu fork, **Contribute → Open pull request**). Verifica que el destino sea el repo original.
6. Escribe **qué cambia y por qué** y pulsa **Create pull request**.
7. El dueño del repo revisa y decide si lo aprueba y mergea.

> **Repos privados:** solo se pueden forkear si la organización tiene activada la opción *Allow forking of private repositories* (`Settings` de la org → `Member privileges`). Si no, pide acceso al dueño o trabaja con él por otra vía.

### Un PR puede venir de dos lados
```text
  /\_/\                          /\_/\
 ( o.o )   Desde un fork        ( -.- )   Desde el mismo repo
  > ^ <    (contribuidor)        > ^ <    (el dueño)

  su-fork/rama ──► tu-repo/main     tu-repo/beta ──► tu-repo/main
```

## Cuando te llega un PR (para dueños)
```text
        /\_/\
       ( o.o )    "Nuevo PR detectado..."
        > ^ <
     +--------------------------------------+
     |  1. Te llega notificación (campana)  |
     |  2. Pestaña Pull requests            |
     |  3. Files changed -> revisa el diff  |
     |  4. Comenta / pide cambios / aprueba |
     |  5. Merge pull request               |
     |  6. Delete branch (limpieza)         |
     +--------------------------------------+
```

1. GitHub te notifica (campana + correo).
2. Ve a la pestaña **Pull requests** del repo.
3. Revisa **Files changed** (el diff línea por línea).
4. Comenta, pide cambios o aprueba.
5. Si todo está bien → **Merge pull request**. Si el repo pide aprobaciones y eres el único dueño, usa la opción **Merge without waiting for requirements** (es tu bypass en acción).
6. Borra la rama del PR si ya no se usa (**Delete branch**).

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
   |  [OK] Todo se hace desde el navegador                 |
   +-------------------------------------------------------+
            \___________________________________/
```

- Nunca pidas ni des permiso de **Write** directo sobre el repo de otra persona. Todo pasa por PR.
- No se borra ni transfiere ningún repo sin avisar al grupo — esa acción está restringida solo a los Owners de la organización.
- Toda rama `main` debe tener protección con PR obligatorio antes de empezar a trabajar en serio (las aprobaciones dependen de cuántos sean en el repo).
- Nunca se edita `main` directo: los dueños trabajan en `beta`; quien colabora desde fuera, en su fork.
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
