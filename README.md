# Sistema de Gestión de Farmacia

![Docker](https://img.shields.io/badge/Docker-2CA5E0?style=for-the-badge&logo=docker&logoColor=white)
![Vue.js](https://img.shields.io/badge/Vue.js-35495E?style=for-the-badge&logo=vuedotjs&logoColor=4FC08D)
![Node.js](https://img.shields.io/badge/Node.js-43853D?style=for-the-badge&logo=node.js&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-005C84?style=for-the-badge&logo=mysql&logoColor=white)

Aplicación fullstack para gestión de farmacias con:
- **Frontend**: Vue 3 + Vite
- **Backend**: Node.js + Express
- **Base de datos**: MySQL 8.0
- **Proxy**: Nginx

## 🚀 Instalación

### Requisitos previos
- Docker 20.10+ ([Instalar Docker](https://docs.docker.com/get-docker/))
- Docker Compose 2.0+ ([Instalar Docker Compose](https://docs.docker.com/compose/install/))
- Git 2.30+ ([Instalar Git](https://git-scm.com/downloads))

### Clonar el proyecto
```bash
git clone --recurse-submodules git@github.com:Th3rick2002/sistema-famacia-san-jose.git
cd sistema-farmacia-san-jose
```

## 🛠 Configuración

1. **Crear archivo `.env`** en la raíz del proyecto:
```bash
cp .env.example .env
```

2. **Editar las variables necesarias**:
```env
# Backend
DATABASE=farmacia_san_jose
USERNAME=admin
PASSWORD=password-segura
PORT_APP=3000
JWT_SECRET=clave-secreta-jwt
```

## 🐳 Comandos Docker

### Entorno de desarrollo
```bash
# Construir imágenes e iniciar contenedores
docker-compose up -d --build

# Detener todos los servicios
docker-compose down

# Ver logs en tiempo real
docker-compose logs -f

# Reconstruir servicios específicos
docker-compose up -d --build backend
```

### Entorno de producción
```bash
# Construir y desplegar
docker-compose -f docker-compose.yml up -d --build

# Forzar recreación de contenedores
docker-compose up -d --force-recreate
```

# 🔄 Flujo de trabajo con Git

### Estructura de repositorios
```
sistema-farmacia-san-jose/ (Padre)
├── sistema-de-gestion-de-farmacia---backend/ (Submódulo)
└── sistema-de-gestion-de-farmacia---frontend/ (Submódulo)
```

### Comandos esenciales
```bash
# Actualizar proyecto completo
git pull origin main
git submodule update --init --recursive

# Trabajar en backend
cd sistema-de-gestion-de-farmacia---backend
git checkout -b feature/nueva-funcionalidad
# Realizar cambios...
git add .
git commit -m "Descripción de cambios"
git push origin feature/nueva-funcionalidad

# Actualizar referencia en padre
cd ..
git add sistema-de-gestion-de-farmacia---backend
git commit -m "Actualiza backend con nueva funcionalidad"
git push origin main
```

## 🌐 Acceso a los servicios

| Servicio | URL de desarrollo | URL de producción |
|----------|------------------|-------------------|
| Frontend | http://localhost:5173 | http://tudominio.com |
| Backend | http://localhost:3000/api | http://api.tudominio.com |
| Nginx | http://localhost | http://tudominio.com |

## 🚨 Solución de problemas

### Migraciones no ejecutadas
```bash
# Ejecutar migraciones manualmente
docker-compose exec backend sh -c "pnpx sequelize-cli db:migrate"

# Ejecutar seeders
docker-compose exec backend sh -c "pnpx sequelize-cli db:seed:all"
```

### Problemas con la base de datos
```bash
# Ver logs de MySQL
docker-compose logs db

# Conectarse a la base de datos
docker-compose exec db mysql -uadmin -p farmacia_san_jose
```

### Reconstruir todo desde cero
```bash
docker-compose down -v
docker-compose up -d --build
```

## 📌 Notas importantes

1. **El backend ejecuta automáticamente migraciones al iniciar**
2. **Para desarrollo frontend**, usa:
   ```bash
   cd sistema-de-gestion-de-farmacia---frontend
   npm run dev
   ```
3. **Las variables de entorno deben coincidir en ambos entornos**
4. **Nginx configura las rutas**:
    - `/` → Frontend
    - `/api` → Backend

## 📁 Estructura del proyecto

```
sistema-farmacia-san-jose/
├── docker-compose.yml
├── docker-compose.override.yml
├── .env.example
├── .env
├── .gitmodules
├── README.md
├── sistema-de-gestion-de-farmacia---backend/
│   ├── src/
│   ├── migrations/
│   ├── seeders/
│   ├── package.json
│   └── Dockerfile
├── sistema-de-gestion-de-farmacia---frontend/
│   ├── src/
│   ├── public/
│   ├── package.json
│   └── Dockerfile
└── nginx
    └── nginx.conf
```

## 🤝 Contribución

1. Fork el proyecto
2. Crea una rama para tu feature (`git checkout -b feature/AmazingFeature`)
3. Commit tus cambios (`git commit -m 'Add some AmazingFeature'`)
4. Push a la rama (`git push origin feature/AmazingFeature`)
5. Abre un Pull Request

## 📄 Licencia

Este proyecto está bajo la Licencia MIT - ver el archivo [LICENSE](LICENSE) para más detalles.

---

**Desarrollado para Farmacia San José**