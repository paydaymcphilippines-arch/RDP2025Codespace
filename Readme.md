una vez abras codespace en la terminal escribe:

1- df -h

y elije la particion que mas almacenamiento tenga

luego ejecuta

2- sudo mkdir -p /tmp/docker-data 

para crear una carpeta de docker en esa ruta

3- sudo nano /etc/docker/daemon.json



pega:

{

  "data-root": "/tmp/docker-data"

}



la ruta



despues reinicia tu codespace , apagalo y prendelo.



despues para verificar

4- docker info










crea un archivo llamado





windows10.yml





con esto dentro:





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


    deploy:


      resources:


        limits:


          memory: 4G


          cpus: "4.0"


    stop_grace_period: 2m














luego ejecuta: docker-compose -f windows10.yml up





docker start windows
