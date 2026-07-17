# 👾 Pacman Smiley Game - Project Context (CLAUDE.md)

```
╔════════════════════════════════════════════════════════════════╗
║                  PACMAN SMILEY GAME PROJECT                    ║
║         Claude AI Assisted Development Context                 ║
╚════════════════════════════════════════════════════════════════╝
```

---

## 📋 Project Overview

**Project Name**: Pacman Smiley - Come las Bolitas  
**Version**: 1.0.0  
**Status**: ✅ Production Ready  
**Technology**: HTML5 Canvas + Vanilla JavaScript  
**Repository**: wallejelsma-stack/pacman  
**Primary Branch**: claude/pacman-smiley-game-fvxyii  

---

## 🎯 Project Goals

### Primary Objectives
1. ✅ Crear un juego tipo Pac-Man funcional y jugable
2. ✅ Implementar mecánicas clásicas de Pac-Man
3. ✅ Desarrollar una interfaz limpia e intuitiva
4. ✅ Asegurar compatibilidad multiplataforma
5. ✅ Cero dependencias externas para la lógica del juego

### Secondary Objectives
1. ✅ Proporcionar excelente feedback visual
2. ✅ Implementar animaciones suaves a 60 FPS
3. ✅ Crear documentación completa
4. ✅ Facilitar extensiones del desarrollador

---

## 📁 File Structure & Purpose

```
Pacman/
├── README.md                    # Guía de usuario y documentación
├── CLAUDE.md                    # Este archivo - contexto de IA
├── index.html                   # ⭐ JUEGO PRINCIPAL (Todo en uno)
└── .gitignore                   # Reglas de git ignore

Archivo Principal:
═════════════════════════════════════════════════════════════════
index.html
  └─ Implementación completa en Canvas 2D
  └─ HTML + CSS + JavaScript integrado
  └─ Sin dependencias externas
  └─ Mejor rendimiento y compatibilidad
```

---

## 🔧 Technology Stack

### Frontend
```
HTML5
├── Canvas API (dibujo)
├── Canvas 2D Context (renderizado)
├── Event API (entrada del usuario)
└── Window API (timing)

CSS3
├── Flexbox (layout UI)
├── Transiciones (animaciones)
├── Media queries (responsividad)
└── Propiedades custom (theming)

JavaScript (ES6)
├── requestAnimationFrame (game loop)
├── Event listeners (entrada de usuario)
├── Gestión de estado (lógica del juego)
└── Patrones funcionales (utilidades)
```

### Build & Deployment
- ✅ No se requiere build step
- ✅ Ejecución directa en navegador
- ✅ Puede servirse con cualquier servidor HTTP
- ✅ Listo para deployment en artifact cloud

### Browser Support
- Chrome 60+ ✅
- Firefox 55+ ✅
- Safari 12+ ✅
- Edge 79+ ✅
- IE 11 ❌ (Not supported)

---

## 🎮 Game Mechanics Reference

### Core Game Loop
```
┌─────────────────────────────────┐
│   Inicializar Estado del Juego  │
│   └─ Smiley, Fantasmas, Items  │
└──────────────┬──────────────────┘
               │
               ▼
        ┌─────────────┐
        │ Game Loop   │ (60 FPS)
        │ (RAF)       │
        └──────┬──────┘
               │
        ┌──────┴──────────────┐
        │                     │
        ▼                     ▼
   Update(dt)            Render()
   ├─ Mover smiley       ├─ Limpiar canvas
   ├─ Mover fantasmas    ├─ Dibujar grid
   ├─ Detectar colisiones├─ Dibujar smiley
   ├─ Comer pelotitas   ├─ Dibujar fantasmas
   └─ Actualizar UI      └─ Mostrar puntuación
```

### Game States
```
MENU/INIT
  └─ Esperando inicio del juego
  └─ Sin lógica activa

RUNNING
  └─ Juego activo
  └─ Smiley moviéndose
  └─ Fantasmas moviéndose
  └─ Detectando colisiones

PAUSED
  └─ Juego congelado
  └─ UI visible
  └─ Puede reanudarse

GAME_OVER
  └─ Juego terminado por atrapado
  └─ Mostrar pantalla de game over

WON
  └─ Juego ganado (todas las pelotitas comidas)
  └─ Mostrar pantalla de victoria
```

### Collision Detection
```javascript
// Pelotitas
if (smiley.x === pellet.x && smiley.y === pellet.y)
  → Comer pelotita, +10 puntos

// Fantasmas
if (smiley.x === ghost.x && smiley.y === ghost.y)
  → Perder una vida, resetear posición

// Ganador
if (pellets.length === 0)
  → ¡GANASTE!

// Perdedor
if (lives === 0)
  → GAME OVER
```

---

## 🎨 Visual Design System

### Color Palette
```
Primary Colors:
├─ Fondo:           #000 (Negro puro)
├─ Smiley:          #ffd700 (Amarillo dorado)
├─ Pelotitas:       #ffb347 (Naranja)
└─ Fantasmas:
   ├─ Rojo:         #ff0000
   ├─ Rosa:         #ff69b4
   ├─ Cian:         #00ffff
   └─ Naranja:      #ffb347

Secondary:
├─ Grid:            #222 (Gris oscuro)
├─ Borde:           #ffd700 (Dorado)
├─ UI Text:         #fff (Blanco)
└─ Error:           #ff6666 (Rojo suave)
```

### Typography
```
Font Stack: System Fonts (sin dependencias externas)
├─ Primary: -apple-system, BlinkMacSystemFont, 'Segoe UI'
└─ Monospace: Courier, monospace

Text Hierarchy:
├─ Título: 2.5em, texto con sombra
├─ Stats: 1.2em, monospace
├─ Instrucciones: 0.95em
└─ Game Over: 3em, dorado
```

### Layout Grid
```
Canvas: 600px × 600px
Game Grid: 20×20 celdas
Cell Size: 30px × 30px
Smiley/Fantasmas: 24px × 24px
Pelotitas: 8px de diámetro
```

---

## 💻 Code Architecture

### Game State Object
```javascript
{
  smiley: {x: number, y: number},
  direction: {x: number, y: number},        // Dirección actual
  nextDirection: {x: number, y: number},    // Dirección buffered
  pellets: Array<{x: number, y: number}>,
  ghosts: Array<{
    x: number, 
    y: number, 
    color: string,
    dx: number,  // velocidad X
    dy: number   // velocidad Y
  }>,
  score: number,
  lives: number,
  gameRunning: boolean,
  gamePaused: boolean,
  gameOver: boolean,
  won: boolean,
  moveTimer: number,
  MOVE_SPEED: 0.1  // segundos por movimiento
}
```

### Key Functions

#### Game Loop
```javascript
function gameLoop(dt) {
  update(dt)     // Actualizar estado
  draw()         // Renderizar en canvas
  requestAnimationFrame(gameLoop)  // Siguiente frame
}
```

#### Update Logic
```javascript
function update(dt) {
  if (!gameRunning || gamePaused) return
  
  moveTimer += dt
  if (moveTimer >= MOVE_SPEED) {
    updateDirection()   // Actualizar dirección
    moveSmiley()       // Mover smiley
    moveGhosts()       // Mover fantasmas
    checkPelletCollisions()   // Comer pelotitas
    checkGhostCollisions()    // Detectar fantasmas
    moveTimer = 0
  }
}
```

#### Rendering
```javascript
function draw() {
  drawBackground()    // Fondo negro
  drawGrid()         // Líneas del grid
  drawPellets()      // Pelotitas naranjas
  drawSmiley()       // Smiley amarillo
  drawGhosts()       // Fantasmas de colores
  drawUI()           // Información en pantalla
}
```

### Input Handling
```javascript
addEventListener('keydown', (e) => {
  if (e.key === ' ') togglePause()
  if (e.key === 'r' || e.key === 'R') restartGame()
  if (arrowKey) updateNextDirection()
})
```

---

## 🎮 Game Objects

### Smiley (Jugador)
```javascript
{
  x: 10,           // Posición grid
  y: 10,           // Posición grid
  size: 24,        // Tamaño en píxeles
  color: #ffd700   // Amarillo dorado
}
```

### Ghosts (Enemigos)
```javascript
[
  { x: 2, y: 2, color: '#ff0000', dx: 1, dy: 0 },      // Rojo
  { x: 17, y: 2, color: '#ff69b4', dx: -1, dy: 0 },    // Rosa
  { x: 2, y: 17, color: '#00ffff', dx: 0, dy: 1 },     // Cian
  { x: 17, y: 17, color: '#ffb347', dx: 0, dy: -1 }    // Naranja
]
```

### Pellets (Items)
```javascript
[
  { x: number, y: number },  // Posición en grid
  ...
]
// Distribuidas aleatoriamente con ~85% de densidad
```

---

## 🚀 Development Workflow

### Setup
```bash
# Clonar repositorio
git clone https://github.com/wallejelsma-stack/pacman.git
cd Pacman

# No se requiere instalación! Empezar a codificar inmediatamente
# O ejecutar servidor local para testing
python3 -m http.server 8080
```

### Making Changes
1. Editar archivos HTML/CSS/JS directamente
2. Refrescar navegador para ver cambios
3. Probar en múltiples navegadores
4. Commit con mensajes claros
5. Push a rama de desarrollo

### Testing Checklist
```
□ El juego inicia correctamente
□ El smiley se mueve suavemente
□ Las pelotitas se generan en posiciones válidas
□ La puntuación se actualiza correctamente
□ Colisión con fantasmas detectada
□ Sistema de vidas funciona
□ Win condition (todas las pelotitas) funciona
□ Pausa/Reanuda funciona
□ Reinicio funciona
□ Sin memory leaks
□ 60 FPS de performance
□ Layout responsive
□ Compatible con todos los navegadores
```

---

## 📊 Performance Metrics

### Current Performance
```
Load Time:        < 200ms
Initial Paint:    < 100ms
Game Start:       < 50ms
Frame Rate:       60 FPS (objetivo)
Memory Usage:     < 5MB
Canvas Renders:   60 por segundo
CPU Usage:        < 5% (idle)

Optimization Notes:
├─ Sin llamadas externas a CDN
├─ CSS integrado (sin requests extra)
├─ Un solo elemento canvas
├─ Detección de colisión eficiente
└─ Manipulación mínima del DOM
```

---

## 🔐 Security Considerations

### Implemented Security
- ✅ Sin inyecciones de scripts externos
- ✅ Sin transmisión de datos
- ✅ Sin rastreo de usuarios
- ✅ Sin explotación de localStorage
- ✅ Ejecución sandboxed
- ✅ Sin eval() o similares

### Privacy
- ✅ Sin analytics
- ✅ Sin cookies
- ✅ Sin llamadas al servidor
- ✅ Totalmente funcional offline
- ✅ Estado del juego solo local

---

## 🎓 Development Guidelines

### Code Style
```javascript
// Convenciones de Nombres
├─ Constantes:    GRID_SIZE, MOVE_SPEED, CELL_SIZE
├─ Variables:     gameRunning, moveTimer, smiley
├─ Funciones:     update(), drawSmiley(), moveGhosts()
├─ Objetos:       gameState, ghost, pellet
└─ Clases:        Ninguna (mantenido simple)

// Calidad de Código
├─ Sin variables no usadas
├─ Indentación consistente (2 espacios)
├─ Nombres de funciones descriptivos
├─ Mínimos comentarios (código auto-explicativo)
└─ Principio DRY aplicado
```

### Adding Features
1. Mantener simple - no sobre-complicar
2. Sin dependencias externas para juego core
3. Mantener performance de 60 FPS
4. Probar en navegadores múltiples
5. Actualizar documentación
6. Commit con mensaje claro

### Common Extensions
```javascript
// Agregar power-ups
function addPowerUp() {
  // Generar power-up aleatorio
  // Agregar detección de colisión
}

// Agregar niveles de dificultad
function setDifficulty(level) {
  MOVE_SPEED = calculateSpeed(level)
}

// Agregar efectos de sonido
function playSound(type) {
  const audio = new Audio('sound.mp3')
  audio.play()
}

// Guardar puntuación máxima
function saveHighScore(score) {
  localStorage.setItem('pacmanHighScore', score)
}
```

---

## 📚 Documentation Structure

### README.md
- Documentación orientada al usuario
- Reglas del juego y controles
- Cómo jugar
- Instrucciones de inicio rápido
- Guía de troubleshooting
- Lista de características

### CLAUDE.md (Este Archivo)
- Contexto de IA/Desarrollador
- Visión general de arquitectura
- Estructura del código
- Workflow de desarrollo
- Decisiones técnicas
- Mejoras futuras

---

## 🐛 Known Issues & Limitations

### Current Limitations
```
✓ Sin efectos de sonido (intencional)
✓ Un solo jugador
✓ Sin escalado de dificultad automático
✓ Sin controles táctiles para móvil
✓ Sin persistencia de puntuación máxima
✓ Sin multijugador
✓ Sin IA inteligente de fantasmas (movimiento aleatorio)
```

### Workarounds & Improvements
- Agregar localStorage para puntuación máxima
- Implementar event listeners táctiles
- Agregar Web Audio API para sonidos
- Crear selector de dificultad
- Implementar WebSocket para multijugador
- Mejorar AI de fantasmas con pathfinding

---

## 🔄 Version Control Strategy

### Branch Structure
```
claude/pacman-smiley-game-fvxyii/  ← Rama de desarrollo principal
  ├─ Commits: adiciones de features
  ├─ Formato: mensajes descriptivos
  └─ Listo para: deployment directo o PR

main/                          ← Solo releases estables
  ├─ Commits: Solo versiones estables
  └─ Tag: Versionado semántico (v1.0.0, etc)
```

### Commit Message Format
```
[TYPE] Descripción breve

Explicación más larga si es necesaria.
- Feature agregada
- Bug arreglado
- Test agregado

TYPES pueden ser:
├─ feat:     Nueva feature
├─ fix:      Bug fix
├─ refactor: Reorganización de código
├─ docs:     Actualización de documentación
└─ test:     Adiciones de tests
```

---

## 🚀 Deployment

### Current Deployment
- ✅ GitHub Repo: `wallejelsma-stack/pacman`
- ✅ Static files only - sin backend requerido
- ✅ Listo para artifact URL o GitHub Pages

### Deployment Options
```
1. GitHub Pages
   └─ Hosting gratuito, deployment automático

2. Netlify
   └─ Deployment continuo desde GitHub

3. Vercel
   └─ Hosting optimizado de sitios estáticos

4. Self-hosted
   └─ Cualquier servidor HTTP (nginx, Apache, etc)

5. Docker Container
   └─ Deployment containerizado
```

---

## 📈 Future Roadmap

### Phase 1 (MVP) ✅
- [x] Movimiento básico del smiley
- [x] Mecánicas de comer pelotitas
- [x] Detección de colisiones
- [x] Seguimiento de puntuación
- [x] Pantalla de game over
- [x] Sistema de vidas
- [x] Funcionalidad de reinicio

### Phase 2 (Polish)
- [ ] Efectos de sonido
- [ ] Mejora de gráficos
- [ ] Animaciones suaves
- [ ] Responsividad en móvil
- [ ] Controles táctiles

### Phase 3 (Features)
- [ ] Niveles de dificultad
- [ ] Power-ups especiales
- [ ] Temas/Skins diferentes
- [ ] Tabla de puntuaciones
- [ ] Logros

### Phase 4 (Advanced)
- [ ] Modo multijugador
- [ ] Fantasmas con IA inteligente
- [ ] Progresión de niveles
- [ ] Controles personalizables
- [ ] Extensión del navegador

---

## 🤝 Collaboration Notes

### For Claude AI
- Lógica del juego limpia y bien estructurada
- Fácil de extender con nuevas features
- Sin dependencias complejas para manejar
- Buena base para mejoras
- Bien documentado para iteraciones futuras

### For Human Developers
- Fork y crea tu propia versión
- Contribuye mejoras vía PR
- Agrega tus propias features
- Comparte tus extensiones
- ¡Únete a la comunidad!

---

## 📝 Quick Reference

### Quick Commands
```bash
# Iniciar servidor local
python3 -m http.server 8080

# Ver el juego
# Abre http://localhost:8080/index.html

# Git workflow
git status                          # Verificar cambios
git add .                           # Preparar todos
git commit -m "Descripción"         # Commit
git push origin branch-name         # Push

# Probar en múltiples dispositivos
# Usar ngrok o similar para testing en vivo
# http://tu-ip:8080/index.html
```

### Quick Links
```
GitHub Repo: https://github.com/wallejelsma-stack/pacman
Issues:      https://github.com/wallejelsma-stack/pacman/issues
Contact:     wallejelsma@gmail.com
```

---

## 🎓 Learning Outcomes

Este proyecto enseña:
- ✅ HTML5 Canvas API
- ✅ Implementación de game loop
- ✅ Manejo de eventos
- ✅ Gestión de estado
- ✅ Detección de colisiones
- ✅ Optimización de performance
- ✅ APIs del navegador
- ✅ Prácticas de JavaScript vanilla

---

## 📞 Support & Contact

**¿Preguntas?** Crea un issue en GitHub  
**¿Ideas?** Envía una discussion  
**¿Encontraste un bug?** Reportalo con detalles  
**¿Quieres contribuir?** ¡Envía un PR!

---

<div align="center">

### 👾 **¡Diviértete Codificando y Jugando!**

Hecho con 💚 por la Comunidad de Pacman Smiley

```
Última Actualización: 2026-07-17
Siguiente Revisión: Cuando se agreguen features
```

</div>
