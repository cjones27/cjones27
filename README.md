# Kreditop 🚀

Kreditop es una app que despliega las transacciones de la compañia. La app la puedes encontrar [aquí](http://cjmtests.click/).

## Requerimientos

* NodeJS
* NextJS
* Tailwindcss
* Typescript
* Express
* Autorización al cluster de MongoDB

## Instalación

El programa se divide en dos aplicaciones, una para el frontend y otra para el baackend. Al ser proyectos en javascript, la información necesaria para levantarlos se encuentra en el package.json. Por lo tanto, solo se necesita correr los siguientes comandos. El desarrollo de ambas aplicaciones fue hecho con pnpm, pero npm y yarn deberían funcionar correctamente también.

### Instalación de requerimientos

```
# NodeJS
sudo apt install curl
curl -fsSL https://deb.nodesource.com/setup_16.x | sudo -E bash - &&\
sudo apt install nodejs
node -v # Confirmar que sea versión 16.x
```

Teniendo NodeJS y NPM, el resto de los requerimientos viene definido en el package.json, por lo que solo hace falta instalarlos y levantar las aplicaciones, corriendo los siguientes comandos.

#### Backend
```bash
pnpm i
pnpm run start
```

#### Frontend
```bash
pnpm i
pnpm run build && pnpm run start
```

## Arquitectura de solución

La arquitectura corresponde a una típica aplicación dividida en frontend y backend, en la cual el frontend solicita data al backend. El backend por su lado recibe las solicitudes, y pide la data a la base de datos, en este caso a MongoDB. Se decidió usar MongoDB porque era una technología que quería conocer en más profundidad y porque permite guardar documentos de forma muy fácil y el setup del servicio es muy rápido.

Se incluye diagrama de arquitectura.

![Untitled Diagram](https://user-images.githubusercontent.com/48262167/203509040-96ad3d49-5b28-4c67-9475-7f0567498979.png)

## Estructura de las aplicaciones

Las aplicaciones están ordenadas internamente de la siguientes formas.

### Backend
```
.
├── app.js
├── package.json
├── node_modules/
├── .env
└── pnpm-lock.yaml
```

### Frontend

```
.
├── components
│   ├── balance.tsx
│   ├── header.tsx
│   ├── searchBar.tsx
│   └── transaction.tsx
├── global.d.ts
├── next-env.d.ts
├── next.config.js
├── node_modules/
├── out
│   ├── 404.html
│   ├── _next/
│   ├── app.html
│   ├── bank_pic.png
│   ├── favicon.ico
│   ├── index.html
│   └── vercel.svg
├── package.json
├── pages
│   ├── _app.tsx
│   ├── api/
│   ├── app.tsx
│   └── index.tsx
├── pnpm-lock.yaml
├── postcss.config.js
├── public
│   ├── bank_pic.png
│   ├── favicon.ico
│   └── vercel.svg
├── styles
│   ├── Home.module.css
│   └── globals.css
├── tailwind.config.js
├── tsconfig.json
└── utils
    └── utils.ts
```

## Aspectos funcionales

En esta tarea se realizó exitosamente el objetivo base de desplegar los movimientos de transacciones entregados. Adicionalmente, se agregaron distintas funcionalidades para potenciar la aplicación.

| Nombre | Cumplimiento | Descripción |
|--------|:------------:|-------------|
| Base tarea | ✅ | Listar movimientos |
| Buscador de movimientos | ✅ | Search bar permite encontrar movimientos en base de datos por textos según descripción e id |
|Paginación de movimientos | ✅ | Se paginaron los elementos para aumentar la velocidad de carga y escalabilidad |
| Orden cronologico | ✅ | Los movimientos están ordenados cronologicamente |
| Coloración condicional | ✅ | Render condicional según si el movimiento es positivo o negativo |
| Despliegue de balance | ✅ | Se despliega el balance actual de la cuenta |
| Loader | ✅ | En caso de estar esperando información de la API, se muestra un loader en el lugar |

## Aspectos no funcionales

| Nombre | Cumplimiento | Descripción |
|--------|:------------:|-------------|
| Deploy de la tarea | ✅ | Se deployeo la tarea en AWS EC2 y S3 |
| API | ✅ | Se construyó una API para solicitar y entregar los datos |
| Base de datos | ✅ | Se utilizó MongoDB para almacenar los datos de la aplicación |
| Busqueda eficiente | ✅ | Se creó un índice de texto para eficientar la búsqueda en MongoDB
| Debounce en búsqueda instantanea | ✅ | Se utilizó el método de debounce para evitar llamar la búsqueda en base de datos en cada keystroke del usuario en el buscador |
| Paginación | ✅ | Se paginó la busqueda en base de datos para aumentar la velocidad y eficiencia de las busquedas |
| Secretos seguros | ✅ | Los secretos de la aplicación se entregan de forma aparte en un .env |
| Data segura | ✅ | La data se puede acceder solo desde el backend |
| Uso de Typescript | 🚧 | Uso en frontend pero no en un 100% y en backend no fue implementado |

## Aspectos a mejorar

Estos son aspectos que fueron considerados y agregan valor tanto funcional como no funcionalmente pero que no se alcanzaron a agregar en la tarea.

| Nombre |
|--------|
| Login para entrar a la aplicación |
| Conección segura via HTTPS |
| Crear movimientos |
| Testing |
| Typescript en backend |
