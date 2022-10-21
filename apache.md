## Servidor Apache
En este documento se va a tratar la instalación del servidor Apache en Ubuntu a través de la línea de comandos. Antes de nada asegúrate de tener un usuario con permisos de administrador y un firewall básico, configurado para tapar los puertos que no vayamos a usar.
- ### primer paso: Instalar Apache

  Apache está incluído en los repertorios de software de Ubuntu, por lo que podrá ser instalado con las herramientas típicas del administrador de paquetes. Actualizamos el equipo e instalamos apache con la línea de comando "sudo apt install apache2"
  
 - ### segundo paso: Ajustar el firewall
  
  Ahora hay que configurar el firewall para que permita el acceso a los puertos web predeterminados.Durante la instalación, Apache se registra con UFW para proporcionar algunos perfiles de aplicación que pueden utilizarse para habilitar o deshabilitar el acceso a Apache a través del firewall.
  
  Enumere los perfiles de aplicación ufw escribiendo lo siguiente:
```
  sudo ufw app list
```
  Obtendrá una lista de los perfiles de aplicación:
```
Output
Available applications:
  Apache
  Apache Full
  Apache Secure
  OpenSSH  
```
Como lo indica el resultado, hay tres perfiles disponibles para Apache:

    Apache: este perfil abre solo el puerto 80 (tráfico web normal no cifrado)
    Apache Full: este perfil abre el puerto 80 (tráfico web normal no cifrado) y el puerto 443 (tráfico TLS/SSL cifrado)
    Apache Secure: este perfil abre solo el puerto 443 (tráfico TLS/SSL cifrado)

Se recomienda habilitar el perfil más restrictivo, que de todos modos permitirá el tráfico que configuró. Debido a que en esta guía aún no configuramos SSL para nuestro servidor, solo deberemos permitir el tráfico en el puerto 80:
Puede verificar el cambio escribiendo lo siguiente:
```
    sudo ufw status
```
El resultado proporcionará una lista del tráfico de HTTP que se permite:

- ### tercer paso: Comprobar el servidor web


