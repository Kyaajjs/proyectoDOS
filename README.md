# reservas-frontend

Frontend del sistema **Your Booking** — reservas de espacios de la Facultad de Ingeniería, UACAM.

Construido con **Vue 3 + Vite + Tailwind CSS + PrimeVue**.

## 🔗 Repositorios y enlaces

- 🔗 Frontend (fork): https://github.com/Kyaajjs/proyectoDOS
- 🔗 Backend: https://github.com/Kyaajjs/reservas-backend
- 🌐 Sitio desplegado: (URL aquí)

---

## ✨ Características

- Inicio de sesión con email/contraseña y Google OAuth
- Panel de **administrador**:
  - Ver reservaciones por día en calendario
  - Gestión de espacios (crear, eliminar)
  - Registro de nuevos usuarios
  - Historial de reservaciones
  - **Dashboard de estadísticas** *(nueva característica)*
- Panel de **usuario**:
  - Reservar espacios con calendario de horarios
  - Ver y editar reservaciones pendientes
  - Historial de reservaciones pasadas
  - **Notificación por email al reservar** *(nueva característica)*

---

## 📋 Requisitos

- [Node.js](https://nodejs.org/) v18 o superior
- [npm](https://www.npmjs.com/)
- Backend corriendo en `http://localhost:5124`

---

## 🚀 Instalación y configuración

```bash
# 1. Clonar el repositorio
git clone https://github.com/Kyaajjs/proyectoDOS.git
cd proyectoDOS

# 2. Instalar dependencias
npm install

# 3. Crear archivo de variables de entorno
echo "VITE_API_BASE=http://localhost:5124" > .env
```

---

## ▶️ Correr en desarrollo

```bash
# Terminal 1 — Frontend
npm run dev

# Terminal 2 — Backend (ver repositorio backend)
```

El frontend corre en `http://localhost:3000` por defecto.

---

## 🏗️ Build para producción

```bash
npm run build
```

Los archivos se generan en la carpeta `dist/`.

---

## ⚙️ Variables de entorno

Crea un archivo `.env` en la raíz del proyecto:

```env
VITE_API_BASE=http://localhost:5124
```

> En producción cambia la URL por la del servidor donde esté desplegado el backend.

---

## 🛠️ Tecnologías

- Vue 3 + Vite
- Vue Router
- Pinia (manejo de estado)
- Tailwind CSS
- PrimeVue + PrimeIcons
- FullCalendar
- vue3-google-login

---

## 👥 Usuarios de prueba

| Email | Contraseña | Rol |
|---|---|---|
| jcaguilar@dev.com | pass123 | admin |
| jramirez@uacam.mx | password | user |
| gmanuel@uacam.mx | gmanuel | user |