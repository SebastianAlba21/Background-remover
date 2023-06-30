# Svelte + Vite

Esta es una aplicación web desarrollada con Svelte que utiliza el servicio de "Cloudinary" para eliminar el fondo de una imagen de forma fácil y rápida.

## Configuración

1. Clona este repositorio en tu máquina local o descárgalo como archivo ZIP.

2. Abre una terminal y navega hasta el directorio del repositorio.

3. Instala las dependencias del proyecto utilizando npm.

4. Crea una cuenta gratuita en "Cloudinary" si aún no tienes una. Puedes registrarte en [https://cloudinary.com](https://cloudinary.com).

5. Obtén tus credenciales de "Cloudinary" (API Key, API Secret y Cloud Name) desde la consola de administración de tu cuenta.

6. Crea un archivo `.env` en el directorio raíz del proyecto y configura las siguientes variables de entorno con tus credenciales de "Cloudinary".

CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret

## Uso

1. Inicia la aplicación en modo de desarrollo.

npm run dev

2. Abre tu navegador web y accede a [http://localhost:5000](http://localhost:5000).

3. Arrastra una imagen con fondo que desees eliminar a la aplicación o haz clic en el área de carga para seleccionar una imagen desde tu dispositivo.

4. La aplicación utilizará el servicio de "Cloudinary" para procesar la imagen y eliminar el fondo automáticamente.

5. Una vez que el proceso haya finalizado, podrás descargar la imagen sin fondo resultante haciendo clic en el botón "Descargar".

## Contribución

Si quieres contribuir a este proyecto, puedes seguir estos pasos:

1. Haz un fork de este repositorio.

2. Crea una rama con una nueva funcionalidad o corrección.

3. Realiza los cambios necesarios y commitea tus modificaciones.

4. Envía tus cambios al repositorio remoto.

5. Abre una pull request en este repositorio y describe tus cambios.

## Licencia

Este proyecto se encuentra bajo la licencia [MIT](LICENSE).
