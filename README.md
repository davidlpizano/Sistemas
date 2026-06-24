<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:FCC624,100:FF6F00&height=220&section=header&text=SysAdmin%20Hub&fontSize=55&fontColor=ffffff&animation=twinkling&fontAlignY=38&desc=David%20Lopez%20%7C%20ASIR&descSize=20&descAlign=50&descAlignY=60&descColor=ffffff" alt="Sistemas Banner" width="100%">

**Administracion de sistemas, virtualizacion, scripting y homelab en produccion con +15 servicios Docker.**

[![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black)](#)
[![Windows Server](https://img.shields.io/badge/Windows_Server-0078D6?style=flat-square&logo=windows&logoColor=white)](#)
[![PowerShell](https://img.shields.io/badge/PowerShell-5391FE?style=flat-square&logo=powershell&logoColor=white)](#)
[![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)](#)
[![Nginx](https://img.shields.io/badge/Nginx_Proxy_Manager-009639?style=flat-square&logo=nginx&logoColor=white)](#)
[![Bash](https://img.shields.io/badge/Bash-4EAA25?style=flat-square&logo=gnubash&logoColor=white)](#)

</div>

<br/>

## 🎯 Sobre este repositorio

Biblioteca de practicas, guias y **scripts de automatizacion** para la administracion de sistemas operativos. Parte de mi formacion en **ASIR** con orientacion a Ciberseguridad.

Aqui demuestro mi capacidad para levantar infraestructuras desde cero, interconectar servicios (Active Directory, DNS, File Servers) y optimizar tareas repetitivas mediante **PowerShell** y **Bash**. Ademas, mantengo un **homelab en produccion** sobre un NAS UGREEN con mas de 15 servicios Docker auto-alojados, accesibles por subdominios con SSL y monitorizados en tiempo real.

<br/>

## 🏠 Homelab — Infraestructura real

<div align="center">

Mi homelab corre sobre un **UGREEN NAS** con Docker. Todos los servicios estan desplegados como contenedores con persistencia en volumenes.

</div>

<br/>

<details>
<summary><b>🌐 Ver arquitectura de red</b></summary>
<br/>

```
Internet
    │
    ▼
┌──────────────────────┐
│   Router / Firewall   │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────────────────────────────────┐
│               UGREEN NAS (Docker)                │
│                                                  │
│  ┌────────────────────────────────────────────┐  │
│  │  Nginx Proxy Manager (NPM)                 │  │
│  │  Wildcard SSL + Reverse Proxy              │  │
│  │  Subdominios HTTPS → todos los servicios   │  │
│  └────────────────────────────────────────────┘  │
│                                                  │
│  ┌───────────┐  ┌───────────┐  ┌───────────┐    │
│  │  Pi-hole  │  │  Grafana  │  │Prometheus │    │
│  │    DNS    │  │ Dashboards│  │ Metricas  │    │
│  └───────────┘  └───────────┘  └───────────┘    │
│                                                  │
│  ┌───────────┐  ┌───────────┐  ┌───────────┐    │
│  │ Nextcloud │  │Vaultwarden│  │Uptime Kuma│    │
│  │   Cloud   │  │Contraseñas│  │ Monitoreo │    │
│  └───────────┘  └───────────┘  └───────────┘    │
│                                                  │
│  ┌───────────┐  ┌───────────┐  ┌───────────┐    │
│  │Firefly III│  │   Plex    │  │ Navidrome │    │
│  │ Finanzas  │  │   Media   │  │  Musica   │    │
│  └───────────┘  └───────────┘  └───────────┘    │
│                                                  │
│  ┌───────────┐  ┌───────────┐  ┌───────────┐    │
│  │ Homepage  │  │ Speedtest │  │qBittorrent│    │
│  │ Dashboard │  │  Tracker  │  │ Descargas │    │
│  └───────────┘  └───────────┘  └───────────┘    │
│                                                  │
│  ┌───────────┐  ┌───────────┐  ┌───────────┐    │
│  │Home Assist│  │    n8n    │  │ Minecraft │    │
│  │ Domotica  │  │ Automatiz.│  │  Server   │    │
│  └───────────┘  └───────────┘  └───────────┘    │
└──────────────────────────────────────────────────┘
```

</details>

<br/>

### 📋 Stack de servicios

<div align="center">

| Categoria | Servicio | Funcion |
| :---: | :--- | :--- |
| 🔀 | **Nginx Proxy Manager** | Reverse proxy + certificado SSL wildcard |
| 🛡️ | **Pi-hole** | DNS server + bloqueador de publicidad |
| 📊 | **Homepage** | Dashboard centralizado |
| ☁️ | **Nextcloud** | Nube privada (archivos, calendario, contactos) |
| 🔑 | **Vaultwarden** | Gestor de contraseñas (compatible Bitwarden) |
| 📈 | **Grafana** | Dashboards de monitorizacion |
| 📈 | **Prometheus + Node Exporter** | Recolector y exportador de metricas |
| ✅ | **Uptime Kuma** | Monitorizacion de disponibilidad |
| 💰 | **Firefly III** | Gestion de finanzas personales |
| 🎬 | **Plex** | Servidor multimedia |
| 🎵 | **Navidrome** | Servidor de musica (Subsonic) |
| 🌐 | **Speedtest Tracker** | Historial de velocidad de Internet |
| ⬇️ | **qBittorrent** | Cliente de descargas |
| 🏡 | **Home Assistant** | Domotica y automatizacion del hogar |
| ⚡ | **n8n** | Automatizacion de workflows |
| 🎮 | **Minecraft** | Servidor de juego |

</div>

<br/>

<table>
<tr>
<td width="50%" valign="top">

### 🔒 Seguridad

- Certificado SSL wildcard via NPM
- Pi-hole filtrando publicidad y telemetria
- Vaultwarden como gestor de credenciales
- Solo acceso HTTPS por subdominios
- Prometheus restringido a red interna

</td>
<td width="50%" valign="top">

### 📊 Monitorizacion

- **Prometheus** + Node Exporter para metricas
- **Grafana** con dashboards:
  - Node Exporter Full (ID 1860)
  - Prometheus 2.0 Overview (ID 3662)
- **Uptime Kuma** para disponibilidad

</td>
</tr>
</table>

<br/>

## 📂 Contenido del repositorio

<table>
<tr>
<td width="50%" valign="top">

### 🐧 Entorno Linux
- Gestion de usuarios, grupos y permisos
- Servicios: SSH, Apache/Nginx, FTP
- Monitorizacion de procesos y recursos
- Hardening y Firewall (UFW/iptables)

### 🪟 Windows Server & AD
- Controladores de dominio (DC)
- GPOs (Politicas de Grupo)
- Almacenamiento y cuotas

</td>
<td width="50%" valign="top">

### ⚙️ Scripting y Automatizacion
- **PowerShell:** Creacion masiva de usuarios AD, backups, informes
- **Bash:** Mantenimiento y auditoria en Linux

### 📦 Virtualizacion y Contenedores
- VMs con VirtualBox/VMware
- **Docker:** +15 servicios en UGREEN NAS
- Docker Compose y gestion de volumenes

</td>
</tr>
</table>

<br/>

## 🚀 Como usar este material

> **Importante:** Muchos scripts requieren privilegios de administrador (`Run as Administrator` en Windows o `sudo` en Linux). Lee siempre los comentarios internos del codigo antes de ejecutar.

<br/>

<div align="center">

*"Un administrador que automatiza, es un administrador con tiempo para innovar."*

<br/>

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:FCC624,100:FF6F00&height=100&section=footer" width="100%"/>

**[⬅️ Volver a mi perfil principal](https://github.com/davidlpizano/davidlpizano)**

</div>
