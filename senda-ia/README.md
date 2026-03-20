# Grupo Senda — Centro IA

Plataforma interna de prompts con IA para los departamentos de Grupo Senda Construcción.

---

## 📁 Estructura del proyecto

```
senda-ia/
├── index.html      ← Toda la aplicación (página única)
├── vercel.json     ← Configuración de deploy en Vercel
└── README.md       ← Este archivo
```

---

## 🚀 Deploy en 3 pasos

### Paso 1 — Subir a GitHub

1. Ve a [github.com](https://github.com) e inicia sesión (o crea cuenta gratis)
2. Haz clic en **"New repository"**
3. Nombre: `senda-ia` (o el que prefieras)
4. Visibilidad: **Private** (recomendado para uso interno)
5. Haz clic en **"Create repository"**
6. Sube los 3 archivos: `index.html`, `vercel.json`, `README.md`
   - Puedes arrastrarlos directamente en la interfaz de GitHub
   - O usar Git desde terminal:
     ```bash
     git init
     git add .
     git commit -m "primer deploy senda-ia"
     git branch -M main
     git remote add origin https://github.com/TU_USUARIO/senda-ia.git
     git push -u origin main
     ```

---

### Paso 2 — Conectar con Vercel

1. Ve a [vercel.com](https://vercel.com) e inicia sesión con tu cuenta de GitHub
2. Haz clic en **"Add New Project"**
3. Selecciona el repositorio `senda-ia`
4. Vercel detecta automáticamente que es un sitio estático
5. Haz clic en **"Deploy"**

⏱️ En menos de 1 minuto tendrás una URL pública tipo:
`https://senda-ia.vercel.app`

---

### Paso 3 — Agregar dominio personalizado (opcional)

Si tienes un dominio propio (ej: `ia.gruposenda.com`):

1. En Vercel, ve a tu proyecto → **Settings → Domains**
2. Escribe tu dominio y sigue las instrucciones para apuntar el DNS
3. Vercel configura HTTPS automáticamente

---

## 🔑 API Key de Claude (IMPORTANTE)

La página usa la API de Anthropic (Claude). Para que funcione en producción:

### Opción A — Agregar la API key directamente en el HTML (sencillo)
En `index.html`, busca la línea:
```javascript
headers: {"Content-Type": "application/json"},
```
Y agrégale el header de autorización:
```javascript
headers: {
  "Content-Type": "application/json",
  "x-api-key": "TU_API_KEY_AQUI",
  "anthropic-version": "2023-06-01",
  "anthropic-dangerous-direct-browser-access": "true"
},
```
> ⚠️ Esta opción es funcional pero expone la key en el código. Solo recomendada si el sitio es de acceso muy restringido (red interna, VPN, etc.)

### Opción B — Variables de entorno en Vercel (más seguro, requiere backend mínimo)
Para ocultar la API key, contacta a tu equipo técnico para agregar una función serverless simple en Vercel que actúe como proxy.

---

## 📌 Actualizar el sitio

Cada vez que modifiques `index.html` y hagas push a GitHub, Vercel redespliega automáticamente en segundos.

```bash
git add index.html
git commit -m "actualizo prompts de presupuesto"
git push
```

---

## 🏗️ Hecho para Grupo Senda Construcción
Centro de Inteligencia Artificial — Uso interno
