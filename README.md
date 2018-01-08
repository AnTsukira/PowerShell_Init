# PowerShell_Init
Command Basic administration
Este comando permitira  saber cuanto de espacio en GB tiene nuestros disk. 
examples:
Get-WmiObject win32_logicaldisk | format-Table DeviceId, @{name="Size (GB)";e={[math]::Round($_.Size/1GB,2)}}, @{n="FreeSpace (GB)";e={[math]::Round($_.FreeSpace/1GB,2)}}
se que muchos no estamos familiarizados con estos comandos, pero les  explicare, y espero que sea un aporte
Get-WmiObject -> Es un cmdlet que permite obtener instancias de las clases de Windows
win32_logicaldisk ->  Instancia  los discos que tienen la maquina
Format-Table  ->  Es un cmdlet que ordena en formato tabla la consulta que se realiza.
DeviceId, Size, FreeSpace son  las cabezeras de la informacion  del win32_logicaldis , tambien hay otras tres mas (DriveType, ProviderName, VolumeName)
En esta consulta  solicitamos solo 3 cabezeras, las cuales dos  tienen un agregado que a continuacion explicare para  sacar dudas
que son el caso de "Size" y "FreeSpace"
En este caso, como estamos trabajando con numeros en otro tipo de formato, muchas veces estamos acostumbrados a verlos en GB o KB. Pues
por Default el sistema lo arroja en bytes, para ello vamos a utilizar algunas propiedades que van dentro de @{}
name o "n" nos permite renombrar la cabezera a nuestro gusto, en este caso va en comillas, "Size (GB)"
e={} nos permite saber que expresion vamos a reemplazar y que formula podemos utilizar para nuestro beneficio en este caso, como utilizaremos 
la formula de Redondeo(ROUND) tenemos que previamente colocar [math] que indica que vamos a utilizar una propiedad matematica
posteriormente dentro del ($_.Size/1GB,2) dividimos entren GB que es lo que deseamos y rendeamos a dos digitos. 
