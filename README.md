# 🎓 Plantilla LaTeX para Artículos Científicos — Revista +Ingenio

Esta es la plantilla oficial en **LaTeX** para la preparación y maquetación de artículos científicos a ser presentados en la revista **+Ingenio** (Revista de Ciencia, Tecnología e Innovación de la Facultad de Ingeniería de la Universidad Nacional de Misiones - UNaM).

El objetivo de esta plantilla es facilitar a los autores el cumplimiento de los estándares tipográficos y de formato exigidos por la editorial de la revista, garantizando un resultado uniforme, profesional y de alta calidad.

---


## 🚀 Características Clave

La plantilla viene pre-configurada con las siguientes especificaciones y paquetes recomendados:

*   **Tipografía Estándar:** Configurada en *Times New Roman* (12pt para texto base) mediante `newtxtext` y `newtxmath`.
*   **Márgenes Precisos:** Ajustados según las directrices de la revista (Superior e Izquierdo: 25 mm; Inferior y Derecho: 15 mm).
*   **Gestión de Bibliografía:** Automatizada con `biblatex` y el motor `biber`, utilizando el estilo estándar de la **IEEE**.
*   **Símbolos y Nomenclatura:** Tabla de nomenclatura automática de dos columnas mediante el paquete `nomencl`.
*   **Tablas Profesionales:** Maquetación moderna y limpia mediante el paquete `tabularray`, evitando desajustes y desbordes.
*   **Unidades Físicas:** Uso consistente del paquete `siunitx` para notación científica y unidades del Sistema Internacional (SI).
*   **Hipervínculos:** Enlaces internos e hipervínculos activos en todo el PDF con `hyperref`.

---

## 📂 Estructura del Proyecto

El repositorio está organizado de la siguiente manera:

*   **[main.tex](file:///home/fab/Projects/plantilla-ingenio/main.tex):** Archivo fuente principal. Contiene el preámbulo con la carga de paquetes, los datos del artículo (título, autores, afiliaciones) y el cuerpo del texto estructurado en secciones.
*   **[references.bib](file:///home/fab/Projects/plantilla-ingenio/references.bib):** Base de datos bibliográfica en formato BibTeX. Aquí se registran las referencias que luego se invocan en el texto con `\cite{...}`.
*   **`images/`:** Directorio para almacenar los recursos gráficos y figuras (se recomiendan formatos vectoriales como PDF/EPS o imágenes de alta resolución en PNG/JPG).
*   **[LICENSE](file:///home/fab/Projects/plantilla-ingenio/LICENSE):** Archivo de licencia del proyecto.
*   **`main.pdf`:** Guía visual interactiva compilada que detalla el manual de uso de la plantilla.

---

## 🛠️ Requisitos de Software

Para compilar este proyecto de forma local, necesitará instalar una distribución de LaTeX completa que incluya:

1.  **Motor de Compilación:** `pdflatex` (o alternativamente `xelatex` o `lualatex`).
2.  **Gestor de Bibliografía:** `biber` (requerido por `biblatex` para procesar la bibliografía).
3.  **Generador de Índices:** `makeindex` (para la tabla de símbolos y nomenclatura).
4.  **Automatización (Opcional pero recomendado):** `latexmk`.

### 📦 Instalación de dependencias

*   **En Linux (Debian/Ubuntu):**
    ```bash
    sudo apt update
    sudo apt install texlive-full latexmk
    ```
*   **En Windows:** Se recomienda instalar **[MiKTeX](https://miktex.org/)** o **[TeX Live](https://www.tug.org/texlive/)** y asegurarse de instalar el motor `biber` desde la consola de paquetes.
*   **En macOS:** Se recomienda instalar **[MacTeX](https://www.tug.org/mactex/)**.

---

## ⚙️ Cómo Comenzar (Uso como Plantilla)

Dado que este repositorio está configurado en GitHub como una **plantilla (template)**, no es necesario clonarlo y borrar el historial de Git manualmente. Puede comenzar de las siguientes maneras:

1. **Desde GitHub (Recomendado):**
   * Inicie sesión en su cuenta de GitHub.
   * Haga clic en el botón verde **"Use this template" (Usar esta plantilla)** en la parte superior.
   * Seleccione **"Create a new repository" (Crear un nuevo repositorio)**.
   * Elija un nombre y créelo. Tendrá una copia limpia en su cuenta sin el historial de commits original.
2. **Descarga Directa:**
   * Descargue el código en `.zip` mediante **Code > Download ZIP**, extráigalo y trabaje localmente.
3. **Clonación Tradicional:**
   * Clone el repositorio de forma estándar usando su terminal:
     ```bash
     git clone <url-del-repositorio>
     ```

---

## 💻 Instrucciones de Compilación

### Opción 1: Compilación Automática (Recomendada)
Si tiene instalado `latexmk`, puede compilar el artículo completo (incluyendo bibliografía y símbolos) con un solo comando:

```bash
latexmk -pdf main.tex
```

> [!TIP]
> Para mantener la compilación en tiempo real mientras edita, puede ejecutar:
> ```bash
> latexmk -pdf -pvc main.tex
> ```

### Opción 2: Compilación Manual (Paso a Paso)
Si prefiere realizar la compilación manualmente o si su editor de texto (como VS Code con LaTeX Workshop, Texstudio, etc.) lo requiere, ejecute la siguiente secuencia de comandos en la terminal:

1.  **Primera pasada de compilación:**
    ```bash
    pdflatex main.tex
    ```
2.  **Procesar la bibliografía:**
    ```bash
    biber main
    ```
3.  **Generar la tabla de símbolos (nomenclatura):**
    ```bash
    makeindex main.nlo -s nomencl.ist -o main.nls
    ```
4.  **Compilaciones finales para resolver referencias cruzadas:**
    ```bash
    pdflatex main.tex
    pdflatex main.tex
    ```

---

## ✍️ Guía Rápida de Edición

### 1. Título, Autores y Afiliaciones
Modifique el bloque correspondiente en el preámbulo de [main.tex](file:///home/fab/Projects/plantilla-ingenio/main.tex):
*   **Título:** Edite el comando `\title{...}` sin remover los logotipos de la cabecera.
*   **Autores:** Use el comando `\author{...}` separando a los autores con `\and`.
*   **Afiliaciones:** Edite el comando `\date{...}` para registrar las instituciones y los correos electrónicos.

### 2. Resumen y Palabras Clave
La estructura requiere tanto la versión en español como en inglés (*Abstract* y *Keywords*):
```latex
\begin{abstract}
  % Su resumen en español aquí (máximo 200 palabras)
  \vspace{0.5em}\noindent\textit{\textbf{Palabras Clave} --- palabra1, palabra2...}
\end{abstract}
```

### 3. Agregar Símbolos
Para incorporar términos a la sección de Simbología, use el comando `\nomenclature`:
```latex
\nomenclature{$E$}{Energía de activación (\unit{\joule\per\mole})}
```

### 4. Insertar Figuras y Tablas
*   **Figuras:** Almacénelas en la carpeta `images/` e insértelas usando el entorno `figure`:
    ```latex
    \begin{figure}[htbp]
        \centering
        \includegraphics[width=0.65\linewidth]{images/mi_grafico.pdf}
        \caption{Descripción del gráfico.}
        \label{fig:mi_grafico}
    \end{figure}
    ```
*   **Tablas:** Utilice el entorno `tblr` para lograr tablas limpias acordes a las normas de la revista:
    ```latex
    \begin{table}[htbp]
      \centering\footnotesize
      \caption{Título de la tabla} \label{tb:mi_tabla}
      \begin{tblr}{colspec={c|c}, hline{1,Z}={1.5pt}, hline{2}={solid}}
        \textbf{Encabezado 1} & \textbf{Encabezado 2} \\
        Dato A & Dato B
      \end{tblr}
    \end{table}
    ```

> [!WARNING]
> Recuerde que los títulos de las **Tablas** se colocan **arriba** de las mismas, mientras que las leyendas de las **Figuras** se ubican **abajo**.

---

## 🔗 Enlaces de Interés

*   🌐 **Sitio Web Oficial de +Ingenio:** [revistas.fio.unam.edu.ar/index.php/masingenio](http://revistas.fio.unam.edu.ar/index.php/masingenio)
*   📥 **Portal de Envíos:** [revistas.fio.unam.edu.ar/index.php/masingenio/es/about/submissions](https://revistas.fio.unam.edu.ar/index.php/masingenio/es/about/submissions)
*   🏫 **Facultad de Ingeniería - UNaM:** [fio.unam.edu.ar](https://www.fio.unam.edu.ar)
