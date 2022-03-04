# Autograders

En el curso de CC-3 vamos a estar utilizando Autograders para que ustedes puedan
obtener retroalimentación de su trabajo más rápidamente.

## Instalación

Vamos a utilizar un CLI que preparó el staff del curso para que puedan subir sus archivos al autograder y que califique de manera automática. Para esto vamos a necesitar tener instalado **NodeJS** en nuestras computadoras, de preferencia una version >= 16.

### NVM

Si ustedes están en Linux es fácil de instalar utilizando `NVM` [Node Version Manager](https://github.com/nvm-sh/nvm) por sus siglas en inglés. Abran una terminal: ++ctrl+alt+t++ e ingresen el siguiente comando:

```sh
wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
```

Posteriormente ustedes deberán hacer `source` a su bash profile, ejecutando el siguiente comando:

```sh
source ~/.bashrc
```

Pueden verificar que se haya instalado correctamente `nvm` ingresando el siguiente comando:

```sh
nvm -v
```

Este comando debería de imprimir en la terminal la versión de `nvm` que instalaron, algo parecido a esto:

```sh
0.39.1
```

### NodeJS

Ahora ya que tenemos `nvm` podemos instalar NodeJS haciendo uso del siguiente comando:

```sh
nvm install --lts
```

Esto va instalar la versión LTS de NodeJS, pueden validar que tienen Node instalado, al finalizar, ingresando el siguiente comando:

```sh
node -v
```

El cual debería imprimir algo parecido a esto:

```sh
v16.13.2
```

### Autograders CLI

Por último vamos a instalar el CLI de autograders haciendo uso de **NPM** (Node Package Manager). Ingresen el siguiente comando en su terminal:

```sh
npm install -g @autograders/cli
```

Para verificar que se instalado de manera correcta, pueden probar el siguiente comando:

```sh
autograders -h
```

El cual debería de genera la siguiente salida:

```sh
╭ Autograders ╮
│             │
│    Help     │
│             │
╰─────────────╯

  Usage:
    $ autograders <option>

  Options
    --sign-up                     Create a new user
    --resend-email-verification   Resend email verification token
    --verify-email                Verify user email
    --sign-in                     Authenticate user
    --forgot-password             Send reset password token
    --reset-password              Reset password
    --submit                      Create a submission
    --get-last-submit             Get last submission
    --get-best-submit             Get best submission
    --help, -h                    Print CLI help.

  Examples:
    $ autograders --sign-in
    $ autograders --submit
```

## Uso de Autograders

Una vez tengan instalado el CLI de autograders podran hacer uso del mismo para sus laboratorios y proyectos.

### Creando una cuenta

Lo primero que tienen que hacer es crear una cuenta en autograders, para eso ustedes deberán utilizar el siguiente comando:

```sh
autograders --sign-up
```

Ingresen la información que se les solicita, y por favor al ingresar su correo, ingresen el correo de la Universidad Galileo. De lo contrario sus laboratorios se van a calificar pero no podremos pasar la nota al GES, es decir, tendrán **0 como nota**.

Al terminar de ingresar sus datos se va a crear un usuario y se les enviara un correo electrónico con un token para que ustedes puedan verificar su correo.

```sh
╭ Autograders ╮
│             │
│   Sign Up   │
│             │
╰─────────────╯

✔ First Name … Andrés

✔ Last Name … Castellanos

✔ Email … andres.cv@galileo.edu

✔ Password … **************

✔ User created successfully.

Created User:

╔═══════════════╤══════════════════════════╗
║ id            │ 61fcd33c10a10341e78bc4b6 ║
╟───────────────┼──────────────────────────╢
║ email         │ andres.cv@galileo.edu    ║
╟───────────────┼──────────────────────────╢
║ firstName     │ Andrés                   ║
╟───────────────┼──────────────────────────╢
║ lastName      │ Castellanos              ║
╟───────────────┼──────────────────────────╢
║ isVerified    │ false                    ║
╟───────────────┼──────────────────────────╢
║ isDeactivated │ false                    ║
╟───────────────┼──────────────────────────╢
║ isInstructor  │ false                    ║
╟───────────────┼──────────────────────────╢
║ createdAt     │ 2022-02-04T07:18:20.966Z ║
╟───────────────┼──────────────────────────╢
║ updatedAt     │ 2022-02-04T07:18:20.966Z ║
╚═══════════════╧══════════════════════════╝
```

El correo que les llegará se tiene que ver así:

![Autograders Sign Up](/assets/img/autograders-sign-up.png)

Si el correo no les llega ustedes pueden volver a intentarlo, haciendo uso del siguiente comando:

```sh
autograders --resend-email-verification
```

> **NOTA**: Si ustedes no tienen verificado su correo, no podran iniciar sesión y subir sus archivos al autograder. Verifiquen su correo.

### Verificando su Correo

Ya que tiene un token de verificación, pueden ingresarlo utilizando el siguiente comando:

```sh
autograders --verify-email
```

Al ingresar la información que se les solicita, les tiene que desplegar un resultado similar a este:

```sh
╭── Autograders ───╮
│                  │
│   Verify Email   │
│                  │
╰──────────────────╯

✔ Email … andres.cv@galileo.edu

✔ Token … ************************

✔ User email verified successfully.

Updated User:

╔═══════════════╤══════════════════════════╗
║ id            │ 61fcd33c10a10341e78bc4b6 ║
╟───────────────┼──────────────────────────╢
║ email         │ andres.cv@galileo.edu    ║
╟───────────────┼──────────────────────────╢
║ firstName     │ Andrés                   ║
╟───────────────┼──────────────────────────╢
║ lastName      │ Castellanos              ║
╟───────────────┼──────────────────────────╢
║ isVerified    │ true                     ║
╟───────────────┼──────────────────────────╢
║ isDeactivated │ false                    ║
╟───────────────┼──────────────────────────╢
║ isInstructor  │ false                    ║
╟───────────────┼──────────────────────────╢
║ createdAt     │ 2022-02-04T07:18:20.966Z ║
╟───────────────┼──────────────────────────╢
║ updatedAt     │ 2022-02-04T07:24:16.944Z ║
╚═══════════════╧══════════════════════════╝
```

### Iniciando Sesión.

Para iniciar sesión pueden utilizar el siguiente comando:

```sh
autograders --sign-in
```

Les va a pedir que ingresen su correo y contraseña, si ingresan sus credenciales de manera correcta les tiene que salir un resultado similar al siguiente:

```sh
╭ Autograders ╮
│             │
│   Sign In   │
│             │
╰─────────────╯

✔ Email … andres.cv@galileo.edu

✔ Password … **************

✔ User signed in successfully.

Authenticated User:

╔═══════════════╤══════════════════════════╗
║ id            │ 61fcd33c10a10341e78bc4b6 ║
╟───────────────┼──────────────────────────╢
║ email         │ andres.cv@galileo.edu    ║
╟───────────────┼──────────────────────────╢
║ firstName     │ Andrés                   ║
╟───────────────┼──────────────────────────╢
║ lastName      │ Castellanos              ║
╟───────────────┼──────────────────────────╢
║ isVerified    │ true                     ║
╟───────────────┼──────────────────────────╢
║ isDeactivated │ false                    ║
╟───────────────┼──────────────────────────╢
║ isInstructor  │ false                    ║
╟───────────────┼──────────────────────────╢
║ createdAt     │ 2022-02-04T07:18:20.966Z ║
╟───────────────┼──────────────────────────╢
║ updatedAt     │ 2022-02-04T07:24:16.944Z ║
╚═══════════════╧══════════════════════════╝
```

### Olvide Mi Contraseña:

Si por alguna razón ustedes pierden sus credenciales, pueden restaurar su contraseña
al utilizar el siguiente comando:

```sh
autograders --forgot-password
```

Al terminar de ingresar sus datos se les enviará un token a su correo electrónico el resultado se tiene que parecer a esto:

```sh
╭──── Autograders ────╮
│                     │
│   Forgot Password   │
│                     │
╰─────────────────────╯

✔ Email … andres.cv@galileo.edu

✔ Reset password token sent successfully!.
```

Y el correo que les llegará se tiene que ver de la siguiente manera:

![Autograders Forgot](/assets/img/autograders-forgot-password.png)

utilizen este token para cambiar su contraseña.

### Cambiando Mi Contraseña:

Cuando tengan su token para restaurar su contraseña, pueden utilizar el siguiente comando:

```sh
autograders --reset-password
```

Si la información está correcta, verán el siguiente resultado:

```sh
╭─── Autograders ────╮
│                    │
│   Reset Password   │
│                    │
╰────────────────────╯

✔ Email … andres.cv@galileo.edu

✔ Token … ************************

✔ New Password … **************

✔ User password changed succesfully.

Updated User:

╔═══════════════╤══════════════════════════╗
║ id            │ 61fcd33c10a10341e78bc4b6 ║
╟───────────────┼──────────────────────────╢
║ email         │ andres.cv@galileo.edu    ║
╟───────────────┼──────────────────────────╢
║ firstName     │ Andrés                   ║
╟───────────────┼──────────────────────────╢
║ lastName      │ Castellanos              ║
╟───────────────┼──────────────────────────╢
║ isVerified    │ true                     ║
╟───────────────┼──────────────────────────╢
║ isDeactivated │ false                    ║
╟───────────────┼──────────────────────────╢
║ isInstructor  │ false                    ║
╟───────────────┼──────────────────────────╢
║ createdAt     │ 2022-02-04T07:18:20.966Z ║
╟───────────────┼──────────────────────────╢
║ updatedAt     │ 2022-02-04T07:54:01.216Z ║
╚═══════════════╧══════════════════════════╝
```
