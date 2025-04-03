# Administración de Redes en Windows

Este documento proporciona una guía sobre cómo realizar diversas configuraciones de red en Windows, incluyendo compartir WiFi desde la PC, eliminar historial de DNS y otras tareas relacionadas con la administración de redes.

## 1. Ver la Configuración de Red
Para obtener información sobre la configuración de red de tu PC, usa el siguiente comando:
```sh
ipconfig /all
```
Este comando muestra detalles como direcciones IP, configuraciones de adaptadores y estado de conexión.

## 2. Liberar y Renovar la Dirección IP
Si tienes problemas de conectividad, puedes liberar y renovar la dirección IP de la siguiente manera:
```sh
ipconfig /release
ipconfig /renew
```

## 3. Vaciar la Caché DNS
Si experimentas problemas de resolución de nombres de dominio, vacía la caché de DNS con el siguiente comando:
```sh
ipconfig /flushdns
```
Después de ejecutar el comando, verás el mensaje:
```
Se vació correctamente la caché de resolución de DNS.
```
Para visualizar la caché de DNS actual, usa:
```sh
ipconfig /displaydns
```

## 4. Compartir WiFi desde la PC
Si deseas convertir tu PC en un punto de acceso WiFi para compartir Internet, sigue estos pasos:
### Habilitar el modo de punto de acceso
1. Abre el símbolo del sistema como administrador.
2. Ejecuta el siguiente comando para configurar la red:
```sh
netsh wlan set hostednetwork mode=allow ssid=NombreWiFi key=ContraseñaWiFi
```
3. Inicia el punto de acceso con:
```sh
netsh wlan start hostednetwork
```
Para detenerlo, usa:
```sh
netsh wlan stop hostednetwork
```

### Compartir la conexión a Internet
1. Ve a **Panel de control > Centro de redes y recursos compartidos**.
2. Haz clic en **Cambiar configuración del adaptador**.
3. Encuentra la conexión de red activa, haz clic derecho y selecciona **Propiedades**.
4. En la pestaña **Compartir**, habilita la opción **Permitir que otros usuarios de la red se conecten a través de la conexión a Internet de este equipo**.
5. Selecciona la red recién creada.

## 5. Restablecer Configuración de Red
Si tienes problemas persistentes con la red, puedes restablecer completamente la configuración con:
```sh
netsh int ip reset
netsh winsock reset
```
Luego, reinicia la PC para aplicar los cambios.

## 6. Eliminar el Historial de Redes WiFi Guardadas
Si deseas eliminar redes WiFi guardadas en tu PC, usa:
```sh
netsh wlan show profiles
```
Este comando mostrará todas las redes guardadas. Para eliminar una en específico:
```sh
netsh wlan delete profile name="NombreDeLaRed"
```

## 7. Ver Conexiones Actuales y Puertos Abiertos
Para verificar las conexiones activas en tu PC y los puertos abiertos, usa:
```sh
netstat -ano
```
Este comando muestra una lista de conexiones activas junto con los PID de los procesos que las usan.

## 8. Verificar Estado del Firewall
Para revisar si el firewall de Windows está activo:
```sh
netsh advfirewall show allprofiles
```
Para desactivarlo temporalmente:
```sh
netsh advfirewall set allprofiles state off
```
Para activarlo nuevamente:
```sh
netsh advfirewall set allprofiles state on
```

---

Siguiendo estas configuraciones, podrás gestionar mejor tu red, solucionar problemas de conectividad y compartir Internet desde tu PC.

