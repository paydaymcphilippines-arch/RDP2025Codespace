
---

### Instrucciones para configurar Docker en **Codespace**

1. **Verifica el almacenamiento disponible**  
   En la terminal, ejecuta el siguiente comando para ver las particiones y el almacenamiento disponible:

   ```bash
   df -h
   ```

   Elige la partición con mayor capacidad de almacenamiento.

2. **Crea la carpeta para Docker**  
   Ejecuta el siguiente comando para crear la carpeta donde Docker almacenará los datos:

   ```bash
   sudo mkdir -p /tmp/docker-data
   ```

3. **Configura Docker**  
   Ahora, edita el archivo de configuración de Docker:

   ```bash
   sudo nano /etc/docker/daemon.json
   ```

   Pega el siguiente contenido:

   ```json
   {
     "data-root": "/tmp/docker-data"
   }
   ```

4. **Reinicia tu Codespace**  
   Apaga y enciende nuevamente tu Codespace para aplicar los cambios.

5. **Verifica la configuración**  
   Para asegurarte de que Docker está configurado correctamente, ejecuta:

   ```bash
   docker info
   ```

---

### Crear archivo `windows10.yml`

Crea un archivo llamado `windows10.yml` con el siguiente contenido:

```yaml
services:
  windows:
    image: dockurr/windows
    container_name: windows
    environment:
      VERSION: "10"
      USERNAME: "Ghosthat"
      PASSWORD: "cristofer089"
    cap_add:
      - NET_ADMIN
    ports:
      - "8006:8006"
      - "3389:3389/tcp"
      - "3389:3389/udp"
    volumes:
      - /tmp/docker-data:/mnt/disco1
    devices:
      - "/dev/kvm:/dev/kvm"
      - "/dev/net/tun:/dev/net/tun"
    deploy:
      resources:
        limits:
          memory: 4G
          cpus: "4.0"
    stop_grace_period: 2m

```

---

### Levantar el contenedor

1. Ejecuta el siguiente comando para levantar el contenedor:

   ```bash
   docker-compose -f windows10.yml up
   ```

2. Inicia el contenedor con:

   ```bash
   docker start windows
   ```

---

¡Y listo! Con estos pasos, habrás configurado correctamente Docker y creado el contenedor de **Windows 10**.
