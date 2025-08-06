---
theme: ./theme.json
author: Joaquin Vigna
date: MMMM dd, YYYY
paging: Slide %d / %d
width: 100
---

```
██████╗ ██████╗  ██████╗ ██╗  ██╗███████╗███╗   ██╗████████╗ █████╗ ██╗     ██╗  ██╗
██╔══██╗██╔══██╗██╔═══██╗██║ ██╔╝██╔════╝████╗  ██║╚══██╔══╝██╔══██╗██║     ██║ ██╔╝
██████╔╝██████╔╝██║   ██║█████╔╝ █████╗  ██╔██╗ ██║   ██║   ███████║██║     █████╔╝
██╔══██╗██╔══██╗██║   ██║██╔═██╗ ██╔══╝  ██║╚██╗██║   ██║   ██╔══██║██║     ██╔═██╗
██████╔╝██║  ██║╚██████╔╝██║  ██╗███████╗██║ ╚████║   ██║   ██║  ██║███████╗██║  ██╗
╚═════╝ ╚═╝  ╚═╝ ╚═════╝ ╚═╝  ╚═╝╚══════╝╚═╝  ╚═══╝   ╚═╝   ╚═╝  ╚═╝╚══════╝╚═╝  ╚═╝

 ██████╗██╗     ██╗    ████████╗ ██████╗  ██████╗ ██╗     ███████╗
██╔════╝██║     ██║    ╚══██╔══╝██╔═══██╗██╔═══██╗██║     ██╔════╝
██║     ██║     ██║       ██║   ██║   ██║██║   ██║██║     ███████╗
██║     ██║     ██║       ██║   ██║   ██║██║   ██║██║     ╚════██║
╚██████╗███████╗██║       ██║   ╚██████╔╝╚██████╔╝███████╗███████║
 ╚═════╝╚══════╝╚═╝       ╚═╝    ╚═════╝  ╚═════╝ ╚══════╝╚══════╝
```

---

# Herramientas CLI para Desarrolladores

```bash
~~~
cowsay -f dragon "La terminal no es el pasado, es el presente más eficiente"
~~~
```

---

## ¿Por qué la terminal?

### Eficiencia 🚀

- Herramientas escritas en lenguajes de alto rendimiento (C, Rust, Go)
- Soluciones cuando los IDEs y GUIs se quedan cortos
- Diseño minimalista: una herramienta, un propósito, máxima velocidad

### Enfoque 🎯

- Menos distracciones visuales = mayor concentración
- Tu trabajo va más allá de escribir código: gestión, automatización, análisis
- Un entorno unificado donde todo fluye sin interrupciones

### Adaptabilidad ⚡

- Construye TU ambiente de trabajo ideal
- Personaliza cada herramienta a tu flujo específico
- La pregunta clave: "¿Qué tarea repito constantemente que podría automatizar?"

---

## Aclaraciones importantes

### 1. **Personalización** 🛠️

> Estas herramientas son las que **yo** encuentro útiles
> Cada workflow debe ser adaptado a **tus** necesidades

### 2. **No a la memorización** 🧠

> No necesitas recordar comandos exactos
> Usar alias y atajos para casos específicos
> ⚠️Tip: veremos otras formas de buscar y crear comandos.

### 3. **Curva de aprendizaje** 📈

> Los primeros días/semanas son difíciles
> Los shortcuts se pulen mes a mes

---

## Categorías de herramientas

### **Navegación** 🧭

- `zoxide` - Navegación inteligente de directorios
- `eza` - Listado de archivos mejorado
- `yazi` - Explorador de archivos en terminal

### **Busqueda** 📁

- `fzf` - Búsqueda fuzzy universal

### **Multiplexación** 🪟

- `tmux` - Gestión de sesiones y ventanas

### **Control de versiones** 🌿

- `lazygit` - Interfaz visual para Git
- `gh` - GitHub CLI

### **IA** 🤖

- `gh copilot` - IA en la terminal

### **Desarrollo** 💻

- `neovim` - Editor de texto avanzado

---

## zoxide - El cd inteligente 🧠

### ¿Qué es zoxide?

Una **mejora sobre cd** que recuerda y aprende tus directorios más usados

```bash
# En lugar de esto:
cd ~/Documents/projects/web/my-awesome-project

# Solo escribes:
z awesome
```

---

## ¿Cómo funciona zoxide?

### Sistema de puntaje 📊

- **Frecuencia**: Cuántas veces visitas un directorio
- **Recencia**: Cuándo fue la última vez que lo visitaste
- **Algoritmo**: Combina ambos factores para determinar el mejor match

```bash
# Primera vez
cd ~/projects/cliente-abc  # zoxide lo registra

# Después
z abc  # ¡Te lleva directo!
```

---

## Reemplazando cd completamente

### En tu `.zshrc`

```bash
# Añadir al final del archivo
eval "$(zoxide init zsh)"

# Esto habilita:
# - z: para saltar a directorios
# - zi: selección interactiva con fzf

# Si quieres reemplazar cd por z:
alias cd="z"
```

### Para bash, fish, etc

```bash
eval "$(zoxide init bash)"  # .bashrc
zoxide init fish | source   # config.fish
```

---

## Mi caso de uso favorito 🚀

### Cambio rápido entre proyectos

```bash
# Estoy en cualquier parte del sistema
pwd  # /home/user/Downloads

# Recuerdo vagamente el nombre del proyecto
z blog  # → /home/user/projects/personal-blog

# Múltiples palabras para ser más específico
z client api  # → /home/user/work/client-xyz/api-backend
```

> **Pro tip**: No importa dónde estés, con recordar parcialmente el nombre es suficiente

---

## eza - El ls moderno 🎨

### ¿Qué es eza?

Un **reemplazo moderno para ls** escrito en Rust

```bash
# En lugar de esto:
ls -la

# Obtienes esto:
eza -la --icons --git
# → Iconos, colores, estado de git, y más información útil
```

---

## Formas de visualización en eza

### Las 3 vistas principales 📋

```bash
# Lista detallada (más común)
eza -l --icons

# Vista de árbol (explorar estructura)
eza --tree --level=2 --icons

# Vista de grilla (aprovechar ancho de terminal)
eza --grid --icons
```

### Banderas esenciales 🏁

```bash
--git          # Estado de archivos en git (M, N, ?)
--header       # Encabezados de columnas
--icons        # Iconos por tipo de archivo
-a             # Archivos ocultos
--group-directories-first  # Carpetas primero
```

---

## Combinaciones poderosas y aliases

### Combos útiles para desarrollo 💪

```bash
# Vista completa de proyecto
eza -la --icons --git --header --group-directories-first

# Árbol ignorando node_modules
eza --tree --git-ignore --level=3 --icons

# Archivos modificados recientemente
eza -la --sort=modified --reverse --time-style=relative
```

### Mis aliases favoritos 🌟

```bash
# Reemplazo directo de ls
alias ls='eza -a --color=always --long --git --no-filesize --icons=always --no-time --no-user --no-permissions'

# Lista detallada con git
alias ll='eza -la --icons --git --header --time-style=relative'

# Árbol de proyecto
alias lt='eza --tree --level=3 --icons --git-ignore'
```

---

## yazi - Explorador de archivos moderno 📁

### ¿Qué es yazi?

Un **explorador de archivos en terminal** ultra rápido escrito en Rust

```bash
# En lugar de hacer esto:
cd src/components
ls -la
cd Header
nvim index.js

# Navegas visualmente:
yazi
# → Preview instantáneo, navegación vim-like, operaciones asíncronas
```

---

## Navegación estilo Vim en yazi

### Movimientos básicos 🎮

```bash
# Navegación principal
j/k         # Abajo/arriba
h/l         # Salir/entrar carpetas
gg/G        # Inicio/final de lista

# Scroll en preview
J/K         # Scroll abajo/arriba en panel de preview
```

### Búsqueda y saltos rápidos ⚡

```bash
/           # Buscar en directorio actual
n/N         # Siguiente/anterior resultado
.           # Toggle archivos ocultos
```

---

## Operaciones de archivos en yazi

### Selección y manipulación 🔧

```bash
# Selección
<Space>     # Seleccionar/deseleccionar
v           # Modo visual (como Vim)

# Operaciones
y           # Copiar (yank)
x           # Cortar
p           # Pegar
d           # Eliminar
r           # Renombrar
```

### Features que cambian el juego 🚀

- **Preview en tiempo real** - Imágenes, código, PDFs sin abrir nada
- **Operaciones asíncronas** - Copia archivos grandes sin bloquear
- **Integración nativa** - zoxide, fzf, ripgrep ya integrados

---

## Búsquedas inteligentes en yazi 🔍

### Las 3 teclas mágicas

```bash
z           # zoxide - Saltar a directorios visitados
            # Ejemplo: z proj → ~/Documents/projects/website

s           # fd - Buscar archivos por nombre
            # Ejemplo: s config → encuentra config.json, config.yaml

S           # ripgrep - Buscar contenido dentro de archivos
            # Ejemplo: S TODO → archivos que contienen "TODO"
---

```
