# Auris Pole — CRM Studio

CRM de gestión para **Auris Pole Dance Studio** (Cuenca, Ecuador): alumnas,
instructores, horarios, reservas con anti-overbooking, pagos, membresías por
paquetes, reportes y un **bot de WhatsApp** simulado para reservas.

La aplicación es un **único archivo estático** (`index.html`) — no requiere
build ni servidor. Los datos se sincronizan con **Firebase Firestore**.

---

## 🚀 Desplegar (GitHub → Vercel)

### 1. Subir a GitHub

```bash
# dentro de la carpeta del proyecto
git init
git add .
git commit -m "Auris Pole CRM"
git branch -M main
git remote add origin https://github.com/TU-USUARIO/auris-pole-crm.git
git push -u origin main
```

> Crea primero el repositorio vacío en https://github.com/new
> (sin README, para que no haya conflicto con el push).

### 2. Desplegar en Vercel

1. Entra a https://vercel.com → **Add New… → Project**.
2. **Import** el repositorio `auris-pole-crm` de GitHub.
3. Configuración (Vercel lo detecta solo, es un sitio estático):
   - **Framework Preset:** `Other`
   - **Build Command:** *(vacío)*
   - **Output Directory:** *(vacío / raíz)*
4. Pulsa **Deploy**. En ~20 s tendrás una URL pública (`*.vercel.app`).

Cada `git push` a `main` vuelve a desplegar automáticamente.

---

## 🔥 Firebase

La configuración del cliente está embebida en `index.html` (`firebaseConfig`).
Las claves del SDK web de Firebase son **públicas por diseño** — la seguridad
real se controla con las **reglas de Firestore**.

> ⚠️ **Recomendación de seguridad:** actualmente las reglas permiten
> lectura/escritura abierta. Antes de uso en producción, restríngelas en
> Firebase Console → Firestore → Rules (por ejemplo, exigir autenticación).

---

## 🔑 Accesos del sistema

- **Admin:** código de acceso `AURIS2025` (configurable dentro de la app).
- **Instructor/a:** últimos 5 dígitos de su teléfono registrado.

---

## 📁 Estructura

```
index.html      → Aplicación completa (CRM + landing + bot)
vercel.json     → Config de despliegue estático
.gitignore
README.md
```
