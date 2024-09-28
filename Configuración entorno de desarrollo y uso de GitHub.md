Configurar un ambiente de desarrollo con Visual Studio Code (VSCode), GitHub y Python desde cero implica varios pasos. A continuación, te guiaré a través del proceso:

### Paso 1: Instalar Python

1. **Descargar Python**:
   - Ve al sitio web oficial de Python: [python.org](https://www.python.org/downloads/).
   - Descarga la última versión de Python para tu sistema operativo (Windows, macOS, Linux).

2. **Instalar Python**:
   - Ejecuta el instalador y asegúrate de marcar la opción "Add Python to PATH" antes de hacer clic en "Install Now".
   - Verifica la instalación abriendo una terminal (Command Prompt en Windows, Terminal en macOS/Linux) y ejecutando:
     ```
     python --version
     ```

### Paso 2: Instalar Visual Studio Code

1. **Descargar VSCode**:
   - Ve al sitio web oficial de Visual Studio Code: [code.visualstudio.com](https://code.visualstudio.com/).
   - Descarga la versión adecuada para tu sistema operativo.

2. **Instalar VSCode**:
   - Ejecuta el instalador y sigue las instrucciones en pantalla.

### Paso 3: Instalar Git

1. **Descargar Git**:
   - Ve al sitio web oficial de Git: [git-scm.com](https://git-scm.com/downloads).
   - Descarga la versión adecuada para tu sistema operativo.

2. **Instalar Git**:
   - Ejecuta el instalador y sigue las instrucciones. Asegúrate de seleccionar las opciones que te permitan usar Git desde la línea de comandos.

3. **Verificar la instalación**:
   - Abre una terminal y ejecuta:
     ```
     git --version
     ```

### Paso 4: Configurar GitHub

1. **Crear una cuenta en GitHub**:
   - Ve a [github.com](https://github.com/) y crea una cuenta si no tienes una.

2. **Configurar Git**:
   - Abre una terminal y configura tu nombre de usuario y correo electrónico de GitHub:
     ```
     git config --global user.name "Tu Nombre"
     git config --global user.email "tuemail@example.com"
     ```

### Paso 5: Instalar la Extensión de Python en VSCode

1. **Abrir VSCode**:
   - Inicia Visual Studio Code.

2. **Instalar la extensión de Python**:
   - Ve a la pestaña de extensiones (icono de cuadrado en la barra lateral izquierda o presiona `Ctrl+Shift+X`).
   - Busca "Python" y selecciona la extensión oficial de Microsoft. Haz clic en "Instalar".

### Paso 6: Crear un Proyecto de Python

1. **Crear un nuevo directorio**:
   - Abre una terminal y crea un nuevo directorio para tu proyecto:
     ```
     mkdir mi-proyecto-python
     cd mi-proyecto-python
     ```

2. **Crear un entorno virtual (opcional pero recomendado)**:
   - Crea un entorno virtual para gestionar las dependencias:
     ```
     python -m venv venv
     ```
   - Activa el entorno virtual:
     - En Windows:
       ```
       venv\Scripts\activate
       ```
     - En macOS/Linux:
       ```
       source venv/bin/activate
       ```

3. **Crear un archivo Python**:
   - Abre VSCode en el directorio del proyecto:
     ```
     code .
     ```
   - Crea un nuevo archivo llamado `main.py` y escribe un simple programa:
     ```python
     print("Hola, mundo!")
     ```

### Paso 7: Usar Git para Control de Versiones

1. **Inicializar un repositorio Git**:
   - En la terminal, inicializa un repositorio Git:
     ```
     git init
     ```

2. **Agregar archivos al repositorio**:
   - Agrega el archivo `main.py` al repositorio:
     ```
     git add main.py
     ```

3. **Hacer un commit**:
   - Realiza un commit de tus cambios:
     ```
     git commit -m "Primer commit: agregar main.py"
     ```

4. **Crear un repositorio en GitHub**:
   - Ve a GitHub y crea un nuevo repositorio.

5. **Conectar tu repositorio local con GitHub**:
   - En la terminal, agrega el repositorio remoto:
     ```
     git remote add origin https://github.com/tuusuario/nombre-del-repositorio.git
     ```

6. **Subir tus cambios a GitHub**:
   - Envía tus cambios al repositorio remoto:
     ```
     git push -u origin master
     ```

### Resumen
Ahora tienes un ambiente de desarrollo configurado con VSCode, GitHub y Python. Puedes comenzar a desarrollar tus proyectos de Python, gestionar el control de versiones con Git y colaborar en GitHub. ¡Buena suerte con tu programación!

---

Aquí tienes una guía paso a paso para hacer un fork de un repositorio en GitHub, clonarlo en tu PC, trabajar en él y luego hacer un pull request:

### Paso 1: Hacer un Fork del Repositorio

1. **Iniciar sesión en GitHub**:
   - Ve a [github.com](https://github.com/) e inicia sesión en tu cuenta.

2. **Encontrar el Repositorio**:
   - Navega al repositorio que deseas forkear.

3. **Hacer un Fork**:
   - Haz clic en el botón "Fork" en la parte superior derecha de la página del repositorio. Esto creará una copia del repositorio en tu cuenta de GitHub.

### Paso 2: Clonar el Repositorio Forkeado

1. **Clonar el Repositorio**:
   - Ve a tu perfil de GitHub y abre el repositorio que acabas de forkear.
   - Haz clic en el botón "Code" y copia la URL del repositorio (puede ser HTTPS o SSH).
   - Abre una terminal en tu PC y navega al directorio donde deseas clonar el repositorio. Luego ejecuta:
     ```
     git clone https://github.com/tuusuario/nombre-del-repositorio.git
     ```
   - Reemplaza `tuusuario` y `nombre-del-repositorio` con tu nombre de usuario y el nombre del repositorio.

2. **Navegar al Directorio del Repositorio**:
   - Cambia al directorio del repositorio clonado:
     ```
     cd nombre-del-repositorio
     ```

### Paso 3: Crear una Nueva Rama para Trabajar

1. **Crear y Cambiar a una Nueva Rama**:
   - Es recomendable trabajar en una nueva rama para tus cambios. Crea una nueva rama y cámbiate a ella:
     ```
     git checkout -b nombre-de-tu-rama
     ```
   - Reemplaza `nombre-de-tu-rama` con un nombre descriptivo para tu rama.

### Paso 4: Hacer Cambios y Confirmarlos

1. **Realizar Cambios**:
   - Abre el proyecto en VSCode y realiza los cambios que deseas.

2. **Agregar y Confirmar Cambios**:
   - Después de realizar los cambios, guarda los archivos y vuelve a la terminal. Agrega los cambios:
     ```
     git add .
     ```
   - Luego, haz un commit de tus cambios:
     ```
     git commit -m "Descripción de los cambios realizados"
     ```

### Paso 5: Subir los Cambios a tu Fork en GitHub

1. **Subir la Rama a GitHub**:
   - Envía tu rama con los cambios a tu repositorio fork en GitHub:
     ```
     git push origin nombre-de-tu-rama
     ```

### Paso 6: Hacer un Pull Request

1. **Crear un Pull Request**:
   - Ve a tu repositorio en GitHub.
   - Verás un mensaje que dice "Compare & pull request" después de haber subido tu rama. Haz clic en ese botón.
   - Completa el formulario para el pull request, proporcionando un título y una descripción de los cambios que realizaste.

2. **Enviar el Pull Request**:
   - Haz clic en el botón "Create pull request" para enviar tu pull request al repositorio original.

### Resumen
Ahora has hecho un fork de un repositorio, lo has clonado en tu PC, has realizado cambios en una nueva rama y has enviado un pull request. El propietario del repositorio original podrá revisar tus cambios y decidir si los acepta. ¡Buena suerte con tu contribución!

---

El flujo para un **code review** (revisión de código) es un proceso estructurado que permite a los desarrolladores revisar y mejorar el código antes de que se integre en la base de código principal. A continuación, se presenta un flujo típico para llevar a cabo un code review:

### Flujo de Code Review

1. **Preparación del Código**:
   - **Desarrollo**: El desarrollador trabaja en una nueva característica o corrección de errores en una rama separada.
   - **Pruebas**: Antes de solicitar una revisión, el desarrollador debe asegurarse de que el código esté probado y funcione correctamente. Esto incluye pruebas unitarias y funcionales.

2. **Crear un Pull Request (PR)**:
   - Una vez que el desarrollador ha terminado de implementar los cambios, crea un pull request en la plataforma de control de versiones (como GitHub, GitLab, Bitbucket).
   - El PR debe incluir una descripción clara de los cambios realizados, el propósito de los mismos y cualquier contexto relevante.

3. **Asignar Revisores**:
   - El desarrollador asigna revisores al PR. Esto puede incluir compañeros de equipo, líderes técnicos o cualquier persona con experiencia en el área del código que se está revisando.

4. **Revisión del Código**:
   - Los revisores reciben una notificación del PR y comienzan a revisar el código.
   - Durante la revisión, los revisores deben:
     - Leer el código y entender la lógica.
     - Verificar que se sigan las convenciones de codificación y los estándares del equipo.
     - Comprobar que el código esté bien documentado y que las pruebas sean adecuadas.
     - Probar el código en su entorno local si es necesario.

5. **Comentarios y Sugerencias**:
   - Los revisores dejan comentarios en el PR, señalando áreas de mejora, errores o sugerencias.
   - Es importante que los comentarios sean constructivos y específicos, proporcionando ejemplos cuando sea posible.

6. **Realizar Cambios**:
   - El desarrollador revisa los comentarios y realiza los cambios necesarios en el código.
   - Después de realizar los cambios, el desarrollador actualiza el PR con los nuevos commits.

7. **Revisión Adicional**:
   - Los revisores revisan nuevamente el código modificado para asegurarse de que se hayan abordado sus comentarios.
   - Este proceso puede repetirse varias veces hasta que todos estén satisfechos con los cambios.

8. **Aprobación del Pull Request**:
   - Una vez que los revisores están satisfechos con el código, aprueban el PR.
   - Dependiendo de las políticas del equipo, puede ser necesario que al menos un revisor apruebe el PR antes de que se pueda fusionar.

9. **Fusión del Código**:
   - El desarrollador o un miembro del equipo con permisos fusiona el PR en la rama principal (por ejemplo, `main` o `master`).
   - Asegúrate de que se realicen pruebas adicionales después de la fusión para verificar que todo funcione correctamente.

10. **Cierre del Pull Request**:
    - Una vez fusionado, el PR se cierra automáticamente (o manualmente, si es necesario).
    - El desarrollador puede eliminar la rama de trabajo si ya no es necesaria.

11. **Reflexión y Mejora Continua**:
    - Después de completar el proceso de revisión, el equipo puede reflexionar sobre el flujo de trabajo y discutir posibles mejoras en el proceso de revisión de código.

### Resumen
El flujo de code review es un proceso colaborativo que ayuda a mejorar la calidad del código y fomenta la comunicación entre los miembros del equipo. Al seguir este flujo, se pueden identificar y corregir problemas antes de que el código se integre en la base de código principal, lo que resulta en un software más robusto y mantenible.


---

Aquí tienes un ejemplo de cómo se llevaría a cabo un code review en GitHub, incluyendo los pasos y las interacciones típicas que podrías encontrar en un pull request (PR).

### Ejemplo de Code Review en GitHub

#### 1. Crear un Pull Request

Supongamos que un desarrollador, llamado **Juan**, ha trabajado en una nueva característica en una rama llamada `feature/nueva-funcionalidad`. Después de completar su trabajo, crea un pull request en GitHub.

- **Título del PR**: "Agregar nueva funcionalidad para el cálculo de impuestos"
- **Descripción del PR**:
  ```
  Este PR agrega una nueva función para calcular impuestos sobre las ventas. 
  - Se ha añadido la función `calcular_impuesto` en el archivo `impuestos.py`.
  - Se han incluido pruebas unitarias en `test_impuestos.py`.
  ```

#### 2. Asignar Revisores

Juan asigna a dos revisores: **María** y **Carlos**. También etiqueta el PR con `review needed`.

#### 3. Revisión del Código

María y Carlos reciben una notificación del PR y comienzan a revisarlo. Aquí hay un ejemplo de cómo podrían interactuar:

- **María**:
  - **Comentario en la línea 15 de `impuestos.py`**:
    ```
    Me gusta la lógica de esta función, pero ¿podrías agregar un comentario que explique cómo se calcula el impuesto?
    ```

- **Carlos**:
  - **Comentario en la línea 22 de `test_impuestos.py`**:
    ```
    Las pruebas son buenas, pero creo que deberías agregar un caso de prueba para cuando el monto es cero. Esto asegurará que la función maneje correctamente ese caso.
    ```

#### 4. Realizar Cambios

Juan revisa los comentarios de María y Carlos. Decide hacer los siguientes cambios:

- Agrega un comentario en la función `calcular_impuesto`.
- Añade un caso de prueba para el monto cero en `test_impuestos.py`.

Después de realizar los cambios, Juan actualiza el PR con nuevos commits.

#### 5. Revisión Adicional

María y Carlos reciben una notificación de que el PR ha sido actualizado. Revisan nuevamente los cambios:

- **María**:
  - **Comentario**:
    ```
    ¡Perfecto! El comentario es claro ahora. Gracias por la actualización.
    ```

- **Carlos**:
  - **Comentario**:
    ```
    Las pruebas se ven bien. Todo parece estar en orden. ¡Buen trabajo!
    ```

#### 6. Aprobación del Pull Request

Una vez que ambos revisores están satisfechos, hacen clic en el botón "Approve" para aprobar el PR.

#### 7. Fusión del Código

Juan, después de recibir las aprobaciones, fusiona el PR en la rama principal (`main`). GitHub automáticamente cierra el PR y muestra un mensaje de éxito.

#### 8. Cierre del Pull Request

Juan puede optar por eliminar la rama `feature/nueva-funcionalidad` si ya no es necesaria.

### Resumen

Este es un ejemplo típico de un proceso de code review en GitHub. Incluye la creación de un pull request, la asignación de revisores, la revisión del código con comentarios, la realización de cambios, la aprobación del PR y la fusión del código. Este proceso ayuda a mejorar la calidad del código y fomenta la colaboración entre los miembros del equipo.

---

Aquí tienes un ejemplo de cómo funciona **GitHub Actions** para automatizar el proceso de integración continua (CI) y entrega continua (CD) en un proyecto de software. Este ejemplo incluye la configuración de un flujo de trabajo que ejecuta pruebas cada vez que se realiza un push a la rama principal.

### Ejemplo de GitHub Actions

#### 1. Crear un Archivo de Flujo de Trabajo

Para comenzar a usar GitHub Actions, debes crear un archivo de flujo de trabajo en tu repositorio. Este archivo se coloca en el directorio `.github/workflows/`. Vamos a crear un flujo de trabajo llamado `ci.yml`.

#### 2. Contenido del Archivo `ci.yml`

Aquí tienes un ejemplo de cómo podría verse el archivo `ci.yml`:

```yaml
name: CI

on:
  push:
    branches:
      - main
  pull_request:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v2

      - name: Set up Python
        uses: actions/setup-python@v2
        with:
          python-version: '3.8'

      - name: Install dependencies
        run: |
          python -m pip install --upgrade pip
          pip install -r requirements.txt

      - name: Run tests
        run: |
          pytest
```

#### 3. Desglose del Archivo

- **name**: Define el nombre del flujo de trabajo, en este caso, "CI".
  
- **on**: Especifica los eventos que activan el flujo de trabajo. En este caso, se activa en:
  - `push` a la rama `main`.
  - `pull_request` hacia la rama `main`.

- **jobs**: Define los trabajos que se ejecutarán en el flujo de trabajo. Aquí hay un trabajo llamado `build`.

- **runs-on**: Especifica el sistema operativo en el que se ejecutará el trabajo. En este caso, se utiliza `ubuntu-latest`.

- **steps**: Define los pasos que se ejecutarán en el trabajo:
  1. **Checkout code**: Utiliza la acción `actions/checkout` para obtener el código del repositorio.
  2. **Set up Python**: Utiliza la acción `actions/setup-python` para configurar Python 3.8.
  3. **Install dependencies**: Instala las dependencias del proyecto utilizando `pip`.
  4. **Run tests**: Ejecuta las pruebas utilizando `pytest`.

#### 4. Activar el Flujo de Trabajo

Una vez que hayas creado y guardado el archivo `ci.yml` en tu repositorio, GitHub Actions se activará automáticamente en los siguientes eventos:

- Cuando realices un push a la rama `main`.
- Cuando se abra un pull request hacia la rama `main`.

#### 5. Ver Resultados

Puedes ver el estado del flujo de trabajo en la pestaña "Actions" de tu repositorio en GitHub. Allí podrás ver si el flujo de trabajo se ejecutó correctamente o si hubo errores en alguna de las etapas.

### Resumen

Este ejemplo muestra cómo configurar un flujo de trabajo básico de GitHub Actions para ejecutar pruebas automáticamente cada vez que se realiza un push o un pull request en la rama principal. GitHub Actions permite automatizar tareas repetitivas y mejorar la eficiencia del desarrollo de software.


---

Aquí tienes un ejemplo de un proyecto en GitHub que podrías crear para gestionar una aplicación simple de "Lista de Tareas" (To-Do List) utilizando **HTML**, **CSS** y **JavaScript**. Este proyecto incluye la estructura básica y algunos archivos esenciales.

### Ejemplo de Proyecto: To-Do List

#### Estructura del Proyecto

```
to-do-list/
├── index.html
├── styles.css
└── script.js
```

#### 1. Archivo `index.html`

Este archivo contiene la estructura HTML de la aplicación.

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lista de Tareas</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <h1>Lista de Tareas</h1>
        <input type="text" id="taskInput" placeholder="Agregar nueva tarea...">
        <button id="addTaskButton">Agregar</button>
        <ul id="taskList"></ul>
    </div>
    <script src="script.js"></script>
</body>
</html>
```

#### 2. Archivo `styles.css`

Este archivo contiene los estilos CSS para la aplicación.

```css
body {
    font-family: Arial, sans-serif;
    background-color: #f4f4f4;
    margin: 0;
    padding: 0;
}

.container {
    width: 300px;
    margin: 50px auto;
    padding: 20px;
    background: white;
    border-radius: 5px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

h1 {
    text-align: center;
}

input {
    width: calc(100% - 60px);
    padding: 10px;
    margin-right: 10px;
}

button {
    padding: 10px;
}

ul {
    list-style-type: none;
    padding: 0;
}

li {
    padding: 10px;
    border-bottom: 1px solid #ddd;
}
```

#### 3. Archivo `script.js`

Este archivo contiene la lógica JavaScript para agregar y mostrar tareas.

```javascript
document.getElementById('addTaskButton').addEventListener('click', function() {
    const taskInput = document.getElementById('taskInput');
    const taskText = taskInput.value;

    if (taskText) {
        const li = document.createElement('li');
        li.textContent = taskText;
        document.getElementById('taskList').appendChild(li);
        taskInput.value = '';
    }
});
```

### 4. Crear el Repositorio en GitHub

1. **Crear un nuevo repositorio** en GitHub llamado `to-do-list`.
2. **Subir los archivos** `index.html`, `styles.css` y `script.js` al repositorio.
3. **Agregar un README.md** para describir el proyecto. Aquí tienes un ejemplo de contenido para el README:

```markdown
# Lista de Tareas

Este es un proyecto simple de una aplicación de lista de tareas (To-Do List) utilizando HTML, CSS y JavaScript.

## Características

- Agregar nuevas tareas.
- Visualizar la lista de tareas.

## Cómo usar

1. Clona el repositorio.
2. Abre el archivo `index.html` en tu navegador.
3. Agrega tareas utilizando el campo de entrada y el botón "Agregar".
```

### Resumen

Este ejemplo de proyecto en GitHub muestra cómo crear una aplicación simple de lista de tareas. Incluye la estructura del proyecto, el código HTML, CSS y JavaScript, y cómo documentar el proyecto en un archivo README. Puedes expandir este proyecto agregando características como eliminar tareas, marcar tareas como completadas, o almacenar tareas en el almacenamiento local del navegador.

---

**GitHub Projects** es una herramienta de gestión de proyectos integrada dentro de GitHub que permite a los equipos organizar, planificar y seguir el progreso de su trabajo de desarrollo de software. GitHub Projects está diseñado para ser flexible y se puede adaptar a diferentes flujos de trabajo, como kanban, listas de tareas, o planificación ágil.

### ¿Cómo funciona GitHub Projects?

GitHub Projects proporciona un tablero visual que te permite organizar tareas y seguir el progreso de tu trabajo. Aquí te explico sus componentes y cómo funciona:

### 1. **Tableros de Proyectos (Project Boards)**

Un tablero de proyecto es un espacio donde puedes ver y gestionar las tareas de tu proyecto. Cada tablero está compuesto por columnas y tarjetas:

- **Columnas (Columns):** Representan estados del trabajo, como "To Do", "In Progress", y "Done". Puedes personalizarlas para que se adapten a tu flujo de trabajo.

- **Tarjetas (Cards):** Cada tarea o trabajo pendiente se representa como una tarjeta. Las tarjetas pueden ser issues, pull requests, o notas simples. Puedes arrastrar y soltar tarjetas entre columnas para indicar su progreso.

### 2. **Creación de un Proyecto**

Para crear un proyecto en GitHub:
1. Ve a la pestaña **"Projects"** en tu repositorio, organización, o perfil personal.
2. Haz clic en **"New project"**.
3. Asigna un nombre al proyecto y selecciona la plantilla que prefieras (por ejemplo, un tablero Kanban).
4. Configura el proyecto con las columnas que necesites y personaliza el flujo de trabajo.

### 3. **Tarjetas (Cards)**

Las tarjetas son los elementos fundamentales en un proyecto. Puedes crear tarjetas directamente en el tablero o convertir issues o pull requests existentes en tarjetas:

- **Crear una nueva tarjeta:**
  - Haz clic en **"+"** en la columna deseada para agregar una nueva tarjeta.
  - Puedes crear una tarjeta rápida (nota) o vincularla a un issue o pull request.
  
- **Convertir un issue en tarjeta:**
  - Arrastra un issue desde la lista de issues al tablero, o selecciona **"Add cards"** en el tablero y elige un issue de la lista.

### 4. **Automatización**

GitHub Projects permite automatizar ciertas acciones para que el flujo de trabajo sea más eficiente:
- **Automatizaciones de columnas:** Puedes configurar reglas para que las tarjetas se muevan automáticamente entre columnas cuando se realizan ciertas acciones, como cuando un pull request es cerrado o un issue es resuelto.
- **GitHub Actions:** Puedes integrar GitHub Actions para realizar tareas automatizadas que impactan en el tablero de proyectos, como mover tarjetas basadas en cambios en el código.

### 5. **Filtros y vistas personalizadas**

Puedes filtrar las tarjetas en un tablero por diferentes criterios, como etiquetas, responsables, o estado. Esto te permite centrarte en partes específicas del proyecto.

### 6. **Colaboración y seguimiento**

GitHub Projects es colaborativo, lo que significa que todos los miembros de un equipo pueden ver y actualizar el tablero. Esto permite una visibilidad clara del progreso y facilita la colaboración en equipo.

- **Asignar tareas:** Puedes asignar tarjetas a miembros del equipo para que queden claros los responsables de cada tarea.
- **Comentarios y discusiones:** En las tarjetas que están vinculadas a issues o pull requests, puedes ver y participar en discusiones directamente desde el tablero.
  
### 7. **Integración con GitHub Issues y Pull Requests**

Una de las principales ventajas de GitHub Projects es su integración estrecha con GitHub Issues y Pull Requests:
- **Issues:** Puedes crear y gestionar issues directamente desde el tablero, lo que facilita la gestión de tareas y bugs.
- **Pull Requests:** Los pull requests también pueden gestionarse desde el tablero, permitiéndote ver qué cambios están en progreso, qué revisiones son necesarias, y qué cambios se han fusionado.

### 8. **Vistas avanzadas: GitHub Projects (Beta)**

GitHub ha lanzado una nueva versión de Projects (en fase Beta), que ofrece vistas más avanzadas y personalizadas, como:
- **Vistas de tabla:** Puedes ver y editar las tareas en un formato de tabla, lo que es útil para un seguimiento más detallado y personalizable.
- **Filtros avanzados:** Con nuevas capacidades de filtrado, puedes crear vistas personalizadas según tus necesidades.
  
### 9. **Ejemplo de uso típico:**

Imagina que estás desarrollando una aplicación web. Tu flujo de trabajo en GitHub Projects podría verse así:
1. **Planificación**: Creas un nuevo proyecto y lo configuras con columnas como "Backlog", "In Progress", "Review", y "Done".
2. **Organización**: Añades issues al tablero que representen las funcionalidades, mejoras y bugs que necesitas abordar.
3. **Desarrollo**: A medida que tú y tu equipo trabajan en las tareas, mueven las tarjetas de una columna a otra, reflejando el estado actual del trabajo.
4. **Revisión y finalización**: Los pull requests pasan por la columna de "Review", y una vez aprobados y fusionados, las tarjetas se mueven automáticamente a "Done".

### 10. **Monitoreo y mejora continua**

Usando GitHub Projects, puedes ver el progreso del proyecto en tiempo real, identificar bloqueos, y ajustar el plan según sea necesario. Es una herramienta eficaz para mantener el trabajo organizado y asegurarte de que todos en el equipo estén alineados.

### Conclusión

GitHub Projects es una herramienta poderosa que te permite gestionar tu trabajo de desarrollo de software directamente en GitHub, manteniendo todo en un solo lugar. Su flexibilidad y capacidad de integración con GitHub Issues y Pull Requests la convierte en una excelente opción para equipos de todos los tamaños, desde proyectos individuales hasta grandes equipos colaborativos.

---

La gestión y ejecución de un proyecto de desarrollo de software con un equipo de 5 desarrolladores requiere un flujo de trabajo bien definido para asegurar que el proyecto se desarrolle de manera eficiente y colaborativa. Aquí te propongo un flujo adecuado que puedes ajustar según las necesidades específicas del proyecto y del equipo:

### 1. **Planificación Inicial**

#### a) Definición de Requisitos:
   - Reúne al equipo con el Product Owner (si lo hay) o con los stakeholders para definir los requisitos del proyecto.
   - Documenta los requisitos funcionales y no funcionales en un documento de especificaciones o un backlog de producto.

#### b) Definición de Roles y Responsabilidades:
   - Asigna roles dentro del equipo, como líder técnico, responsable de la integración continua, responsable de las pruebas, etc.
   - Define claramente quién será responsable de qué parte del proyecto.

#### c) Selección de Herramientas:
   - Decide qué herramientas usarás para la gestión de proyectos (por ejemplo, GitHub Projects, Jira, Trello), control de versiones (Git), integración continua (Jenkins, GitHub Actions), y comunicación (Slack, Microsoft Teams).

#### d) Creación del Backlog:
   - Divide los requisitos en tareas (issues) manejables y priorízalos en un backlog.
   - Cada tarea debe ser clara, con criterios de aceptación bien definidos.

### 2. **Configuración del Entorno de Desarrollo**

#### a) Configuración del Repositorio:
   - Crea un repositorio Git en una plataforma como GitHub o GitLab.
   - Configura ramas estándar: `main` (o `master`), `develop`, y ramas feature específicas (`feature/nombre-funcionalidad`).

#### b) Configuración de la Integración Continua (CI/CD):
   - Configura pipelines de CI/CD para automatizar las pruebas y despliegues.
   - Asegúrate de que cada commit o pull request desencadene la ejecución de tests automáticos.

#### c) Establecimiento de Normas de Codificación:
   - Define y documenta las normas de codificación (por ejemplo, estilo de código, comentarios, estructura de los commits).
   - Considera usar [[Linter]]s y herramientas de análisis de código para garantizar la calidad del código.

### 3. **Desarrollo Iterativo**

#### a) Sprint Planning:
   - Organiza el trabajo en sprints (generalmente de 1 a 2 semanas).
   - Al inicio de cada sprint, el equipo se reúne para planificar qué tareas del backlog se trabajarán.

#### b) Desarrollo de Funcionalidades:
   - Cada desarrollador crea una rama para trabajar en una funcionalidad específica.
   - Desarrolla y prueba localmente antes de hacer un commit y push a la rama remota.

#### c) Pull Requests y Revisiones de Código:
   - Una vez que una funcionalidad está lista, el desarrollador abre un pull request (PR).
   - Al menos un desarrollador del equipo revisa el código, asegurándose de que cumple con las normas establecidas y que funciona según lo esperado.
   - Si se aprueba, se fusiona la rama en `develop` (o directamente en `main` si la funcionalidad está lista para producción).

### 4. **Pruebas y Control de Calidad**

#### a) Pruebas Unitarias y de Integración:
   - Los desarrolladores escriben pruebas unitarias y de integración junto con el código.
   - Las pruebas se ejecutan automáticamente en el pipeline de CI/CD para garantizar que no se rompan funcionalidades existentes.

#### b) Pruebas de Calidad (QA):
   - Si el equipo cuenta con un QA, este realiza pruebas manuales o automatizadas adicionales en un entorno staging.
   - Reporta cualquier bug en el backlog para que los desarrolladores lo corrijan.

### 5. **Integración Continua y Despliegue**

#### a) Integración Continua:
   - Las ramas se fusionan regularmente a `develop` para integrar las funcionalidades con el trabajo del resto del equipo.
   - Las pruebas automáticas verifican la estabilidad del código.

#### b) Despliegue a Entornos de Prueba:
   - Una vez que una funcionalidad ha pasado todas las pruebas en `develop`, se despliega a un entorno staging para pruebas más exhaustivas.

#### c) Despliegue a Producción:
   - Cuando todas las funcionalidades programadas para un sprint han sido validadas, se realiza el despliegue a producción desde la rama `main`.
   - El despliegue puede ser automático o manual, dependiendo del flujo de CI/CD configurado.

### 6. **Monitoreo y Retroalimentación**

#### a) Monitoreo en Producción:
   - Implementa herramientas de monitoreo para seguir el rendimiento del aplicativo en producción.
   - Configura alertas para detectar cualquier problema que pueda surgir después del despliegue.

#### b) Reuniones de Retrospectiva:
   - Al final de cada sprint, el equipo realiza una reunión de retrospectiva para discutir lo que funcionó bien, lo que se puede mejorar y cómo hacerlo.
   - Los aprendizajes se aplican en el próximo sprint.

### 7. **Mantenimiento y Ciclo de Vida Continuo**

#### a) Corrección de Bugs:
   - Los bugs encontrados en producción se gestionan de manera prioritaria, creando issues en el backlog.
   - Se aplican parches o fixes rápidamente y se despliegan siguiendo el mismo flujo de CI/CD.

#### b) Refactorización:
   - Identifica áreas del código que necesitan ser refactorizadas para mejorar la calidad o el rendimiento.
   - Integra la refactorización en el ciclo de desarrollo regular.

#### c) Documentación Continua:
   - Mantén la documentación del proyecto actualizada, incluyendo la arquitectura, APIs, guías de instalación y uso.
   - La documentación ayuda a nuevos miembros del equipo a integrarse y asegura que el conocimiento se mantenga en el equipo.

### Conclusión

Este flujo proporciona una estructura clara para la gestión y ejecución de un proyecto de desarrollo con un equipo de 5 desarrolladores. Al seguir este flujo, el equipo puede colaborar de manera efectiva, mantener la calidad del código y entregar funcionalidades de manera constante y confiable. La clave es la planificación cuidadosa, la comunicación constante, y la adaptación del flujo según las necesidades del proyecto.


---

Aquí te presento un caso realista donde tres programadores trabajan simultáneamente en el desarrollo de un juego de Tic-Tac-Toe (Tres en Raya) usando GitHub, Python y Visual Studio Code (VSCode). 

### **Contexto del Proyecto**

- **Objetivo:** Desarrollar una versión de Tic-Tac-Toe como un aplicativo de consola en Python.
- **Equipo:**
  - **Desarrollador 1 (Ana):** Responsable de la lógica del juego.
  - **Desarrollador 2 (Carlos):** Encargado de la interfaz de usuario en la consola.
  - **Desarrollador 3 (Beatriz):** Implementación de pruebas unitarias y CI/CD.

### **Flujo de Trabajo**

#### **1. Planificación Inicial**

- **Creación del Repositorio en GitHub:**
  - Carlos crea un repositorio en GitHub llamado `tictactoe-python`.
  - El repositorio se inicializa con un README básico que describe el proyecto.

- **Configuración del Repositorio:**
  - Ana configura la estructura básica del proyecto en el repositorio:
    - `src/`: Contendrá el código fuente.
    - `tests/`: Contendrá las pruebas unitarias.
    - `README.md`: Documentación básica del proyecto.
  - Beatriz añade un archivo `.gitignore` para excluir archivos innecesarios de ser rastreados por Git.

- **Asignación de Tareas:**
  - **Ana:** Desarrolla la lógica del juego (reglas, verificación de ganadores, etc.).
  - **Carlos:** Desarrolla la interfaz de usuario basada en la consola.
  - **Beatriz:** Configura las pruebas unitarias y el flujo de CI/CD.

#### **2. Desarrollo Simultáneo**

##### **Ana - Lógica del Juego**

- **Rama:** `feature/game-logic`
- **Tareas:**
  - Ana crea la clase `TicTacToe` en el archivo `src/tictactoe.py`.
  - Implementa la inicialización del tablero y los métodos para realizar movimientos, verificar ganadores y determinar si hay empate.

- **Commits:**
  - Ana realiza commits regulares con mensajes descriptivos: 
    - `Implementa inicialización del tablero.`
    - `Añade verificación de ganadores.`
  - Realiza un **push** de los cambios a la rama `feature/game-logic`.

##### **Carlos - Interfaz de Usuario**

- **Rama:** `feature/ui`
- **Tareas:**
  - Carlos desarrolla la interfaz de usuario en consola en `src/ui.py`.
  - Implementa funciones para imprimir el tablero y solicitar la entrada de los jugadores.

- **Commits:**
  - Carlos realiza commits regulares con mensajes como:
    - `Añade función para imprimir el tablero.`
    - `Implementa lógica para entrada de jugadores.`
  - Realiza un **push** a la rama `feature/ui`.

##### **Beatriz - Pruebas y CI/CD**

- **Rama:** `feature/tests-ci`
- **Tareas:**
  - Beatriz crea pruebas unitarias en `tests/test_tictactoe.py` para los métodos de la clase `TicTacToe`.
  - Configura un pipeline de CI usando GitHub Actions para que las pruebas se ejecuten automáticamente en cada push o pull request.

- **Commits:**
  - `Añade pruebas unitarias para la lógica del juego.`
  - `Configura GitHub Actions para CI/CD.`
  - Beatriz realiza un **push** a la rama `feature/tests-ci`.

#### **3. Integración y Revisión de Código**

- **Pull Requests (PRs):**
  - Cada desarrollador crea un pull request desde su rama (`feature/game-logic`, `feature/ui`, `feature/tests-ci`) hacia la rama `develop`.
  - Los PRs se revisan mutuamente:
    - Ana revisa el PR de Carlos para asegurarse de que la interfaz funciona bien con la lógica.
    - Carlos revisa el PR de Beatriz para verificar que las pruebas unitarias cubren los casos necesarios.
    - Beatriz revisa el PR de Ana, asegurándose de que la lógica esté correctamente implementada.

- **Fusión de PRs:**
  - Después de las revisiones y aprobaciones, los PRs se fusionan en `develop`.
  - Las pruebas automáticas de Beatriz aseguran que no haya conflictos ni errores introducidos al fusionar.

#### **4. Pruebas y Validación**

- **Despliegue en Entorno de Pruebas:**
  - Beatriz despliega el juego en un entorno de pruebas donde todo el equipo puede probar la aplicación manualmente.
  - Se identifican y corrigen bugs menores que se detectaron durante las pruebas.

- **Ejecución de Pruebas Automatizadas:**
  - El pipeline de CI ejecuta las pruebas unitarias cada vez que se hace un push a `develop` o se crea un PR hacia `main`.
  - Si las pruebas fallan, se notifica al equipo para que solucione el problema.

#### **5. Despliegue en Producción**

- **Preparación para Producción:**
  - Cuando el equipo está satisfecho con el desarrollo y las pruebas, Beatriz crea un pull request para fusionar `develop` en `main`.
  - Después de la aprobación, el código se despliega en producción.
  
- **Despliegue:**
  - La aplicación se despliega como una versión inicial del juego de Tic-Tac-Toe.

### **6. Mantenimiento y Mejoras Futuras**

- **Feedback y Mejoras:**
  - Después del lanzamiento, el equipo recopila feedback de los usuarios y lo utiliza para planificar futuras versiones del juego.
  - Nuevas funcionalidades, como la opción de jugar contra la computadora, se agregan al backlog para futuros sprints.

- **Soporte Continuo:**
  - El equipo sigue trabajando en corrección de bugs y refactorización del código para mejorar la calidad y la experiencia de usuario.

### **Conclusión**

Este caso demuestra cómo tres programadores pueden trabajar simultáneamente en diferentes aspectos de un proyecto usando GitHub, Python y VSCode. Mediante ramas separadas, revisiones de código y CI/CD, se garantiza que el proyecto se desarrolle de manera organizada y colaborativa, culminando en un producto final de calidad.


---
Aquí tienes un instructivo paso a paso para subir tus archivos `.md` (Markdown), creados en **Obsidian**, a **GitHub**. Asumo que ya tienes una cuenta en GitHub y te guiaré en los pasos básicos.

---
![[Separador.png]] 
[[Compartir notas de clase con los estudiantes]] 
---

Para trabajar en el repositorio que has hecho *fork* en **GitHub** desde tu computador personal utilizando **Visual Studio Code (VSCode)**, sigue los siguientes pasos:

### **Pasos para clonar el proyecto a tu máquina local y trabajar desde VSCode**:

---

### **1. Instalar Git y configurar tu cuenta (si no lo has hecho antes)**

#### **a. Instalar Git**:
- Si ya tienes **Git** instalado, puedes saltar este paso. Si no lo tienes, descarga e instala Git desde [aquí](https://git-scm.com/downloads) para tu sistema operativo.
  
#### **b. Configurar Git con tus credenciales de GitHub**:
Después de instalar Git, abre la terminal de tu sistema operativo o la terminal integrada de VSCode y configura tu usuario y correo electrónico que utilizarás para GitHub:
  
```bash
git config --global user.name "TuNombreDeUsuario"
git config --global user.email "tuemail@ejemplo.com"
```

Esto permitirá que Git relacione tus commits con tu cuenta de GitHub.

---

### **2. Clonar el repositorio del fork a tu máquina local**

#### **a. Copiar la URL del repositorio fork en GitHub**:
1. Ve a la página de tu *fork* en GitHub.
2. Haz clic en el botón verde **Code**.
3. Copia la URL del repositorio (puedes usar HTTPS o SSH, dependiendo de cómo prefieras clonar el repositorio).

#### **b. Clonar el repositorio en tu computador**:
Abre una terminal en tu sistema (o usa la terminal integrada en VSCode) y ejecuta el siguiente comando, reemplazando la URL por la URL que copiaste:

```bash
git clone https://github.com/TuNombreDeUsuario/nombre-del-repositorio-fork.git
```

Esto descargará el contenido del repositorio en una carpeta local.

---

```
git config --global user.name "CapitanFantastico"
git config --global user.email "gustavo.adolfo.osorio@correounivalle.edu.co"
git clone https://github.com/CapitanFantastico/Tic-tac-toe.git

Cloning into 'Tic-tac-toe'...
remote: Enumerating objects: 9, done.
remote: Counting objects: 100% (9/9), done.
remote: Compressing objects: 100% (7/7), done.
remote: Total 9 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
Receiving objects: 100% (9/9), done.

```
---


#### **c. Navegar al directorio del repositorio clonado**:
Después de clonar, entra en el directorio del proyecto para trabajar en él:

```bash
cd nombre-del-repositorio-fork
```

---

### **3. Abrir el proyecto en Visual Studio Code**

#### **a. Abrir VSCode en el directorio del proyecto**:
Si estás en la terminal, puedes abrir el proyecto en VSCode ejecutando:

```bash
code .
```

Este comando abrirá el directorio actual en VSCode. Si no tienes este comando habilitado, puedes seguir este proceso:

1. Abre **VSCode**.
2. En el menú principal, selecciona **File > Open Folder** (o **Archivo > Abrir carpeta**).
3. Navega a la carpeta donde clonaste el repositorio y selecciona la carpeta del proyecto para abrirla.

---

### **4. Vincular el repositorio local con el repositorio original (upstream)**

Esto es importante si quieres mantener tu fork sincronizado con el repositorio original (el que clonaste). El repositorio original es llamado "upstream".

#### **a. Agregar el repositorio original como "upstream"**:
En la terminal, asegúrate de estar en el directorio del proyecto y ejecuta el siguiente comando para agregar el repositorio original como un *remote* llamado **upstream**:

```bash
git remote add upstream https://github.com/UsuarioOriginal/nombre-del-repositorio-original.git
```

Esto permitirá obtener actualizaciones del repositorio original en el futuro.


```bash
PS C:\Users\Gustavo\Downloads\USB\Carpeta de desarrollo\TicTacToe> git remote add upstream https://github.com/CapitanFantastico/tic_tac_toe.git
```

#### **b. Verifica que "upstream" fue agregado correctamente**:
Para asegurarte de que la configuración fue exitosa, puedes listar los remotes que tienes configurados con este comando:

```bash
git remote -v
```

Deberías ver tanto tu repositorio **origin** (el fork que hiciste) como el **upstream** (el repositorio original).

```
PS C:\Users\Gustavo\Downloads\USB\Carpeta de desarrollo\TicTacToe> git remote -v
upstream        https://github.com/CapitanFantastico/tic_tac_toe.git (fetch)
upstream        https://github.com/CapitanFantastico/tic_tac_toe.git (push)
```


---

### **5. Hacer cambios en el proyecto usando VSCode**

Ahora que tienes el repositorio clonado y abierto en VSCode, puedes comenzar a hacer cambios en el código:

1. Abre cualquier archivo, haz tus ediciones.
2. Guarda los cambios.

---

### **6. Confirmar (commit) tus cambios en Git**

#### **a. Agregar los cambios al *stage* de Git**:
Después de realizar cambios en el código, debes añadirlos al área de preparación (*staging area*) antes de confirmarlos. Puedes hacerlo con:

```bash
git add .
```

El `.` indica que se agregarán todos los archivos modificados.

#### **b. Hacer un commit de tus cambios**:
Realiza un **commit** para registrar los cambios:

```bash
git commit -m "Descripción clara de los cambios que hiciste"
```

Asegúrate de que el mensaje del commit sea descriptivo y explique qué cambios hiciste.

---

### **7. Enviar (push) tus cambios a GitHub**

Ahora que has realizado el commit, puedes enviar tus cambios a tu fork en GitHub usando el comando **push**:

```bash
git push origin main
```

Esto enviará los cambios a la rama principal (o `main`) de tu fork en GitHub. Si tu repositorio usa `master` en lugar de `main`, reemplaza `main` por `master`.

---

### **8. Mantener el fork sincronizado con el repositorio original**

Es recomendable mantener tu fork sincronizado con el repositorio original (upstream), especialmente si se han hecho cambios importantes. Para hacerlo:

#### **a. Obtener los últimos cambios del repositorio original**:
Primero, obtén los cambios más recientes del repositorio **upstream**:

```bash
git fetch upstream
```

#### **b. Fusionar los cambios en tu rama local**:
Fusiona los cambios obtenidos desde el **upstream** en tu rama `main`:

```bash
git merge upstream/main
```

Si el repositorio original utiliza la rama `master`, usa `upstream/master`.

#### **c. Enviar los cambios actualizados a tu fork**:
Finalmente, envía los cambios sincronizados a tu fork en GitHub:

```bash
git push origin main
```

---

### **9. Crear un Pull Request en GitHub (opcional)**
Una vez que hayas realizado los cambios en tu fork y quieras contribuir al proyecto original, puedes crear un **Pull Request** desde GitHub:
1. Ve a la página de tu fork en GitHub.
2. Haz clic en **Pull Request**.
3. Sigue las instrucciones para comparar y enviar los cambios al repositorio original.

---

### **Resumen:**
1. Instala y configura **Git** si no lo has hecho antes.
2. Clona el repositorio fork en tu computadora.
3. Abre el proyecto en **VSCode**.
4. Vincula el repositorio original con **upstream**.
5. Realiza cambios en el código y guarda.
6. Haz un commit de los cambios.
7. Envía los cambios a tu fork en GitHub.
8. Mantén tu fork sincronizado con el repositorio original.

Con estos pasos, tendrás el proyecto listo para trabajar desde tu computadora local con **VSCode** y **GitHub**.

---

Los comandos `git rev-parse HEAD` y `git rev-parse origin/main` se utilizan para obtener información relacionada con los **hashes** de commits en un repositorio de Git. Aquí te explico qué hace cada uno:

### 1. **`git rev-parse HEAD`**
   - **Descripción**: Este comando obtiene el hash del commit actual al que apunta `HEAD`.
   - **¿Qué es `HEAD`?**: En Git, `HEAD` es un puntero que representa el commit actual en el que estás trabajando, es decir, el último commit en tu rama activa (normalmente la rama principal como `main` o `master`).
   - **Uso típico**: Este comando se utiliza para obtener el identificador único (hash SHA-1) del commit en el que te encuentras en ese momento. Esto es útil para referencia o para otras operaciones automatizadas.

   **Ejemplo de salida**:
   ```
   $ git rev-parse HEAD
   e83c5163316f89bfbde7d9ab23ca2e25604af290
   ```
   La salida es el hash completo del commit actual.

### 2. **`git rev-parse origin/main`**
   - **Descripción**: Este comando obtiene el hash del commit más reciente en la rama `main` del remoto `origin`.
   - **¿Qué es `origin/main`?**: `origin` es el nombre predeterminado que Git asigna al repositorio remoto (normalmente el repositorio en GitHub, GitLab, etc.), y `main` es el nombre de la rama principal en ese remoto. Por lo tanto, `origin/main` se refiere al último commit en la rama `main` del repositorio remoto.
   - **Uso típico**: Se utiliza para obtener el hash del último commit que está en la rama `main` del remoto. Esto es útil cuando quieres verificar en qué commit está la rama remota en comparación con tu rama local.

   **Ejemplo de salida**:
   ```
   $ git rev-parse origin/main
   c84b1e49b291ac648192af08471e0503bfc25fb1
   ```
   La salida es el hash del commit más reciente en la rama `main` del repositorio remoto.

### Resumen:
- **`git rev-parse HEAD`**: Muestra el hash del commit actual en el que estás trabajando en tu repositorio local.
- **`git rev-parse origin/main`**: Muestra el hash del último commit en la rama `main` del repositorio remoto `origin`.

Ambos comandos son útiles para obtener referencias precisas de commits y compararlas entre tu copia local y el repositorio remoto.

---

El comando `git pull origin main` es usado para **actualizar** tu copia local del repositorio con los últimos cambios que se encuentran en la rama `main` del repositorio remoto `origin`. Esencialmente, combina dos acciones: **`git fetch`** y **`git merge`**.

### Desglose del comando:

- **`git pull`**: Este comando descarga los cambios desde el repositorio remoto y los fusiona automáticamente con la rama en la que estás trabajando localmente.
- **`origin`**: Es el nombre predeterminado del repositorio remoto (generalmente en GitHub, GitLab, etc.). Indica de dónde se deben obtener los cambios.
- **`main`**: Es el nombre de la rama del repositorio remoto desde la cual se deben traer los cambios. En muchos casos, esta es la rama principal del proyecto.

### Lo que hace paso a paso:

1. **`git fetch origin main`**: Primero, **descarga** los commits y archivos más recientes de la rama `main` desde el remoto `origin`, pero no los fusiona inmediatamente con tu código local.
2. **`git merge origin/main`**: Luego, **fusiona** (merge) los cambios traídos desde el remoto `origin` con tu rama actual. Si ya estás en la rama `main` localmente, se fusionarán los cambios que haya en el `origin/main` con tu `main` local.

### Escenarios comunes:

- Si tu rama local **está desactualizada** (por ejemplo, si otros colaboradores han hecho cambios en la rama `main` del remoto), este comando traerá esos cambios y los combinará con los cambios en tu repositorio local.
- Si no tienes cambios locales que entren en conflicto con los cambios remotos, el proceso se completa automáticamente sin intervención.
- Si hay **conflictos** entre los cambios remotos y los tuyos, Git te pedirá que resuelvas esos conflictos manualmente antes de completar el merge.

### Ejemplo práctico:

Supongamos que has estado trabajando en la rama `main` de tu repositorio local y que tu compañero de equipo ha hecho varios cambios y los ha subido al remoto. Para obtener esos cambios y fusionarlos con tu copia local, ejecutarías:

```bash
git pull origin main
```

Esto asegura que tienes la versión más reciente del código en tu copia local, actualizando tanto el historial de commits como los archivos.

### Resumen:
- **`git pull origin main`**: 
   - Trae los cambios de la rama `main` del remoto `origin`.
   - Los fusiona automáticamente con tu rama actual local (si estás en `main`, los fusiona con `main`).
   - Si no hay conflictos, se realiza una fusión automática. Si hay conflictos, debes resolverlos manualmente.