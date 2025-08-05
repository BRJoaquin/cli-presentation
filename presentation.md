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

### **Procesamiento de datos** 🔧

- `jq` - Manipulación de JSON

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

### En tu `.zshrc`:

```bash
# Añadir al final del archivo
eval "$(zoxide init zsh)"

# Esto habilita:
# - z: para saltar a directorios
# - zi: selección interactiva con fzf
```

### Para bash, fish, etc:

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
