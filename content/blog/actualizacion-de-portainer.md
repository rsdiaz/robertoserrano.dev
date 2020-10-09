---
title: Actualización de Portainer
description: 'Portainer es una herramienta web open-source, que permite gestionar contenedores Docker. Permite administrar contenedores de forma remota o local.'
picture: https://res.cloudinary.com/rserrano/image/upload/v1599347502/blog/portainer-logo.png
alt: Actualización de Portainer
category: Docker
createdAt: 9-06-2020
updatedAt:  9-06-2020
author:
  name: Roberto Serrano Diaz-Grande
  bio: Entusiasta de HTML, CSS, JavaScript, Node.js, Vue, etc... Comparto mi aprendizaje y conocimiento a traves de mi blog, en el cual publico artículos sobre desarrollo web y mi día a día tecnológico.
  img: https://res.cloudinary.com/rserrano/image/upload/v1598652059/roberto-serrano-desarrolloweb-tarragona.jpg
---

Para quien no sepa que es Portainer, Portainer es una aplicación web desarrollada con Angular que sirve para gestionar contenedores Docker de manera visual.

Yo la conocí a través del curso en [YouTube sobre Docker en Qnap](https://www.youtube.com/watch?v=BuG_ghLhFV0&t=1s) de [@jmramirez](https://twitter.com/jmramirez) el cual recomiendo si quieres saber más sobre Docker.

Portainer permite desde su interfaz actualizar contenedores Docker, esto suele funcionar en todos los contenedores, a excepción del propio Portainer. Es por eso que hay que realizar una actualización manual.

Hace seis días se lanzo una nueva release de Portainer, la CE 2.0.0 la cual introduce 101 cambios a Portainer, uno de los mayores cambios es el soporte con Kubernetes. Tenéis todos los cambios [aquí.](https://github.com/portainer/portainer/releases)

En mi caso utilizo Portainer en un NAS Synology donde tengo instalado Docker, pero la verdad que Portainer es mucho mas completo que la aplicación nativa de Synology Docker.

Los siguientes pasos para actualizar Portainer son válidos en cualquier plataforma que ejecute Docker.

Los pasos a seguir para actualizar Portainer son bastante sencillos:

- Parar el contenedor de Portainer
- Eliminar el contenedor de Portainer
- Actualizar y descargar la nueva imagen de Portainer
- Crear y ejecutar el nuevo contenedor.

Abrimos una terminal y escribimos los siguientes comandos.

```bash
$ docker stop portainer-server
$ docker rm portainer-server
$ docker pull portainer/portainer
$ docker run -d -p 8000:8000 -p 9000:9000 --network=rsnet \
--restart always \
--name="portainer-server" \
-v /var/run/docker.sock:/var/run/docker.sock \
-v /volume2/docker/portainer:/data \
portainer/portainer-ce:latest
```

Una vez finalizado, ya podemos acceder a la dirección [http://ipportainer:9000](http://ipdeportainer:9000/) para comprobar que Portainer está actualizado.

Con esto ya tenemos actualizado Portainer a la nueva versión.

Espero que sirva de ayuda, si tienes alguna duda o algo que aportar puedes usar los comentarios.

Saludos.

### Enlaces

[Curso en YouTube sobre Docker en Qnap.](https://www.youtube.com/user/masqueteclas)

[Portainer](https://www.portainer.io/portainer-ce/)

[Docker](https://www.docker.com/)