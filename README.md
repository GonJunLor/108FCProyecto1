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


Paso 4. Se pide modificar el fichero index.html desde el contenedor
```
sudo docker exec -it 108FCProyecto1 bash
```
