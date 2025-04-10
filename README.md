# Fundamentos de contenerización
## Actividad 1 - Servidor Web Simple con Nginx

Paso 1. construir la imagen con el mismo nombre que le repositorio con la version 1.0
```
sudo docker image build --tag 108fcproyecto1:1.0 .
```	
	
- Comprobar que se ha creado la imagen:
```
sudo docker image ls 
```

- Borrar imagen (prueba):
```
sudo docker image rmi --force 108fcproyecto1
```

Paso 2. Ejecutar el contenedor en el puerto 80
```
sudo docker container run -d -p 80:80 --name 108FCProyecto1 108fcproyecto1:1.0
```

- Comprobar que se ha ejecutado el contenedor
```
sudo docker container ls
```
- Borrar contendor (prueba):
```
sudo docker container rm --force 108fcproyecto1
```

Paso 3. Comprobación: http://localhost
```
http://localhost
```

Paso 4. Se pide modificar el fichero index.html desde el contenedor
```
sudo docker exec -it 108FCProyecto1 bash
```
- En la consola dentro del contenedor actualizamos e instalamos un editor, en este caso nano.
```
apt update
apt install nano
```
- Abrimos el archivo index con nano para editarlo
```
nano /usr/share/nginx/html/index.html
```
- Salimos de la consola del contenedor
```
exit
```
## Crear y subir imagen a dockerHub
* Creamos la imagen de el contenedor editado y comprobamos que se ha creado
```
docker commit 108fcproyecto1 108fcproyecto1:1.0
docker images
```
* Guardamos la imagen en un archivo .tar
```
docker save -o 108fcproyecto1version1.tar 108fcproyecto1:1.0 
```
* Iniciamos sesión en dockerHub con el navegador.
```
docker login
```
* Creamos una etiqueta a la imagenb que vamos a subir
```
sudo docker tag 108fcproyecto1:1.0 gonjunlor/108fcproyecto1:1.0
```
* Subimos la imagen a dockerHub
```
docker push gonjunlor/108fcproyecto1:1.0
```