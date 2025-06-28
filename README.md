# 🐧 Evolution API Dockerizado para VPS Linux

Este proyecto está basado en el repositorio oficial de [Evolution API](https://github.com/EvolutionAPI/evolution-api), una solución para enviar mensajes de WhatsApp a través de una API sencilla y potente.

Este entorno incluye:

- Evolution API
- Redis
- PostgreSQL
- Variables de entorno configurables
- Documentación clara para exponer puertos y asegurar el servicio

> Ideal para los que deseen tener la Evolution API funcionando en un VPS minutos, sin configuraciones complicadas ni instalaciones manuales.

---

## ✅ Requisitos

Asegúrate de tener instalados:

```bash
docker -v
docker compose version
```

Si no los tienes, puedes instalarlos con:

- [Docker Engine](https://docs.docker.com/engine/install/)
- [Docker Compose Plugin](https://docs.docker.com/compose/install/)

También se recomienda agregar tu usuario al grupo `docker` para evitar usar `sudo`:

- [Post-installation steps for Linux] (https://docs.docker.com/engine/install/linux-postinstall/)

## 🚀 Instalación del proyecto

### 1. Clona este repositorio

```bash
git clone https://github.com/devalexcode/docker-evolution-api.git
cd docker-evolution-api
```

### 2. Crea el archivo `.env`

```bash
cp .env.example .env
```

## ⚙️ Configuración del archivo `.env`

Antes de levantar los servicios, asegúrate de crear y configurar tu archivo `.env`:

```bash
# Abre el editor de código para editar los valores por defecto
nano .env
```

Edita el archivo `.env` con tus propios valores:

```dotenv
############################################
# 🔐 Evolution API
############################################

# ------------------------------------------
AUTHENTICATION_API_KEY=api_key # Clave de autenticación para Evolution API (Contraseña de administrador)
# ------------------------------------------
EVOLUTION_API_PORT=8080 # Puerto de escucha para Evolution API
# ------------------------------------------
CONFIG_SESSION_PHONE_VERSION=2.3000.1023204200 # Whatsapp Web version for baileys channel: https://web.whatsapp.com/check-update?version=0&platform=web
# ------------------------------------------

############################################
# 🐘 PostgreSQL
############################################

# ------------------------------------------
POSTGRESS_USER=user # Usuario de PostgreSQL (POR SEGURIDAD MODIFICA ESTE VALOR)
# ------------------------------------------
POSTGRESS_PASS=123456 # Contraseña de PostgreSQL (POR SEGURIDAD MODIFICA ESTE VALOR)
# ------------------------------------------
POSTGRESS_PORT=5432 # Puerto de PostgreSQL (Se sugiere no modificar)
# ------------------------------------------

############################################
# 🧠 Redis
############################################

REDIS_PORT=6379 # Puerto de Redis (Se sugiere no modificar)
```

### 3. Levanta los servicios

```bash
docker compose up -d
```

Este comando:

- Construye las imágenes necesarias
- Levanta los contenedores definidos en `docker-compose.yml`
- Todo en segundo plano (`-d`)

---

## 📦 Verifica que el contenedor esté en ejecución

Después de levantar el entorno con `docker compose up -d`, puedes verificar que Evolution API se esté ejecutando correctamente con:

```bash
docker ps
```

Deberías ver una salida similar a esta:

```bash
CONTAINER ID   IMAGE                            COMMAND                  CREATED          STATUS              PORTS                                                                                   NAMES
e3b6d8e6c317   atendai/evolution-api:latest     "/bin/bash -c '. ./D…"   28 seconds ago   Up 26 seconds       0.0.0.0:8080->8080/tcp, [::]:8080->8080/tcp                                            evolution_api
```

---

## 🌐 Acceso a la aplicación

Accede desde el navegador (o usa `curl`) en:

```
http://IP_DEL_SERVIDOR:8080/manager
```

![Diagrama del entorno Evolution API](docs/login.png)

> Ingresa en el campo API Key Global el valor que asignaste en el archivo .env  
> Reemplaza `8080` con el puerto configurado si usaste otro.  
> Si estás en localhost, puedes usar `http://localhost:8080/manager`

---

## 👨‍💻 Autor

Desarrollado por [Alejandro Robles | Devalex ](http://devalexcode.com)  
¿Necesitas que lo haga por ti? ¡Estoy para apoyarte! 🤝 http://devalexcode.com/soluciones/evolution-api-whatsapp-en-servidor-vps

¿Dudas o sugerencias? ¡Contribuciones bienvenidas!
