# Proyecto: Formulario de Contacto - Hersilia Fundación

Este proyecto es un formulario de contacto desarrollado en PHP, diseñado para enviar correos electrónicos a la dirección oficial de Hersilia Fundación.

## Características
- Recoge datos del usuario: Nombre, Correo, Teléfono, Asunto y Mensaje.
- Sanitiza los datos ingresados para mayor seguridad.
- Envía los datos por correo electrónico al destinatario configurado.
- Muestra un mensaje de éxito o error según el resultado del envío.

## Requisitos
- Servidor con PHP 7 o superior.
- Servidor con la función `mail()` habilitada para enviar correos.
- Conexión a internet para el envío de correos.

## Instalación
1. Descarga los archivos del proyecto y colócalos en el directorio de tu servidor web.
2. Asegúrate de que el servidor tenga activada la función de envío de correos.
3. Modifica la variable `$destinatario` en el archivo PHP para que contenga el correo de destino.

## Uso
1. Accede al formulario a través de tu navegador.
2. Completa los campos requeridos (Nombre, Correo, Teléfono, Asunto y Mensaje).
3. Envía el formulario.
4. Si el mensaje es enviado correctamente, aparecerá una notificación de éxito.
5. En caso de error, se mostrará un mensaje indicando el fallo.

## Seguridad
- Se utiliza `htmlspecialchars()` para evitar ataques XSS.
- Se valida que los datos ingresados no estén vacíos antes de enviarlos.
- Se recomienda implementar una verificación CAPTCHA para evitar spam.

## Personalización
Para cambiar la apariencia del formulario o ajustar el contenido del correo, edita las secciones de CSS en el archivo HTML y los valores de `$titulo` y `$contenido` en el script PHP.

## Licencia
Este proyecto es de código abierto y puede ser utilizado y modificado libremente.

