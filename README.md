<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=FCC624&height=200&section=header&text=SysAdmin%20Hub&fontSize=50&fontColor=ffffff&animation=twinkling&fontAlignY=40&desc=David%20Lopez%20%7C%20ASIR&descSize=20&descAlign=50&descAlignY=62&descColor=ffffff" alt="Sistemas Banner">

**Configuración de servidores, virtualización, gestión de usuarios, automatización con scripting y homelab en producción.**

[![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)](#)
[![Windows Server](https://img.shields.io/badge/Windows_Server-0078D6?style=for-the-badge&logo=windows&logoColor=white)](#)
[![PowerShell](https://img.shields.io/badge/PowerShell-5391FE?style=for-the-badge&logo=powershell&logoColor=white)](#)
[![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)](#)
[![Nginx](https://img.shields.io/badge/Nginx_Proxy_Manager-009639?style=for-the-badge&logo=nginx&logoColor=white)](#)

</div>

---

## 🎯 Sobre este repositorio

Este espacio sirve como biblioteca de mis prácticas, guías y **scripts de automatización** relacionados con la Administración de Sistemas Operativos. Es parte de mi evolución como técnico **ASIR** y futuro perfil enfocado en Ciberseguridad.

Aquí demuestro mi capacidad para levantar infraestructuras desde cero, interconectar servicios (Active Directory, DNS, File Servers) y optimizar tareas repetitivas mediante **PowerShell** y **Bash**.

Además, mantengo un **homelab en producción** sobre un NAS UGREEN con más de 15 servicios Docker auto-alojados, accesibles por subdominios con SSL y monitorizados en tiempo real.

---

## 🏠 Homelab — Infraestructura real en producción

Mi homelab corre sobre un **UGREEN NAS** con Docker, gestionado a través de la interfaz nativa del NAS. Todos los servicios están desplegados como contenedores Docker con persistencia de datos en volúmenes.

### 🌐 Arquitectura de red

```
Internet
    │
    ▼
┌─────────────────────┐
│   Router / Firewall  │
└────────┬────────────┘
         │
         ▼
┌─────────────────────────────────────────────┐
│              UGREEN NAS (Docker)            │
│                                             │
│  ┌─────────────────────────────────────┐    │
│  │  Nginx Proxy Manager (NPM)         │    │
│  │  Wildcard SSL + Reverse Proxy      │    │
│  │  Subdominios → todos los servicios  │    │
│  └─────────────────────────────────────┘    │
│                                             │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐    │
│  │ Pi-hole  │ │ Grafana  │ │ Prometheus│   │
│  │   DNS    │ │ Dashboards│ │ Métricas │   │
│  └──────────┘ └──────────┘ └──────────┘    │
│                                             │
│  ┌──────────┐ ┌──────────┐ ┌───────────┐   │
│  │Nextcloud │ │Vaultwarden│ │Uptime Kuma│  │
│  │  Cloud   │ │Contraseñas│ │Monitoreo  │  │
│  └──────────┘ └──────────┘ └───────────┘   │
│                                             │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐    │
│  │Firefly III│ │  Plex   │ │Navidrome │    │
│  │ Finanzas │ │  Media   │ │  Música  │    │
│  └──────────┘ └──────────┘ └──────────┘    │
│                                             │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐    │
│  │Homepage  │ │Speedtest │ │qBittorrent│   │
│  │Dashboard │ │ Tracker  │ │ Descargas│    │
│  └──────────┘ └──────────┘ └──────────┘    │
│                                             │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐    │
│  │Home Asst.│ │   n8n    │ │Minecraft │    │
│  │  Domótica│ │Automatiz.│ │  Server  │    │
│  └──────────┘ └──────────┘ └──────────┘    │
└─────────────────────────────────────────────┘
```

### 📋 Stack de servicios

| Servicio | Función |
| :--- | :--- |
| **Nginx Proxy Manager** | Reverse proxy + certificado SSL wildcard |
| **Pi-hole** | DNS server + bloqueador de publicidad para toda la red |
| **Homepage** | Dashboard centralizado de todos los servicios |
| **Nextcloud** | Nube privada (archivos, calendario, contactos) |
| **Vaultwarden** | Gestor de contraseñas (compatible Bitwarden) |
| **Grafana** | Dashboards de monitorización (Node Exporter, Prometheus) |
| **Prometheus** | Recolector de métricas del sistema |
| **Node Exporter** | Exportador de métricas del hardware/OS |
| **Uptime Kuma** | Monitorización de disponibilidad de servicios |
| **Firefly III** | Gestión de finanzas personales |
| **Plex** | Servidor multimedia (películas, series) |
| **Navidrome** | Servidor de música (compatible Subsonic) |
| **Speedtest Tracker** | Historial de velocidad de Internet |
| **qBittorrent** | Cliente de descargas |
| **Home Assistant** | Domótica y automatización del hogar |
| **n8n** | Automatización de workflows (bajo demanda) |
| **Minecraft** | Servidor de juego (bajo demanda) |

### 🔒 Seguridad aplicada

- Certificado SSL wildcard gestionado por NPM para todos los subdominios
- Pi-hole como DNS local filtrando publicidad y telemetría a nivel de red
- Vaultwarden como gestor de contraseñas centralizado
- Acceso a servicios solo por subdominios HTTPS (no puertos expuestos directamente)
- Prometheus restringido a red interna, sin acceso público

### 📊 Monitorización

- **Prometheus** recolecta métricas del sistema vía Node Exporter
- **Grafana** con dashboards importados:
  - Node Exporter Full (ID 1860) — CPU, RAM, disco, red, temperatura
  - Prometheus 2.0 Overview (ID 3662) — estado del propio Prometheus
- **Uptime Kuma** monitoriza la disponibilidad de cada servicio

---

## 📂 Estructura del repositorio

El contenido está dividido por entornos y tecnologías:

### 1. 🐧 Entorno Linux
- Gestión avanzada de usuarios, grupos y permisos (chmod, chown, ACLs).
- Configuración de servicios básicos (SSH, Apache/Nginx, FTP).
- Monitorización de procesos y recursos del sistema.
- Hardening básico y configuración del Firewall (UFW/iptables).

### 2. 🪟 Windows Server & Active Directory
- Despliegue de controladores de dominio (DC).
- Creación y gestión de **GPOs** (Políticas de Grupo).
- Administración de almacenamiento y cuotas.

### 3. ⚙️ Scripting y Automatización
- **PowerShell:** Scripts para creación masiva de usuarios en AD, backups programados e informes del sistema.
- **Bash:** Scripts de mantenimiento y auditoría en servidores Linux.

### 4. 📦 Virtualización y Contenedores
- Despliegue de máquinas virtuales con VirtualBox/VMware.
- **Docker:** despliegue y gestión de +15 servicios en contenedores sobre UGREEN NAS.
- Docker Compose para orquestación de stacks multi-contenedor.
- Gestión de volúmenes, redes y actualizaciones de imágenes.

---

## 🚀 Cómo utilizar este material

Si vas a probar alguno de mis scripts de PowerShell o Bash, **asegúrate de leer los comentarios internos del código**. Muchos scripts requieren ser ejecutados con privilegios de administrador (`Run as Administrator` en Windows o `sudo` en Linux) y podrían modificar la configuración de tu máquina si no se adaptan a tu entorno.

---

<div align="center">

*"Un administrador que automatiza, es un administrador con tiempo para innovar."*

**[⬅️ Volver a mi perfil principal](https://github.com/davidlpizano/davidlpizano)**

</div>
