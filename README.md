# fotoxemailconrasperry
Raspberry pi captura una foto cuando  un sensor ultrasónico detecta presencia, luego lo envia por email.
Intrucciones:
  1. Descarga los archivos y colócalos en la carpeta /home/pi.
  2. Modifica el archivo enviaradjuntocorreo2.py, agrega la cuenta de correo desde el que se envia y la contraseña. También        agrega el correo a donde se envia. 
  3. Google no permitirá el inicio de sesión a través de smtplib porque ha marcado este tipo de inicio de sesión como "menos        seguro". Para solucionar este problema, vaya a https://www.google.com/settings/security/lesssecureapps mientras está          conectado a su cuenta de Google y a "Permitir aplicaciones menos seguras". 
  4. Conecta tu cámara web en algún puerto de usb.
  5. Conecta el sensor ultrasónico: 
              
      raspberry       ultrasonico 
  
      GPIO 25         TRIGGER
      GPIO 7          ECHO
      5V              VCC
      Ground          GND
      
  6. Activa el uso de la cámara y el remote GPIO en en menu de raspberry -> preferencias -> configuracion de raspberry pi ->        interfaces.
  7. Ahora instalaremos el paquete fswebcam, desde la "terminal de comandos" ejecuta el comando:
        sudo apt-get install fswebcam
  8. Ahora haremos que el programa principaldetectorpresencia.py se inicie automáticamente cada vez que se inicie la                raspberry. Ejecutamos el siguiente comando:
        crontab -e
  9. Luego nos desplazamos por el documento que se abrió  con la tecla "flecha abajo" hasta la última linea vacia
      y colocamos el siguiente texto:
        reboot python principaldetectorpresencia.py
  10. Presionamos tecla "control" y "x" juntas, luego la tecla "y" ó "s" para guardar los cambios.
      
  11. Listo, reinicia tu raspberry, se captura una foto cuando un objeto se acerque a 40 cm del sensor. El mensaje tarda en         llegar al correo entre 10 y 20 segundos.
