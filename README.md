# 🧩 RRHH Stack

Repositorio principal del **stack RRHH**, que orquesta **backend** y **frontend** usando **Git Submodules**.

Este repositorio **no contiene lógica de negocio**. Su función es:
- Coordinar versiones de backend y frontend
- Centralizar Docker / docker-compose
- Facilitar despliegues y trabajo en equipo

---

## 📂 Estructura del proyecto

```text
rrhh-stack
├── docker-compose.yml
├── Dockerfile
├── rrhh-backend    (submodule → repo independiente)
├── rrhh-frontend   (submodule → repo independiente)
└── README.md
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
