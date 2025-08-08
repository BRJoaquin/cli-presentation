---
theme: ./theme.json
author: Joaquin Vigna
date: MMMM dd, YYYY
paging: Slide %d / %d
width: 50
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
cowsay -f dragon "No hay mayor satisfacción que invertir horas automatizando una tarea que al final toma segundos."
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
```

---

## fzf - El buscador fuzzy universal 🔮

### ¿Qué es fzf?

Un **filtro interactivo** que te permite buscar y seleccionar de cualquier lista

```bash
# La filosofía de fzf:
# 1. Toma cualquier entrada (archivos, historial, procesos...)
# 2. Te deja buscar interactivamente
# 3. Devuelve tu selección

# Es la navaja suiza de la terminal
```

### ¿Por qué es especial? ✨

- **Fuzzy matching**: No necesitas escribir exacto
- **Combina con TODO**: pipes, comandos, scripts
- **Velocidad extrema**: Millones de líneas sin problema
- **La base perfecta** para crear tus propias herramientas

---

## fzf - Comandos base

### El poder está en los atajos ⚡

```bash
fzf                  # Solo: busca archivos en directorio actual

CTRL-T               # Buscar archivos desde cualquier comando
# Ejemplo: vim <CTRL-T> → busca y abre archivo

CTRL-R               # ¡EL GAME CHANGER! Busca en tu historial
# Nunca más olvides ese comando largo que usaste

ALT-C                # Cambiar de directorio interactivamente
```

### ¿Por qué CTRL-R es revolucionario? 🚀

```bash
# En lugar de:
history | grep docker

# Solo presionas CTRL-R y escribes: "dock"
```

---

## fzf - El poder del \*\*

### Autocompletado fuzzy en esteroides 💪

```bash
# Activa búsqueda fuzzy al escribir **<TAB>
nvim **<TAB>          # Busca cualquier archivo recursivamente
cd **<TAB>           # Navega a cualquier directorio
kill -9 **<TAB>      # Selecciona proceso para matar
```

### Ejemplos prácticos del día a día

```bash
# 1. Matar proceso molesto
kill -9 $(ps aux | fzf | awk '{print $2}')

# 2. Cambiar a branch de git
git checkout $(git branch | fzf)
```

---

## fzf - Combinaciones poderosas

### La magia de los pipes 🪄

```bash
# 1. Buscar en logs CSV
cat logs.csv | fzf

# Ejemplo: buscar errores del usuario "admin" en tiempo real
```

### Buscar archivos con preview sintáctico 🎨

```bash
# 2. Buscar arhivos js con preview en colores
fd -e js | fzf --preview 'bat --color=always {}' \
  --preview-window=right:60% \
  --bind 'enter:execute(nvim {})'

# bat muestra el código con syntax highlighting
```

### Buscar código y abrir en editor 💻

```bash
# 3. Buscar variables con ripgrep + colores + preview
rg --color=always "var" | fzf --ansi \
  --preview 'bat --color=always {1}' \
  --preview-window=right:50% \
  --delimiter=: \
  --bind 'enter:execute(nvim {1} +{2})'

# --ansi: mantiene colores de ripgrep
# {1}: archivo, {2}: línea → abre en la línea exacta
```

---

# fzf - Bonus: scripts

Algunos scripts que uso a diario:

- gh-clone: Busca todos tus repos y clona el que elijas
- gh-pr: Busca los PRs abiertos y te cambia de rama automáticamente

---

## tmux - Sesiones persistentes de terminal 🔄

### ¿Qué es tmux?

Un **gestor de sesiones de terminal** que mantiene tu trabajo vivo

### ¿Para qué sirve? 💡

- **Desarrollo remoto**: SSH se cae, tu trabajo sigue
- **Contextos separados**: Una sesión por proyecto
- **Procesos largos**: Deja corriendo, desconecta, vuelve mañana

---

## tmux - Comandos básicos

### Gestión de sesiones 🎯

```bash
# Crear sesión
tmux new -s proyecto        # Nueva sesión "proyecto"
tmux new -s api -d          # Nueva sesión en background

# Listar sesiones
tmux ls                     # Ver todas las sesiones

# Conectar a sesión
tmux attach -t proyecto     # Reconectar a "proyecto"
tmux a                      # Attach a la última sesión

# Eliminar sesión
tmux kill-session -t api    # Eliminar sesión "api"
```

### Shortcuts esenciales (Prefix: Ctrl+b) ⌨️

```bash
# Ventanas
Ctrl+b c        # Create nueva ventana
Ctrl+b n        # Next ventana
Ctrl+b p        # Previous ventana
Ctrl+b 0-9      # Ir a ventana número X

# Paneles
Ctrl+b %        # Split vertical |
Ctrl+b \"       # Split horizontal —
Ctrl+b o        # Cambiar al siguiente panel
Ctrl+b arrow    # Moverse entre paneles

# Sesión
Ctrl+b d        # Detach (salir sin cerrar)
```

---

## tmux - Bonus: Scripts personalizados 🚀

### Automatización con funciones custom

```bash
# tcode - Ambiente de desarrollo instantáneo
# → Crea sesión con nombre del directorio actual
# → Ventana 1: nvim abierto
# → Ventana 2: terminal split para comandos/servidor
# → Si ya existe, te conecta

# tattach - Attach interactivo con fzf
# → Lista todas las sesiones
# → Seleccionas con fzf
# → Te conecta a la elegida

# tkill - Kill selectivo
# → Muestra sesiones con fzf
# → Puedes seleccionar múltiples
# → Las elimina de una vez

# tkillall - Limpieza total
# → Elimina TODAS las sesiones
# → Útil para empezar fresh
```

### Uso típico del workflow 🔄

```bash
cd ~/projects/api
tcode              # → Sesión "api" con nvim + terminal

cd ~/projects/web
tcode              # → Sesión "web" con nvim + terminal

tattach            # → Elige entre api/web con fzf
tkill              # → Elimina sesiones que no usas
```

---

## lazygit - Git visual en la terminal 🎨

### ¿Qué es lazygit?

Una **interfaz visual para Git** que simplifica operaciones complejas

```bash
lazygit  # → Dashboard interactivo de Git
```

### Características principales ✨

- **Stage selectivo**: Elige líneas específicas para commit
- **Vista unificada**: Status, branches, commits, stashes
- **Navegación visual**: Preview de cambios al instante

---

## gh - GitHub desde la terminal 🐙

### ¿Qué es gh?

La **CLI oficial de GitHub** para trabajar con repos sin salir de la terminal

```bash
# Sin gh: cambiar al browser constantemente
# Con gh: todo desde donde estás trabajando

gh pr create    # → Crear PR desde la terminal
gh repo clone   # → Clonar con un comando
gh pr list      # → Ver estado de PRs
```

### ¿Para qué sirve? 💡

- **Pull Requests**: Crear, revisar, mergear sin browser
- **Gestión de repos**: Clonar, fork, crear nuevos
- **Ver estado**: PRs abiertos, reviews pendientes
- **Automatizar**: Scripts que interactúan con GitHub

---

## gh - Comandos más útiles

### Los que uso a diario 🚀

```bash
# Crear PR interactivo
gh pr create
# → Te pregunta título, descripción, reviewers
# → Auto-detecta el branch

# Ver PRs y su estado
gh pr list                    # Lista PRs abiertos
gh pr view                    # Ver PR actual en terminal
gh pr view --web              # Abrir PR en browser

# Clonar repo (más fácil que git clone)
gh repo clone user/repo       # Clona con SSH automáticamente
```

---

## gh copilot - IA en tu terminal 🤖

### GitHub Copilot para CLI

Obtén **sugerencias de comandos** y **explicaciones** directamente en la terminal

```bash
# Instalar extensión
gh extension install github/gh-copilot

# Preguntar cómo hacer algo
gh copilot suggest "comprimir todos los jpg en subdirectorios"
# → tar -czf images.tar.gz $(find . -name "*.jpg")

# Explicar comandos complejos
gh copilot explain "ps aux | grep python | awk '{print $2}' | xargs kill"
# → Te explica paso a paso qué hace cada parte
```

### Alias para flujo ultra rápido ⚡

```bash
# En tu .bashrc/.zshrc
alias '??'='gh copilot suggest'
alias '?!'='gh copilot explain'

# Uso diario:
?? "encontrar archivos grandes"
# → find . -type f -size +100M

?? "ver puertos en uso"
# → lsof -i -P -n | grep LISTEN

?! "chmod 755"
# → Explicación de permisos Unix
```

---

## neovim - El editor del futuro 🚀

### ¿Qué es neovim?

Un **editor de texto modal** basado en Vim, pero modernizado para el siglo XXI

```bash
nvim archivo.js  # → Editor potente, extensible y rápido
```

### ¿Por qué neovim? 💡

- **Modal**: Modos separados para escribir, navegar y comandar
- **Extensible**: Miles de plugins, LSP nativo, Treesitter
- **Eficiente**: Nunca sacas las manos del teclado
- **Portable**: Misma config en local, servidor, contenedor

### Lo esencial para empezar 🎯

```bash
# Modos básicos
i         # Insert - escribir
Esc       # Normal - navegar/comandos
:wq       # Guardar y salir
:q!       # Salir sin guardar

# Movimiento eficiente
hjkl      # ← ↓ ↑ → (sin flechas)
w/b       # Siguiente/anterior palabra
gg/G      # Inicio/fin del archivo
```

> **No es para todos**: Curva de aprendizaje alta, pero el retorno de inversión es enorme para quienes viven en la terminal

---

```bash
 ██████╗ ██████╗  █████╗  ██████╗██╗ █████╗ ███████╗██╗
██╔════╝ ██╔══██╗██╔══██╗██╔════╝██║██╔══██╗██╔════╝██║
██║  ███╗██████╔╝███████║██║     ██║███████║███████╗██║
██║   ██║██╔══██╗██╔══██║██║     ██║██╔══██║╚════██║╚═╝
╚██████╔╝██║  ██║██║  ██║╚██████╗██║██║  ██║███████║██╗
 ╚═════╝ ╚═╝  ╚═╝╚═╝  ╚═╝ ╚═════╝╚═╝╚═╝  ╚═╝╚══════╝╚═╝
```
