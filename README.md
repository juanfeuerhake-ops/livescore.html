# livescore.html
# 🎯 Scanner de Picks + LiveScore

Dos herramientas deportivas deployadas en Vercel:

---

## 📊 Scanner de Picks (`/`)

Picks de apuestas con análisis profesional generados por IA para el Mundial 2026, UFC y Tenis.

### Características
- ⚽ **Mundial 2026** — partidos de hoy y mañana via ESPN, análisis con Groq (Llama 3.3)
- 🥊 **UFC** — cartel semanal analizado por Gemini 2.5 Flash, se refresca cada lunes
- 🎾 **Tenis** — Grand Slam > Masters 1000 > Top 5 ATP/WTA, via ESPN + Groq
- 2 picks por evento en mercados alternativos (handicap, over/under, método de victoria, etc.)
- Razonamiento detallado + edge analítico por cada pick
- Índice de confianza individual por pick

### Variables de entorno (Vercel)

| Variable | Descripción |
|----------|-------------|
| `GROQ_UFC_KEY` | API key de Groq → usada para Mundial y Tenis |
| `GEMINI_API_KEY` | API key de Gemini (Google AI Studio) → usada para UFC |

### APIs usadas
- **ESPN** (pública, sin key) → calendario de partidos del Mundial y Tenis
- **Groq** (gratuito) → análisis de fútbol y tenis
- **Gemini 2.5 Flash** (gratuito con límites) → análisis de UFC

### Archivos principales
```
/
├── index.html          ← Frontend de picks (tabs: Mundial / UFC / Tenis)
├── api/
│   └── picks.js        ← Serverless function (Vercel)
├── fixtures.json       ← Fallback de partidos si ESPN no responde
└── public/
    ├── manifest.json
    ├── sw.js
    └── icon-192.png
```

---

## 📱 LiveScore (`/scores.html`)

App de marcadores en vivo estilo 365Scores. Sin APIs de pago, todo gratuito.

### Características
- ⚽ **Fútbol** — 20 ligas: Mundial, Libertadores, Premier, La Liga, MLS, Chile, Argentina, Brasil, México y más
- 🏀 **Básquet** — NBA y NCAA en tiempo real
- 🎾 **Tenis** — ATP y WTA agrupado por torneo
- 🥊 **UFC/MMA** — cartel del evento activo
- Strip de fechas (ayer, hoy, mañana, +3 días)
- Filtros: En vivo / Próximos / Terminados
- Buscador de equipos y partidos
- Favoritos con persistencia local
- Detalle de partido: scoreboard, eventos (goles, tarjetas) y estadísticas
- Auto-refresh cada 60 segundos
- Swipe para cerrar el detalle
- PWA compatible (instalable en móvil)

### APIs usadas
- **ESPN Public API** (100% gratuita, sin key requerida)

### No requiere variables de entorno

---

## 🚀 Deploy en Vercel

```bash
# Clonar el repo
git clone https://github.com/juanfeuerhake-ops/apuestas

# Instalar Vercel CLI (opcional)
npm i -g vercel

# Deploy
vercel --prod
```

Configurar en Vercel → Settings → Environment Variables:
- `GROQ_UFC_KEY` = tu key de [console.groq.com](https://console.groq.com)
- `GEMINI_API_KEY` = tu key de [aistudio.google.com](https://aistudio.google.com)

---

## ⚠️ Disclaimer

Los picks generados por IA son análisis de contexto, **no garantías de resultados**. Las cuotas mostradas son estimaciones orientativas. Verifica siempre en tu casa de apuestas. Juega con responsabilidad.
