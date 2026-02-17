# IA-CHAT-TRADING | TERMINAL SMC

Terminal de trading con inteligencia artificial para análisis de XAUUSD (Gold) basada en Smart Money Concepts.

## ⚡ Características

- **Gráfico en Tiempo Real**: Widget de TradingView para XAUUSD
- **Chat con Gemini AI**: Asistente especializado en Smart Money Concepts
- **Generador de Señales SMC**: Operaciones completas (Entrada, SL, TP)
- **Radar de Liquidez**: Detección automática de Order Blocks, BOS y FVG
- **Estética Cyberpunk**: Diseño Matrix con animaciones neón

## 🔑 Configuración de API Key

### ⚠️ IMPORTANTE: Necesitas tu propia API Key

**El error 404 ocurre porque la API Key incluida no es válida o tiene restricciones.**

### Cómo obtener tu API Key GRATUITA:

1. **Visita**: https://aistudio.google.com/app/apikey
2. **Inicia sesión** con tu cuenta de Google
3. **Click en "Create API Key"** o "Get API Key"
4. **Copia la clave** (comienza con `AIza...`)
5. **En la terminal**: Click en el botón "⚙️ CONFIG API" (esquina superior izquierda)
6. **Pega tu clave** y guarda

### ¿Por qué no funciona con variables de entorno de Vercel?

Las variables de entorno de Vercel (`CLAVE_DE_API_DE_GEMINI`) **NO funcionan en HTML estático** porque solo están disponibles en:
- API Routes (`/api/...`)
- Server-Side Rendering (SSR)
- Edge Functions

**Solución implementada**: La aplicación usa **localStorage** del navegador para guardar tu API Key de forma segura y persistente.

## ✅ Características de Seguridad

- ✅ Tu API Key se guarda SOLO en tu navegador (localStorage)
- ✅ Nunca se envía a ningún servidor externo (excepto Google Gemini)
- ✅ Validación automática al cargar la página
- ✅ Mensajes de error detallados (404, 403, etc.)
- ✅ Modal automático si la clave es inválida
- ✅ Logs en consola para debugging

## 🚀 Despliegue en Vercel

```bash
git add .
git commit -m "Sistema de API Key con manejo de errores 404/403"
git push origin main
```

Vercel detectará automáticamente los cambios y desplegará la aplicación.

## 🐛 Solución de Problemas

### Error 404: API Key inválida
- **Causa**: La API Key no existe, fue eliminada, o no tiene permisos
- **Solución**: Genera una nueva clave en https://aistudio.google.com/app/apikey

### Error 403: Acceso denegado
- **Causa**: La API Key no tiene permisos para Gemini 1.5 Flash
- **Solución**: Verifica que tu proyecto tenga la Gemini API habilitada

### La API Key se borra al recargar
- **Causa**: Navegación privada o cookies bloqueadas
- **Solución**: Usa el navegador en modo normal y permite localStorage

## 📂 Estructura

```
ia-chat-trading/
├── index.html         # Aplicación completa (HTML + CSS + JS)
├── vercel.json        # Configuración de Vercel
└── README.md          # Este archivo
```

## 🐛 Debugging Avanzado

Si experimentas errores, abre la consola del navegador (F12) y busca:

```
🔌 Conectando con Gemini API...
📡 URL: https://generativelanguage.googleapis.com/v1beta/models/gemini-1.5-flash:generateContent?key=AIza***
📥 Respuesta HTTP: 200 OK
✅ Respuesta exitosa de Gemini
```

Si ves:
- `❌ Error de API: 404` → API Key inválida
- `❌ Error de API: 403` → Sin permisos
- `❌ Error de API: 429` → Límite de requests excedido (espera unos minutos)

## 📝 Notas Técnicas

- **Variable en código**: `CLAVE_DE_API_DE_GEMINI`
- **Storage**: localStorage del navegador
- **Modelo**: gemini-1.5-flash
- **Endpoint**: `https://generativelanguage.googleapis.com/v1beta/models/gemini-1.5-flash:generateContent`
- **Framework**: Vanilla JS (sin dependencias)
- **API Key gratuita**: Límite de 60 requests/minuto

## 🎯 Flujo de Validación

1. **Al cargar**: Verifica si hay API Key en localStorage
2. **Si está vacía**: Abre modal automáticamente
3. **Antes de cada request**: Valida que la clave exista
4. **Si hay error 404/403**: Muestra mensaje detallado y abre modal
5. **Logs en consola**: Debugging completo de cada operación
