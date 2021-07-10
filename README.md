# ¡Hola! Bienvenido a mis configuraciones de Linux.
Actualmente mis objetivos son:
- Aprender a utilizar un gestor de ventanas de mosaico
- Realizar instalaciones avanzadas en donde la partición **home** y la partición **swap** se encuentren en un disco externo a donde se encuentra la partición **root**.

Para realizar la instalación avanzada, debo de administrar mis particiones, para eso utilizaré gparted y los siguientes comandos:
- lsblk -f // Este me permitirá saber los UUID de las particiones.
- sudo gparted
AQUÍ ES UTILIZANDO UNA LINUX LIVE
- dd // Permite enviar información de una partición a otra.
- sudo dd if='ruta de donde viene la información' of='ruta a donde quiero copiar la información' status=progress && sync
Después del último paso, debe actualizarse el UUID de la nueva **home** y redimensionar su tamaño.
- sudo e2fsck -f 'ruta a la partición que quiero redimensionar'
- sudo resize2fs 'ruta a la partición que quiero que obtenga su tamaño real'
- sudo e2fsck -f 'ruta a la partición a la que le acabo de cambiar el UUID' // Verificar la partición 
Se le pone yes a todo.
- sudo tune2fs -U random 'ruta a la partición que ya no quiero que sea mi home' // Se está cambiando el UUID
- lsblk -f 
Reiniciar y comprobar las particiones con:
df -h 
