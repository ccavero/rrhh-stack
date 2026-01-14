![CI](https://github.com/ccavero/rrhh-stack/actions/workflows/test.yml/badge.svg)

# 🧩 RRHH Stack

Repositorio principal del **Stack de Gestión de Recursos Humanos (RRHH)**, que orquesta el **backend** y el **frontend** mediante **Git Submodules**, centralizando la integración, validación y pruebas automáticas del proyecto.

---

## 📦 Estructura del proyecto

Este repositorio actúa como **orquestador** del stack completo:

```text
rrhh-stack/
├── rrhh-backend/    # API Backend (NestJS)
├── rrhh-frontend/   # Frontend (React / Vite)
└── .github/
    └── workflows/
        └── test.yml # Pipeline de CI
```

### Repositorios

- **rrhh-stack**
  - Repositorio principal
  - Infraestructura y orquestación
  - Referencias a submódulos

- **rrhh-backend**
  - Backend NestJS
  - Repositorio independiente
  - Historial Git propio

- **rrhh-frontend**
  - Frontend Next.js
  - Repositorio independiente
  - Historial Git propio

---

## 🔗 Git Submodules

Un **submódulo** es un repositorio Git incluido dentro de otro repositorio,
manteniendo su propio historial.

En este proyecto:
- Backend y frontend se desarrollan de forma independiente
- El stack define qué commit exacto de cada uno se usa
- Permite desplegar versiones consistentes del sistema completo

Los submódulos están definidos en el archivo `.gitmodules`.

---

## 🚀 Clonar el proyecto

Para clonar correctamente el proyecto con sus submódulos:

```bash
git clone git@github.com:ccavero/rrhh-stack.git
cd rrhh-stack
git submodule update --init --recursive
```

---

## 🔄 Actualizar el proyecto

Para traer cambios del repositorio principal y de los submódulos:

```bash
git pull
git submodule update --init --recursive
```

---

## 🛠️ Flujo de trabajo recomendado

### Backend o Frontend

```bash
cd rrhh-backend   # o rrhh-frontend
git checkout main
git pull
# trabajar normalmente
git add .
git commit -m "mensaje"
git push
```

Luego, desde el repositorio principal:

```bash
cd rrhh-stack
git add rrhh-backend rrhh-frontend
git commit -m "chore: actualizar submódulos"
git push
```

---

## 📌 Notas importantes

- Nunca editar código del backend o frontend directamente desde `rrhh-stack`
- Cada submódulo se versiona y commitea en su propio repositorio
- `rrhh-stack` solo guarda la referencia a los commits usados

---

## ✅ Estado

Repositorio listo para:
- Desarrollo local con Docker
- Despliegue controlado
- Escalado del equipo
