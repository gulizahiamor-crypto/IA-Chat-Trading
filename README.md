# IA-CHAT-TRADING | TERMINAL SMC

Terminal de trading con inteligencia artificial para análisis de XAUUSD (Gold) basada en Smart Money Concepts.

## ⚡ Características

- **Gráfico en Tiempo Real**: Widget de TradingView para XAUUSD
- **Chat con Gemini AI**: Asistente especializado en Smart Money Concepts
- **Generador de Señales SMC**: Operaciones completas (Entrada, SL, TP)
- **Radar de Liquidez**: Detección automática de Order Blocks, BOS y FVG
- **Estética Cyberpunk**: Diseño Matrix con animaciones neón

## 🔑 Configuración de API Key

### IMPORTANTE: Variables de Entorno en Vercel

Las variables de entorno de Vercel (`CLAVE_DE_API_DE_GEMINI`) **NO funcionan en HTML estático** porque solo están disponibles en:
- API Routes (`/api/...`)
- Server-Side Rendering (SSR)
- Edge Functions

### Solución Implementada

La aplicación usa **localStorage** del navegador para almacenar la API Key:

1. **Primera vez**: Usa la clave por defecto
2. **Configuración manual**: Click en "⚙️ CONFIG API" en la esquina superior izquierda
3. **Persistencia**: La clave se guarda localmente en tu navegador

### Obtener tu API Key de Gemini

1. Visita: https://makersuite.google.com/app/apikey
2. Crea un nuevo proyecto si no tienes uno
3. Genera una API Key (comienza con `AIza...`)
4. Pégala en el modal de configuración

## 🚀 Despliegue en Vercel

```bash
git add .
git commit -m "Sistema de API Key con validación automática"
git push origin main
```

Vercel detectará automáticamente los cambios y desplegará la aplicación.

## 🛠️ Validaciones Implementadas

- ✅ Validación automática al cargar la página
- ✅ Modal de configuración automático si la clave está vacía
- ✅ Validación antes de cada consulta a Gemini
- ✅ Manejo de errores con códigos HTTP
- ✅ Logs en consola para debugging

## 📂 Estructura

```
ia-chat-trading/
├── index.html         # Aplicación completa (HTML + CSS + JS)
├── vercel.json        # Configuración de Vercel
└── README.md          # Este archivo
```

## 🐛 Debugging

Si experimentas errores:

1. Abre la consola del navegador (F12)
2. Verifica los logs de `console.error`
3. Comprueba que la API Key comience con `AIza`
4. Verifica que tu API Key tenga permisos para Gemini 1.5 Flash

## 📝 Notas Técnicas

- **Variable en código**: `CLAVE_DE_API_DE_GEMINI`
- **Storage**: localStorage del navegador
- **Modelo**: gemini-1.5-flash
- **Framework**: Vanilla JS (sin dependencias)
