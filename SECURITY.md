# SEGURIDAD DE API KEYS - IA-CHAT-TRADING

## ⚠️ IMPORTANTE: NO SUBIR API KEYS A GITHUB

### Sistema Implementado: localStorage

La aplicación utiliza **localStorage del navegador** para almacenar la API Key de forma segura:

```javascript
// La clave se guarda SOLO en tu navegador
localStorage.setItem('gemini_api_key', tuClave);

// Se recupera al cargar la página
let CLAVE_DE_API_DE_GEMINI = localStorage.getItem('gemini_api_key') || '';
```

## ✅ Ventajas de este Sistema

1. **Privacidad Total**: La clave NUNCA sale de tu navegador
2. **No se sube a Git**: El código no contiene claves hardcoded
3. **Persistencia Local**: La clave se mantiene entre sesiones
4. **Sin servidor**: No necesitas backend para gestionar claves

## 🔒 Flujo de Seguridad

1. **Usuario obtiene clave**: https://aistudio.google.com/app/apikey
2. **Usuario la pega en el modal**: Click en "⚙️ CONFIG API"
3. **Sistema la guarda**: `localStorage.setItem('gemini_api_key', clave)`
4. **Uso en requests**: Se lee de localStorage cada vez
5. **Nunca se sube a Git**: El código no tiene claves

## 🚫 Lo que NO Hacer

❌ NO escribir claves en el código:
```javascript
// ❌ NUNCA HACER ESTO
let CLAVE_DE_API_DE_GEMINI = 'AIzaSy...';
```

❌ NO subir archivos con claves:
- `config.json` con claves
- `.env` con claves
- `secrets.js` con claves

❌ NO compartir tu API Key:
- En screenshots
- En videos
- En foros
- En Discord/Telegram

## ✅ Buenas Prácticas

### 1. Usar localStorage (implementado)
```javascript
let CLAVE_DE_API_DE_GEMINI = localStorage.getItem('gemini_api_key') || '';
```

### 2. Validar antes de usar
```javascript
if (!CLAVE_DE_API_DE_GEMINI || CLAVE_DE_API_DE_GEMINI === '') {
    openConfigModal(); // Pide al usuario que configure
}
```

### 3. Logs seguros
```javascript
// Ocultar la clave en logs
console.log('URL:', apiUrl.replace(CLAVE_DE_API_DE_GEMINI, 'AIza***'));
```

### 4. .gitignore actualizado
El archivo `.gitignore` previene subir archivos sensibles accidentalmente.

## 🔄 Cómo Rotar tu API Key

Si crees que tu clave fue comprometida:

1. Ve a https://aistudio.google.com/app/apikey
2. **Elimina la clave antigua**
3. Crea una nueva clave
4. En la terminal: Click "⚙️ CONFIG API"
5. Pega la nueva clave
6. Guarda

La clave se actualiza instantáneamente sin necesidad de redesplegar.

## 📋 Checklist de Seguridad

Antes de cada commit, verifica:

- [ ] No hay claves hardcoded en el código
- [ ] El `.gitignore` está configurado
- [ ] Los logs no muestran claves completas
- [ ] La documentación no contiene claves de ejemplo reales
- [ ] Los screenshots/videos no exponen claves

## 🔍 Cómo Verificar

Buscar claves en el repositorio:

```bash
# Buscar patrones de API Keys
git grep -i "AIza"

# Buscar en historial (si es necesario limpiar)
git log -p | grep -i "AIza"
```

Si encuentras una clave en el historial de Git:
1. **Rota la clave inmediatamente** en Google AI Studio
2. Considera usar `git filter-branch` o BFG Repo-Cleaner para limpiar el historial

## 📞 Soporte

Si tu clave fue expuesta:
1. **Revoca la clave inmediatamente** en Google AI Studio
2. Genera una nueva clave
3. Actualízala en tu navegador con "⚙️ CONFIG API"

---

**Última actualización**: 2026-02-17
**Método de almacenamiento**: localStorage (navegador)
**Código limpio de claves**: ✅ Verificado
