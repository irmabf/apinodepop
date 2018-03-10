# Nodepop 

Práctica Keepcoding Modulo2 NodeJS & MongoDB

# Sobre la aplicación

La aplicación está desarrollada con NodeJS y MongoDB con su librería Mongoose. Para poder utilizar el proyecto deberás tener instalado en tu ordenador tanto node como mongodb, buscar la documentación
de ambos para ver cómo hacerlo.


# Instalación

Clona la app, cambia el nombre del fichero .env.example a .env y pon un puerto en PORT, normalemente se usa el 3000. En MONGODB_HOST se recomienda 127.0.0.1 y en MONGODB_PORT 27017, da un nombre a tu base de datos
en MONGODB_DATABASE_NAME y configura un JWT_SECRET así como un JWT_EXPIRES_IN.

Una vez configurado el fichero .env ejecuta
```
npm run dev
```

Ahora carga los datos de la base de datos con  

```
npm run sample
```

Si quieres borrar los datos de la base de datos:

```
npm run deletedb
```

***

#	Uso:

*Utiliza POSTMAN para ejecutar la API y comprobar las rutas

*Para peticiones POST utilizar x-www-form-urlencoded*


###En primer lugar necesitas crear un usuario, en postman, selecciona POST introduce la siguiente ruta

*http://localhost:3000/apiv1/authenticate

En esta ruta, selecciona body,  -www-form-urlencoded e introduce tres keys: name, email y password asi como sus values, por ejemplo pepitogrillo como name, pepito@example.com  como email y 12345 para la password. 

***

###Login de usuario (


```
POST http://localhost:3000/apiv1/authenticate 
```

* PARÁMETROS (*OBLIGATORIOS)

```
	email: email del usuario que utilizaste en la ruta anterior para crear una cuenta
	password: contraseña del usuario que utilizaste anteriormente

```

Al pulsar send se te devolverá un token que es el que usarás para los siguientes métodos


###Añadir usuarios:
* URL


*Para peticiones POST utilizar x-www-form-urlencoded*
*Para utilizar lenguaje deseado --> Accept-Language [en - es]

```
POST /apiv1/users/signup
```

* PARÁMETROS (* OBLIGATORIOS)

```
	*name: nombre
	*email: email del usuario
	*pass: contraseña

```

eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX2lkIjoiNWFhM2VhM2M2NjEwNjUwZTE4OTA3Yjk4IiwiaWF0IjoxNTIwNjkxOTQ2LCJleHAiOjE1MjA4NjQ3NDZ9.BIM5vlmkjZo8z0y6k0pa4EO2752zRkhLFoLX6mQDHms

//list all the adds  get
http://localhost:3000/apiv1/ads?token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX2lkIjoiNWFhM2VhM2M2NjEwNjUwZTE4OTA3Yjk4IiwiaWF0IjoxNTIwNjkxOTQ2LCJleHAiOjE1MjA4NjQ3NDZ9.BIM5vlmkjZo8z0y6k0pa4EO2752zRkhLFoLX6mQDHms


// list all the adds containing macbook as name
http://localhost:3000/apiv1/ads?name=macbook&token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX2lkIjoiNWFhM2VhM2M2NjEwNjUwZTE4OTA3Yjk4IiwiaWF0IjoxNTIwNjkxOTQ2LCJleHAiOjE1MjA4NjQ3NDZ9.BIM5vlmkjZo8z0y6k0pa4EO2752zRkhLFoLX6mQDHms

#Ejemplo de request para listar todos los anuncios:

Metodo GET

http://localhost:3000/apiv1/ads?token=tutoken


http://localhost:3000/apiv1/ads?token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX2lkIjoiNWFhM2YwMWE2NjEwNjUwZTE4OTA3Yjk5IiwiaWF0IjoxNTIwNjkzMzIwLCJleHAiOjE1MjA4NjYxMjB9.zR6huGIt5oFPEG8rSi_0ef3vs2s5m7aX6Sq_66ALjuM

***

#Ejemplo de request para listar todos los anuncios que contengan la palabra mackbook como nombre del anuncio:

Metodo GET

http://localhost:3000/apiv1/ads?name=macbook&token=TUTOKEN

http://localhost:3000/apiv1/ads?name=macbook&token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX2lkIjoiNWFhM2YwMWE2NjEwNjUwZTE4OTA3Yjk5IiwiaWF0IjoxNTIwNjkzMzIwLCJleHAiOjE1MjA4NjYxMjB9.zR6huGIt5oFPEG8rSi_0ef3vs2s5m7aX6Sq_66ALjuM