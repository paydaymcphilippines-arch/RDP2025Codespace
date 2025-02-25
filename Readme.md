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

