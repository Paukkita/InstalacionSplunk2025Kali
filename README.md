# Instalación de Splunk en Kali Linux (2025)

Hoy, 26 de noviembre de 2025, comenzaré mi aprendizaje en **Splunk**. Como primer paso, realizaré la instalación de esta herramienta en mi máquina virtual con Kali Linux.

### Para que sirve Splunk? 


Splunk es una plataforma para buscar, analizar y visualizar datos generados por dispositivos, como logs de sistemas o aplicaciones. Permite monitorizar el rendimiento y la seguridad
de los sistemas en tiempo local, además es posible de instalar en local o en la nube y su lenguaje SPL facililita consultas rápidas y precisas.

---

## Detalles de la instalación

- **Sistema operativo:** Kali Linux  
- **Kernel:** 6.16.8+kali-amd64  
  > Para comprobar el kernel desde la terminal de Kali, ejecuta:  
  > ```bash
  > uname -r
  > ```
- **Kernel:** 6.16.8+kali-amd64 
---

## Paso 1: Descargar Splunk

1. Dirígete a la página oficial de Splunk: [https://www.splunk.com/](https://www.splunk.com/)
2. En la pantalla principal, aparecerá la versión disponible: **Splunk Enterprise 10.0.2**.  
   Esta versión se ofrece con un **free trial de 60 días**, ideal para prácticas.  
   > En entornos empresariales o para uso prolongado, se debería adquirir otra licencia o mantener la licencia gratuita tras el periodo de prueba.

<img width="1918" height="986" alt="Pantalla principal Splunk" src="https://github.com/user-attachments/assets/4d96a99f-2678-4f1e-ad5d-ef91c1b786c8" />

3. Regístrate con un correo electrónico y los datos que prefieras.  
   > En este ejemplo usaré un email personal para prácticas.

<img width="437" height="407" alt="Registro completado" src="https://github.com/user-attachments/assets/3398727b-b3f2-4735-a2e1-4d19f7ea4d87" />

4. Recibirás un correo de confirmación como este:

<img width="1600" height="671" alt="Correo de confirmación" src="https://github.com/user-attachments/assets/b67df503-bb3f-4ec9-816e-46799dff0c4a" />

5. Una vez iniciada la sesión, se abrirá la pestaña de descarga. Selecciona:
   - **Sistema operativo:** Linux
   - **Formato de archivo:** `.deb` (ya que Kali se basa en Debian)

<img width="1918" height="957" alt="Descarga Splunk .deb" src="https://github.com/user-attachments/assets/5c04ad9a-a589-4ce4-99ad-733a18bd01b2" />
   -> Ahora solo queda a que se nos descargue este fichero .deb, hay que recalcar que en vez de descargar el fichero de forma gráfica podemos darle al wget y nos dara
   un comando para que lo introduzcamos en la terminal, sin embargo en este caso lo haremos de forma más gráfica ya que en mi caso es mas cómodo, ya que es para practicar,
   si buscasemos eficiencia es más rápido y permite automatizarlo hacerlo con el wget.

<img width="1916" height="990" alt="image" src="https://github.com/user-attachments/assets/600a071f-b8e5-4c50-920f-b5ac66727d40" />

## Paso 2: Configuración de Splunk en nuestro sistema
Ahora para instalar podemos hacerlo de dos metodos, yo usare GDebi
sudo apt update
sudo apt install gdebi
-> Una vez instalado GDebi buscamos el .deb
->abrir con 
<img width="1917" height="947" alt="image" src="https://github.com/user-attachments/assets/c10f19e5-4bda-4bda-952a-cafc69737fa8" />
<img width="1917" height="992" alt="image" src="https://github.com/user-attachments/assets/cbe2cf41-d401-477f-bcc3-2c4cabdaa8ca" />

-> Introducimos el nombre del usuario para autentificar el proceso y esperamos a que se descargue

-> Una vez descargado nos vamos al directorio /opt y ejecutamos splunk
<img width="657" height="482" alt="image" src="https://github.com/user-attachments/assets/4fd64f9c-c016-49bd-8c75-768b8b5de176" />

-> Se nos abriran los terminos y condiciones los cuales al acabar de leerlos nos saldra esto:
- Do you agree with this license? [y/n]: -
-> le daremos a "yes"
  <img width="665" height="247" alt="image" src="https://github.com/user-attachments/assets/aa7e5a13-a5f4-4e8d-84b8-476a55b89ab2" />
  
  -> Y pondremos nombre y usuario

Una vez cargue nos vamos a este dominio en localhost http://<Tu-usuario>:8000 y veremos que ya nos carga splunk

### RECOMENDACIÓN:
Para facilitar el inicio de Splunk lo añadiremos al PATH 
> ```bash
  > echo 'export PATH=$PATH:/opt/splunk/bin' >> ~/.bashrc
> source ~/.bashrc
  > ```
Y cada vez que lo queramos iniciar solo tendremos que hacer:
 > ```bash
  > sudo splunk start 
  > ```
* Ten en cuenta que esto solo funciona para el usuario que lo estás haciendo"

De igual forma este es el comando para asegurarnos el inicio sin accesos directos:
 > ```bash
  > sudo /opt/splunk/bin/splunk start
  > ```

## Paso 3: Comandos y uso básico de Splunk
### Comandos básicos
```bash
# Iniciar Splunk
sudo /opt/splunk/bin/splunk start

# Detener Splunk
sudo /opt/splunk/bin/splunk stop

# Reiniciar Splunk
sudo /opt/splunk/bin/splunk restart

# Comprobar el estado de Splunk
sudo /opt/splunk/bin/splunk status
```
### Comandos básicos SPL
```bash
# 1. Buscar todos los eventos en un índice
index=demo

# 2. Contar la cantidad de eventos
index=demo | stats count

# 3. Filtrar eventos que contengan una palabra clave
index=demo error

# 4. Mostrar tabla con campos específicos
index=demo | table _time host source message
```

