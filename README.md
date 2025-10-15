# Tarea-7

## Índice  

1. [Herramientas de monitoreo y análisis](#1-herramientas-de-monitoreo-y-análisis)  
   1.1. [Significado de htop](#11-significado-de-htop)  
   1.2. [Complemento con glances, ifconfig, nmap y lynis](#12-complemento-con-glances-ifconfig-nmap-y-lynis)  

2. [Direcciones IP](#2-direcciones-ip)  
   2.1. [Qué es IPv4 e IPv6](#21-qué-es-ipv4-e-ipv6)  
   2.2. [Comandos en Ubuntu para explorarlas](#22-comandos-en-ubuntu-para-explorarlas)  

3. [Instalación en Arch Linux](#3-instalación-en-arch-linux)  
   3.1. [Qué es Arch Linux](#31-qué-es-arch-linux)  
   3.2. [Proceso paso a paso de instalación](#32-proceso-paso-a-paso-de-instalación)  

4. [Creación del repositorio y documentación](#4-creación-del-repositorio-y-documentación)  

---

## 1. Herramientas de monitoreo y análisis  

### 1.1 Significado de htop  

**a. ¿Qué es htop?**  
`htop` es una herramienta de monitoreo de procesos en tiempo real para sistemas Linux. Muestra información detallada del uso del CPU, memoria RAM, procesos activos, carga del sistema y más. Es una versión mejorada del clásico `top`, con una interfaz más visual y fácil de usar.  

**b. ¿Qué información muestra?**  
- **CPU:** Porcentaje de uso por núcleo.  
- **Memoria:** Uso actual y disponible.  
- **Swap:** Memoria virtual en uso.  
- **Procesos:** Identificador (PID), usuario, estado, prioridad y consumo de recursos.  
- **Carga del sistema:** Promedios de carga de los últimos minutos.

- **Área de procesos (principal):**  
   - **PID:** Identificador del proceso.  
   - **USER:** Usuario que ejecuta el proceso.  
   - **PRI / NI:** Prioridad y valor nice (afecta planificación). NI negativo = mayor prioridad.  
   - **VIRT / RES / SHR:** Memoria virtual, memoria residente (física) y memoria compartida.  
   - **S:** Estado del proceso (R = Running, S = Sleeping, D = Uninterruptible sleep, Z = Zombie, T = Stopped).  
   - **%CPU / %MEM:** Porcentajes — siempre interpretar con la nota de si es por núcleo o total (por defecto, %CPU muestra porcentaje total disponible).  
   - **TIME+:** Tiempo de CPU consumido por ese proceso desde su inicio.  
   - **Command:** Ruta o nombre del ejecutable y sus argumentos.
 
     
-**Teclas de función y atajos importantes (lista exhaustiva)**

- `F1` — Help (ayuda rápida).  
- `F2` — Setup (configuración visual: columnas, colores).  
- `F3` — Search (buscar proceso por nombre).  
- `F4` — Filter (filtrar por expresión).  
- `F5` — Tree view (ver procesos en árbol, útil para ver jerarquía padre/hijo).  
- `F6` — Sort by (seleccionar columna para ordenar, p. ej. %CPU, %MEM).  
- `F7` — Nice - (aumenta prioridad).  
- `F8` — Nice + (disminuye prioridad).  
- `F9` — Kill (matar proceso; luego elegir señal, p. ej. SIGTERM o SIGKILL).  
- `F10` — Quit (salir).  
- `Space` — marcar/desmarcar proceso (para operar en grupo).  
- `U` — mostrar solo procesos de usuario actual (toggle).  
- `P` — ordenar por %CPU (toggle).  
- `M` — ordenar por %MEM (toggle)

**c. Cómo usarlo:**  
Para ejecutarlo simplemente usa:  
`htop`

**d. Salida esperada:**  
![Ejecución de htop](imagenes/htop.png)

---

### 1.2 Complemento con glances, ifconfig, nmap y lynis  

Estas herramientas complementan la información del sistema obtenida con `htop`.  

**a. glances**  
Muestra métricas de rendimiento como CPU, RAM, red, disco, procesos, temperatura, etc.  
Instalación:  
`sudo apt install glances -y`  
Ejecución:  
`glances`  

**b. ifconfig**  
Permite ver y configurar interfaces de red.  
Instalación:  
`sudo apt install net-tools -y`  
Ver interfaces de red:  
`ifconfig`  

**c. nmap**  
Herramienta de análisis de red que detecta equipos, puertos abiertos y servicios.  
Instalación:  
`sudo apt install nmap -y`  
Escaneo de red básico:  
`nmap -sn 192.168.1.0/24`  

**d. lynis**  
Auditor de seguridad que evalúa vulnerabilidades en tu sistema.  
Instalación:  
`sudo apt install lynis -y`  
Ejecutar auditoría completa:  
`sudo lynis audit system`  

**Salida de ejemplo:**  
![Resultados de glances](imagenes/glances.png)  
![Resultados de nmap](imagenes/nmap.png)  
![Resultados de lynis](imagenes/lynis.png)

---

## 2. Direcciones IP  

### 2.1 Qué es IPv4 e IPv6  

**IPv4:**  
Es la cuarta versión del Protocolo de Internet. Utiliza direcciones de 32 bits (ejemplo: `192.168.0.1`) y permite aproximadamente 4 mil millones de direcciones.  
Su formato es **decimal** y se usa ampliamente en redes domésticas y empresariales.  

**IPv6:**  
Es la sexta versión, diseñada para reemplazar a IPv4 por falta de direcciones disponibles.  
Utiliza **128 bits**, lo que permite una cantidad casi infinita de direcciones (ejemplo: `2001:0db8:85a3:0000:0000:8a2e:0370:7334`).  
Ofrece ventajas como mayor seguridad, autoconfiguración y mejor enrutamiento.  

---

### 2.2 Comandos en Ubuntu para explorarlas  

**a. Ver información de red general:**  
`ip a`  

**b. Mostrar solo direcciones IPv4:**  
`ip -4 addr show`  

**c. Mostrar solo direcciones IPv6:**  
`ip -6 addr show`  

**d. Mostrar tabla de rutas:**  
`ip route show`  

**e. Ver estadísticas de red:**  
`netstat -i`  

**f. Mostrar conexiones activas:**  
`ss -tunap`  

**Salida esperada:**  
![IPv4 e IPv6](imagenes/ip.png)

---

## 3. Instalación en Arch Linux  

### 3.1 Qué es Arch Linux  

Arch Linux es una distribución GNU/Linux basada en el principio **KISS (Keep It Simple, Stupid)**.  
Se caracteriza por su instalación mínima, que permite al usuario construir su sistema desde cero, instalando solo lo necesario.  
Su modelo de actualizaciones es **rolling release**, es decir, el sistema se mantiene siempre actualizado sin necesidad de reinstalar.  

---

### 3.2 Proceso paso a paso de instalación  

**a. Actualizar claves y sincronizar el reloj:**  
`timedatectl set-ntp true`  

**b. Ver discos disponibles:**  
`fdisk -l`  

**c. Crear particiones en el disco:**  
`cfdisk /dev/sda`  

**d. Formatear particiones:**  
`mkfs.ext4 /dev/sda1`  

**e. Montar partición principal:**  
`mount /dev/sda1 /mnt`  

**f. Instalar el sistema base:**  
`pacstrap /mnt base linux linux-firmware`  

**g. Generar el archivo fstab:**  
`genfstab -U /mnt >> /mnt/etc/fstab`  

**h. Ingresar al nuevo sistema:**  
`arch-chroot /mnt`  

**i. Configurar zona horaria:**  
`ln -sf /usr/share/zoneinfo/America/Mexico_City /etc/localtime`  

**j. Configurar idioma del sistema:**  
`echo "LANG=es_MX.UTF-8" > /etc/locale.conf`  

**k. Instalar y habilitar GRUB:**  
`pacman -S grub`  
`grub-install /dev/sda`  
`grub-mkconfig -o /boot/grub/grub.cfg`  

**l. Reiniciar:**  
`exit`  
`umount -R /mnt`  
`reboot`  

**Salida esperada:**  
![Instalación Arch Linux](imagenes/archlinux.png)
