
### **Instructivo para Subir Archivos Markdown a GitHub desde Obsidian**

#### **Paso 1: Preparar tus Archivos Markdown en Obsidian**
1. Abre **Obsidian** y asegúrate de que tus notas en formato Markdown (`.md`) están listas.
2. Localiza la carpeta de tu vault donde están guardadas tus notas. Por defecto, estarán en la carpeta del vault de Obsidian que has creado en tu computadora.

---

#### **Paso 2: Crear un Repositorio en GitHub**
1. Ve a tu cuenta de **GitHub** y accede con tu usuario.
2. Haz clic en el botón verde que dice **"New repository"** en tu página principal de GitHub.
3. Llena los siguientes campos:
   - **Repository Name:** Dale un nombre a tu repositorio, por ejemplo, `documentacion-obsidian`.
   - **Description (Opcional):** Puedes añadir una descripción corta de lo que contiene el repositorio.
   - **Visibility:**
     - **Public:** Cualquiera puede ver tu repositorio.
     - **Private:** Solo tú y los colaboradores que invites podrán ver el repositorio.
4. Asegúrate de marcar la casilla que dice **Add a README file** para iniciar el repositorio con un archivo README.
5. Haz clic en **Create repository**.

---

#### **Paso 3: Instalar y Configurar Git en tu Computadora**
Si aún no tienes **Git** instalado en tu computadora, sigue estos pasos:

1. **Instalar Git:**
   - Descarga Git desde su [sitio oficial](https://git-scm.com/) e instálalo siguiendo las instrucciones para tu sistema operativo.

2. **Configurar Git:**
   - Abre una terminal (símbolo del sistema en Windows, o terminal en macOS/Linux) y configura tu nombre de usuario y correo electrónico:
   
     ```bash
     git config --global user.name "TuNombreDeUsuario"
     git config --global user.email "tuemail@example.com"
     ```

---

#### **Paso 4: Clonar el Repositorio de GitHub en tu Computadora**
1. En GitHub, ve a la página del repositorio que acabas de crear.
2. Haz clic en el botón **Code** (de color verde) y copia el enlace del repositorio (usualmente es algo como `https://github.com/usuario/nombre-repositorio.git`). (Hay que seleccionar HTTPS en lugar de SSH)
3. En tu terminal, navega a la carpeta donde quieres clonar el repositorio:
   
   ```bash
   cd /ruta/a/tu/carpeta
   ```

4. Clona el repositorio:

   ```bash
   git clone https://github.com/usuario/nombre-repositorio.git
   ```

   Esto descargará el repositorio en tu computadora.

---

#### **Paso 5: Mover tus Archivos Markdown a la Carpeta del Repositorio**
1. Ve a la carpeta local de tu repositorio clonado en tu computadora.
2. Copia los archivos `.md` que creaste en **Obsidian** y pégalos dentro de la carpeta del repositorio.

---

#### **Paso 6: Subir los Archivos a GitHub**
Ahora que tienes los archivos dentro del repositorio local, puedes subirlos a GitHub:

1. Abre la terminal y navega a la carpeta del repositorio clonado:

   ```bash
   cd /ruta/a/tu/repositorio-clonado
   ```

2. Asegúrate de que los archivos `.md` se han agregado al repositorio:

   ```bash
   git status
   ```

   Verás los archivos listados en "Untracked files".

3. Añade los archivos al área de preparación (staging area):

   ```bash
   git add .
   ```

4. Crea un commit con un mensaje describiendo lo que estás subiendo:

   ```bash
   git commit -m "Añadir archivos Markdown creados en Obsidian"
   ```

5. Finalmente, empuja (push) los cambios a GitHub:

   ```bash
   git push origin main
   ```

```
remote: Permission to CapitanFantastico/MaterialDS2.git denied to g0s0ri0.
fatal: unable to access 'https://github.com/CapitanFantastico/MaterialDS2.git/': The requested URL returned error: 403

remote: Permission to denied to . fatal: unable to access https://github.com/: The requested URL returned error: 403

```
- Ver https://docs.github.com/es/enterprise-cloud@latest/repositories/creating-and-managing-repositories/troubleshooting-cloning-errors
- Ver https://app.aluracursos.com/forum/topico-solucion-al-error-remote-permission-to-denied-to-115036?utm_source=google&utm_medium=cpc&utm_campaign=AL_PRF_Search_Pmax&gad_source=1&gclid=Cj0KCQjw8--2BhCHARIsAF_w1gzgAtUfcL1mb6AxSOrrwDUc7kSRL1sp0HwKL2QpDWsCj71OOvsmyhAaAm_PEALw_wcB 
- https://stackoverflow.com/questions/47465644/github-remote-permission-denied <-

I used to have the same error when i change my user email by **git config --global user.email** and found my solution here: **_Go to: Control Panel -> User Accounts -> Manage your credentials -> Windows Credentials_**

Under **_Generic Credentials_** there are some credentials related to Github, Click on them and click "**_Remove_**".

and when you try to push something, you need to login again. hope this will be helpful for you

> Lo hice, ingresé y borré las credenciales, volví a git push y apareció una ventana para sign in, cuando elegí hacerlo con un código generado pude ver que estaba logueado con otro usuario, así que puse el usuario que necesitaba y todo funcionó correctamente.



---
El error `403: Forbidden` en **Git** suele estar relacionado con problemas de **autenticación** o **permisos** al intentar hacer un `git push`. Esto ocurre cuando Git no puede acceder al repositorio remoto debido a restricciones en tu cuenta o problemas con las credenciales.

Aquí te doy algunos pasos para solucionar el problema:

---

### **Solución 1: Verifica tus credenciales de Git**
Si estás utilizando **HTTPS** para interactuar con GitHub, Git necesita las credenciales correctas (nombre de usuario y token personal de acceso) para autenticarte. 

#### Pasos:
1. **Actualizar credenciales:**
   - Si recientemente cambiaste tu contraseña o eliminaste tu **token de acceso personal** (PAT), necesitarás actualizar tus credenciales. GitHub ya no acepta contraseñas simples, por lo que debes usar un **Personal Access Token (PAT)**.
   - Crea un nuevo **Personal Access Token** en [GitHub Settings](https://github.com/settings/tokens) > **Developer Settings** > **Personal access tokens** > **Generate new token**.
   - Asegúrate de darle los permisos adecuados, como `repo` para acceso completo al repositorio.
  
2. **Actualizar el token en Git localmente:**
   - Una vez creado el token, abre la terminal y ejecuta el siguiente comando para actualizar la URL remota con tu token:

     ```bash
     git remote set-url origin https://<your-token>@github.com/CapitanFantastico/MaterialDS2.git
     ```

   - O, si deseas que Git te pida las credenciales nuevamente:

     ```bash
     git remote set-url origin https://github.com/CapitanFantastico/MaterialDS2.git
     ```

   - Luego, al hacer `git push`, se te pedirá el nombre de usuario y el nuevo token en lugar de la contraseña.

---

### **Solución 2: Revisa los permisos del repositorio**
Si el repositorio es privado o perteneciente a una organización, asegúrate de que tienes permisos de **escritura** o **colaboración** en él.

#### Pasos:
1. **Verificar si tienes permisos de escritura:**
   - Ve a la página del repositorio en GitHub.
   - En la pestaña **Settings** > **Manage Access**, verifica si tu cuenta está agregada como colaborador con permisos de `Write` o `Admin`.

2. **Solicitar acceso:** Si no tienes permisos, pide al administrador del repositorio que te agregue como colaborador.

---

### **Solución 3: Autenticación por SSH**
Si prefieres no usar tokens de acceso personal con HTTPS, puedes usar **autenticación SSH**.

#### Pasos:
1. **Generar clave SSH:**
   - Si no tienes una clave SSH, genera una nueva clave:
     ```bash
     ssh-keygen -t rsa -b 4096 -C "tu-email@example.com"
     ```
   - Sigue las instrucciones y guarda la clave en la ubicación predeterminada.

2. **Agregar la clave SSH a tu cuenta de GitHub:**
   - Copia la clave pública:
     ```bash
     cat ~/.ssh/id_rsa.pub
     ```
   - Ve a [GitHub SSH Settings](https://github.com/settings/keys) y agrega tu clave pública.

3. **Cambiar la URL remota a SSH:**
   - Cambia la URL remota en tu repositorio local:
     ```bash
     git remote set-url origin git@github.com:CapitanFantastico/MaterialDS2.git
     ```

4. **Intenta hacer `git push` nuevamente:**
   ```bash
   git push origin main
   ```

---

### **Solución 4: Verifica si GitHub está bloqueando el acceso**
A veces, el acceso a GitHub puede estar bloqueado por un firewall o proxy.

#### Pasos:
- **Intenta desde otro entorno de red** (por ejemplo, en casa o en otra red).
- Si estás usando una red corporativa o universitaria, asegúrate de que GitHub no esté bloqueado o utiliza una VPN.

---

### **Solución 5: Verificar la configuración de 2FA (Autenticación de Dos Factores)**
Si tienes habilitada la **autenticación de dos factores (2FA)** en GitHub, es obligatorio utilizar **tokens de acceso personal** o **SSH** en lugar de contraseñas tradicionales.

#### Pasos:
- Revisa que estás usando un **Personal Access Token** (PAT) o SSH en lugar de tu contraseña, ya que las contraseñas no funcionan con 2FA habilitado.

---

### **Resumen**
- Verifica que estás usando **un Personal Access Token** (no una contraseña).
- Asegúrate de tener **permisos de escritura** en el repositorio.
- Considera usar **SSH** como alternativa si prefieres no usar tokens.
  
Cualquier de estos pasos debería resolver el error `403` al hacer `git push`.

---

#### **Paso 7: Verifica los Archivos en GitHub**
1. Vuelve a la página de tu repositorio en **GitHub**.
2. Verás los archivos `.md` subidos en la lista de archivos del repositorio.

---

### **Conclusión**
¡Listo! Has subido tus archivos Markdown de Obsidian a GitHub. Ahora puedes compartir tu documentación con otros o seguir trabajando en el repositorio con control de versiones. Recuerda que cualquier cambio que hagas en tus archivos locales deberás volver a **commit** y **push** para reflejar los cambios en GitHub.

---

### **Quick setup** — if you’ve done this kind of thing before

Get started by [creating a new file](https://github.com/CapitanFantastico/MaterialDS2/new/main) or [uploading an existing file](https://github.com/CapitanFantastico/MaterialDS2/upload). We recommend every repository include a [README](https://github.com/CapitanFantastico/MaterialDS2/new/main?readme=1), [LICENSE](https://github.com/CapitanFantastico/MaterialDS2/new/main?filename=LICENSE.md), and [.gitignore](https://github.com/CapitanFantastico/MaterialDS2/new/main?filename=.gitignore).

### …or create a new repository on the command line

echo "# MaterialDS2" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/CapitanFantastico/MaterialDS2.git
git push -u origin main

### …or push an existing repository from the command line

git remote add origin https://github.com/CapitanFantastico/MaterialDS2.git
git branch -M main
git push -u origin main


---

Cuando intentas hacer un **push** en GitHub y aparece la ventana "Connect to GitHub" con las opciones de autenticación como **Browser/Device** y **Token**, y los botones **Sign in with your browser** y **Sign in with a code**, estás utilizando un flujo moderno de autenticación en GitHub que refuerza la seguridad de las conexiones. Aquí te explico cómo conectarte y hacer el push en GitHub utilizando los métodos más comunes.

### Opciones de Conexión a GitHub

#### 1. **Sign in with your browser**
Esta es la opción más sencilla y recomendada por GitHub si prefieres hacer login directamente desde tu navegador.

**Pasos:**
1. Selecciona **Sign in with your browser**.
2. Se abrirá tu navegador predeterminado y serás redirigido a la página de inicio de sesión de GitHub.
3. Inicia sesión con tu cuenta de GitHub (correo electrónico/usuario y contraseña).
4. Una vez que te hayas autenticado en el navegador, GitHub te mostrará un mensaje de éxito y podrás regresar a tu terminal o editor de código.
5. Vuelve a la ventana donde estabas intentando hacer el push, y GitHub debería estar conectado. Ahora puedes ejecutar el comando `git push`.

#### 2. **Sign in with a code**
Esta opción te permite autenticarte usando un código que puedes ingresar en un dispositivo diferente.

**Pasos:**
1. Selecciona **Sign in with a code**.
2. GitHub te proporcionará un código de autenticación único.
3. Ve al navegador y accede a [https://github.com/login/device](https://github.com/login/device).
4. Ingresa el código proporcionado en la ventana que aparece.
5. Después de ingresar el código, GitHub te pedirá que inicies sesión.
6. Una vez autenticado, GitHub te redirigirá con un mensaje de éxito, y podrás continuar con el push.

#### 3. **Token**
Esta opción te permite autenticarte utilizando un **Token de Acceso Personal (PAT)** en lugar de tu usuario y contraseña. Desde 2021, GitHub dejó de aceptar contraseñas tradicionales en la terminal y recomienda el uso de tokens para la autenticación.

**Pasos:**
1. Si no tienes un **Token de Acceso Personal (PAT)**, ve a GitHub y sigue estos pasos:
   - Inicia sesión en [GitHub](https://github.com).
   - Ve a **Settings** (Configuración) > **Developer settings** > **Personal access tokens** > **Tokens (classic)**.
   - Haz clic en **Generate new token**.
   - Selecciona los permisos que necesitas para tu repositorio (por ejemplo, `repo` para acceder y hacer push a repositorios privados o públicos).
   - Copia el token generado (no podrás verlo de nuevo después de cerrar la página).
   
2. En la ventana de "Connect to GitHub", selecciona la opción **Token**.
3. Introduce el **Token de Acceso Personal** que generaste en GitHub.
4. El token autenticará tu conexión y podrás ejecutar el comando `git push`.

#### 4. **Browser/Device**
Este método puede ser una variación del flujo de autenticación basado en dispositivos o navegadores, permitiéndote ingresar a GitHub en un dispositivo diferente (teléfono, tablet) o desde un navegador.

### Cómo Hacer el Push a GitHub

Después de autenticarte usando cualquiera de las opciones anteriores, sigue estos pasos para hacer **push** a tu repositorio:

1. **Agregar los archivos y hacer commit** (si no lo has hecho ya):
   ```bash
   git add .
   git commit -m "Mensaje de commit"
   ```

2. **Hacer el push al repositorio remoto**:
   ```bash
   git push origin main
   ```

   - Si el branch principal de tu repositorio se llama algo diferente, como `master` o algún otro nombre, asegúrate de sustituir `main` por el nombre correcto.
   - Si es la primera vez que haces un push a un repositorio remoto o a un branch nuevo, puede que necesites incluir la opción `-u`:
     ```bash
     git push -u origin main
     ```

### Notas Adicionales:
- Si estás utilizando **Visual Studio Code** (VSCode), este suele manejar la autenticación a través de su integración con GitHub, y puedes utilizar el flujo de autenticación desde allí también.
- **SSH**: Si prefieres una autenticación más persistente y segura, puedes configurar GitHub para autenticación mediante **SSH keys**. Esto te permitirá hacer push sin ingresar credenciales cada vez.

### Conclusión
Puedes autenticarse con GitHub mediante **Sign in with your browser** o **Sign in with a code** si prefieres autenticación por navegador, o puedes usar un **Token de Acceso Personal (PAT)** para conectarte directamente desde la terminal. Cualquiera de estos métodos te permitirá realizar el **push** de manera segura y sencilla.
