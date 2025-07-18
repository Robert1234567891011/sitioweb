# sitioweb
Comandos necesarios para pasar windows 11 Home a PRO cmd------>

"sc config LicenseManager start= auto & net start LicenseManager"

"sc config wuauserv start= auto & net start wuauserv"

"changepk.exe /productkey VK7JG-NPHTM-C97JM-9MPGT-3V66T"

"exit"

"exit"

Comandos para activar 

------>para activar WINDOW 11:        "irm https://get.activated.win | iex" --> 1,1,0

------>para activar OFFICE 2024:      "irm https://massgrave.dev/get | iex" --> 2,1.0

------>¿Cómo saber si estoy en UEFI o Legacy?

Busca "Modo BIOS":

Presiona Win + R, escribe "msinfo32" y pulsa Enter.

Si dice "UEFI", estás en modo UEFI.

Si dice "Legacy", estás en BIOS tradicional.

En Linux-------->  Ejecuta en la terminal: "ls /sys/firmware/efi"

En Windows----verificar informacion completa de equipo---->

Con CMD : ------------> "systeminfo"

Verificar con CMD si el disco es GPT o MBR  :  ----> "diskpart"  luego  "list disk"


ATAJOS PARA Window 10, 11

------>crear punto de restauracion     W+R : "systempropertiesprotection"

------>deshabilitar cuenta de usuario en Window 7, 10, 11, pero no sirve para window 11 home--->  W+R : "lusrmgr.msc"

instalar el siguiente archivo ---->  "https://github.com/akruhler/AccountManagement?tab=readme-ov-file"

------->para ingresar a particiones   W+R : "diskmgmt.msc"

------>para window 11 home - Para ver información similar en Windows Home, puedes usar---> "netplwiz" o "compmgmt.msc"

------>Este comando abre la ventana de Propiedades del Sistema, donde puedes---->

- Ver y cambiar el nombre del equipo y grupo de trabajo/dominio.

- Configurar el rendimiento del sistema.

- CAMBIAR EL NOMBRE DEL EQUIPO solo con powerShell como administrador  -------> :

1.- "Rename-Computer -NewName "NUEVO_NOMBRE" -Force"

2.- "Restart-Computer"

3.- "hostname"

- Administrar las opciones de inicio y recuperación.

- Habilitar o deshabilitar escritorio remoto.

- Configurar variables de entorno.----->"sysdm.cpl"
  

W+R y cambiar nombre de usuario con --------> "netplwiz"    propiedades


COMANDOS PARA GESTIONAR USUARIOS en CMD  : ingresar a CMD

Ver todos los usuarios del sistema------------>     "net user"

Crear un nuevo usuario-----------> "net user NuevoUsuario Contraseña /add"

Si quieres crear un usuario llamado "Carlos" con la contraseña "12345"-----------> "net user Carlos 12345 /add"

Cambiar la contraseña de un usuario---------------> "net user Carlos abc123"

Eliminar el usuario "Carlos":-->"net user Carlos /delete"

Deshabilitar y habilitar usuario------------>  "net user Carlos /active: no" o "net user Carlos /active: yes"

COMANDOS PARA GESTIONAR GRUPOS LOCALES

Ver todos los grupos locales:-------> "net localgroup"

Ver los usuarios dentro de un grupo específico: --------> "net localgroup NombreDelGrupo" -----> Ejemplo: Para ver los miembros del grupo de Administradores: -->"net localgroup Administradores"


Agregar un usuario a un grupo (darle permisos de Administrador):------->"net localgroup Administradores Usuario /add"--->Ejemplo: Dar permisos de administrador a "Carlos":---->"net localgroup Administradores Carlos /add"

Eliminar un usuario de un grupo:-----> "net localgroup Administradores Usuario /delete"

Ejemplo: Quitar a "Carlos" de los Administradores:------>"net localgroup Administradores Carlos /delete"

EVITAR QUE UNA CUENTA SE DESHABILITE AUTOMATICAMENTE

Si quieres asegurarte de que un usuario nunca se deshabilite (por ejemplo, la cuenta de Administrador), usa este comando en CMD (como Administrador):

Esto garantiza que la cuenta siempre esté habilitada.---->"wmic useraccount where name="Usuario" set AccountDisabled=FALSE"

--->Ejemplo: Si la cuenta se llama "Carlos", ejecuta:---->"wmic useraccount where name="Carlos" set AccountDisabled=FALSE"

DESHABILITAR UNA CUENTA MANUALMENTE

Si quieres deshabilitar una cuenta para que no pueda iniciar sesión, usa este comando:-----> "wmic useraccount where name="Usuario" set AccountDisabled=TRUE"-------->Ejemplo: Para deshabilitar la cuenta "Carlos":----->"wmic useraccount where name="Carlos" set AccountDisabled=TRUE"

Alternativa con net user: "net user Carlos /active:no"

VOLVER A HABILITAR UNA CUENTA DEHABILITAR

Si una cuenta está deshabilitada y quieres activarla nuevamente, usa:-----> "net user Usuario /active:yes"------> Ejemplo: Para activar "Carlos":----->"net user Carlos /active:yes"

VERIFICAR SI UNA CUENTA ESTA HABILITADA O DESHABILITAR

Para ver si una cuenta está activa o deshabilitada, ejecuta en CMD:--->"wmic useraccount where name="Usuario" get Name, AccountDisabled"---->Si el resultado muestra FALSE, la cuenta está habilitada.
Si muestra TRUE, la cuenta está deshabilitada.

VERIFICAR CON QUE IP ESTA TU CPU ------->"ipconfig"

PARA PROBAR LA CONECTIVIDAD DEL SERVIDOR INTERNET----->Verificar si tienes Internet (ping a Google)"ping google.com",Ver si un sitio web responde (por ejemplo, Trabajopolis)--> "ping trabajopolis.bo",Hacer ping a Google Translate---> "ping translate.google.com"---->Obtener detalles de red en CMD:--->"ipconfig /all"

VERIFICAR Y REPARAR ARCHIVOS DEL SISTEMA---¿Cuándo usar sfc /scannow?

- Si Windows se congela o tiene errores frecuentes.

- Si las aplicaciones fallan o no responden.

- Después de un apagón o una actualización fallida.

- Si ves mensajes de "Archivos del sistema dañados" o "Windows no puede encontrar un archivo".

--->"sfc /scannow"----Se encontraron archivos corruptos, pero no se pudieron reparar → Ejecuta este comando antes de volver a intentarlo:------>"DISM /Online /Cleanup-Image /RestoreHealth"---->Después de usar DISM, ejecuta de nuevo sfc /scannow.

VERIFICAR ESTADOS DE DISCOS DUROS-->

- Detecta y corrige errores en el disco (como archivos dañados o sectores defectuosos).

- Mejora el rendimiento del sistema al organizar correctamente los datos en el disco.

- Previene pérdida de datos al reparar problemas antes de que empeoren.------->"chkdsk"

Ejecutar el comando básico (solo escaneo, sin reparar):------>"chkdsk C:"

Escanear y corregir errores automáticamente:---->"chkdsk C: /f"---->/f → Corrige errores en la unidad.

Escaneo profundo con reparación de sectores dañados:------>"chkdsk C: /f /r"---->/f → Repara errores del sistema de archivos.
/r → Detecta y repara sectores defectuosos en el disco.

COMPROBAR PERMISOS DE USUARIO---->

- Muestra el nombre del usuario con el que has iniciado sesión.

- Útil para verificar si tienes permisos de administrador o de usuario estándar.

- Puede ser usado en scripts o automatización para identificar al usuario activo.------>"whoami"

INFORMACION DEL SISTEMA----->

- Muestra la versión exacta de Windows instalada.

- Muestra la arquitectura del sistema (32 o 64 bits).

- Indica la fecha de instalación de Windows.

- Muestra la cantidad de RAM instalada.

- Identifica el nombre del equipo y el dominio al que pertenece.

- Indica si el sistema tiene virtualización habilitada.

- Muestra la fecha del último inicio del sistema

-------->"systeminfo"

ESTADO DE FIREWALL------>

Este comando se usa en CMD para ver el estado actual del Firewall de Windows en todos los perfiles de red.

- Muestra si el Firewall está activado o desactivado en los distintos perfiles de red.

- Indica si están permitidas las conexiones entrantes y salientes.

- Te ayuda a diagnosticar problemas de red relacionados con el Firewall.----->"netsh advfirewall show allprofiles"


cambiar el tipo de cuenta de un usuario Administrador a Estándar en Windows 11 usando CMD--->

-Presiona Win + R, escribe cmd, luego presiona Ctrl + Shift + Enter para abrirlo con permisos de administrador.-->

- Ver la lista de usuarios del sistema:"net user"---->Esto te mostrará los nombres de usuario disponibles en el sistema.------->

- Remover al usuario del grupo de Administradores:---->"net localgroup Administradores Usuario /delete"------>Ejemplo: Si el usuario se llama "Carlos", usa:--->"net localgroup Administradores Carlos /delete"-------->

- Verificar que el usuario ya no es administrador:---->"net localgroup Administradores"----->El usuario no debe aparecer en la lista.

 ¿Cómo volver a hacer Administrador a un usuario?

 Si más adelante quieres devolverle permisos de Administrador al usuario, usa este comando:--->"net localgroup Administradores Usuario /add"---Ejemplo:--->"net localgroup Administradores Carlos /add"


ATAJOS PARA----->Abrir el Administrador de tareas:

Ctrl + Shift + Esc
Abrir el Explorador de archivos:

Windows + E
Abrir la Configuración:

Windows + I
Acceder a Configuración del sistema (msconfig):

Windows + R → "msconfig"
Abrir el Administrador de dispositivos:

Windows + X → "M"
Acceder al Panel de control:

Windows + R → "control"
Acceder al Editor del Registro:

Windows + R → "regedit"
Abrir la consola de comandos (CMD):

Windows + R → "cmd"
Abrir el Símbolo del sistema como administrador:

Windows + X → "A"
Acceder a Propiedades del sistema avanzado:

Windows + R → "sysdm.cpl"
Acceder a la configuración de red (Conexiones de red):

Windows + R → "ncpa.cpl"
Apagar o reiniciar el equipo:

Windows + X → U → "U" (Apagar) o "R" (Reiniciar)
Acceder a las opciones de energía:

Windows + X → "O"

Cómo corregir los puertos USB que no funcionan en Windows 10
"https://purosistemas.com/como-corregir-los-puertos-usb-que-no-funcionan-en-windows-10/"

comando en Pawer Shell para verificar las condiciones de USB---->"msdt.exe -id devicediagnostics"
Link de descarga de USBDeview: Cómo utilizar para solucionar problemas 

USB---------->"https://mega.nz/file/XopmnDQB#URKUuEdpNLiwApQNt32hTi1DqlAfB5aF1EmKLtkatkE"
link de tutorial ----->"https://www.youtube.com/watch?v=Wc2ep3pUrzY"


COMANDOS PARA MIGRASION DE BD de sql server y visual studio 2022 .NET 6---------------->

remover migracion------>"Remove-Migration"


para migrar --------> "Add-Migration InitialCreate" y "Update-Database"

---------> CREAR EL PROYECTO Blazor

Abre una terminal o el símbolo del sistema.

Ejecuta el siguiente comando para crear un nuevo proyecto Blazor Server:

"dotnet new blazorserver -o BCP_Frontend"

Esto creará una carpeta llamada "BCP_Frontend" con la estructura básica de un proyecto Blazor.

Navega a la carpeta del proyecto:

"cd BCP_Frontend"

Ejecuta el proyecto para asegurarte de que todo esté bien:

"dotnet run"
---------

 Limpia y recompila el proyecto
Si los errores persisten, borra la caché de compilación y recompila el proyecto.

Ejecuta estos comandos en la terminal:

"dotnet clean"
"dotnet build"
"dotnet run"

Abre tu navegador en https://localhost:5001 o http://localhost:5000 para ver la aplicación Blazor predeterminada.
---------------------------
2. Instalar Dependencias
Dentro de la carpeta del proyecto (BCP_Frontend), instala Newtonsoft.Json para manejar JSON en las peticiones HTTP:

"dotnet add package Microsoft.AspNetCore.Components.Web"

"dotnet add package Microsoft.AspNetCore.Components.WebAssembly"

"dotnet add package System.Net.Http.Json"

"dotnet add package Newtonsoft.Json"

--------------
repositorio git----------------->"https://github.com/M0r13n/mikrotik_monitoring"


descarga de dockers ----->"https://docs.docker.com/desktop/install/windows-install/"

crear cuenta
https://www.profesionalreview.com/2021/12/04/como-crear-un-usuario-en-windows-11/

para utilizar con IA y catálogos

-  "https://www.template.net/edit-online/675034a011c142c447fba1f7"                (plantillas)

-  "https://creativemarket.com/search/creative-marketing?categoryIDs=1"           (plantillas)

-  "https://www.template.net/"

- IA------>
-  "https://app.simplified.com/home"

-  "https://designs.ai/"

-  "https://www.photopea.com/"

-  "https://create.vista.com/es/home/"

- "https://www.pexels.com/es-es/buscar/videos/muebles/" (videos y imagenes)
- "https://pixabay.com/es/videos/search/" (videos y imagenes)


https://new.express.adobe.com/design/template/urn:aaid:sc:VA6C2:212080ff-6c22-415a-adcd-f01cf80df804?category=text&taskID=flyer


-https://slidesgo.com/
-https://www.freepik.com/


-------------------------------------------------------------



# Descargar HP Support Assistant (oficial)
Start-BitsTransfer -Source "https://ftp.hp.com/pub/caps-softpaq/cmit/HPIA.exe" -Destination "$env:TEMP\HPIA.exe"

# Instalar drivers automáticamente
Start-Process -FilePath "$env:TEMP\HPIA.exe" -ArgumentList "/Silent /Install /AcceptEULA" -Wait



pnputil /add-driver "C:\Drivers\*.inf" /install /subdirs


# Chipset (Intel)
pnputil /add-driver "C:\Drivers\Chipset\*.inf" /install

# Gráficos (Intel HD 4400)
pnputil /add-driver "C:\Drivers\Graphics\*.inf" /install

# Wi-Fi (Intel/Realtek)
pnputil /add-driver "C:\Drivers\WiFi\*.inf" /install




# Forzar búsqueda de drivers en Windows Update
Start-Process -FilePath "ms-settings:windowsupdate" -Wait





Get-PnpDevice | Where-Object {$_.Status -eq "Error"} | Select-Object FriendlyName, InstanceId




# Listar dispositivos sin drivers
Get-PnpDevice | Where-Object {$_.Status -eq "Error"} | Format-Table FriendlyName, Status




# checklist_bd.ps1
# Autor: Richard Poma - Monitoreo de BD
# Fecha: 2025

function Test-Ping {
    param([string]$ip)
    if (Test-Connection -ComputerName $ip -Count 2 -Quiet) {
        Write-Host "PING $ip ---> OK" -ForegroundColor Green
        return $true
    } else {
        Write-Host "PING $ip ---> ERROR" -ForegroundColor Red
        return $false
    }
}

Write-Host "===== MONITOREO DE BASE DE DATOS =====" -ForegroundColor Cyan

# 1. PRESUPUESTO
if (Test-Ping -ip "10.72.40.61") {
    Start-Process "http://apppresupuestos.bdpst.com.bo/web/ingresoprincipal.aspx"
    Start-Process "mstsc.exe" -ArgumentList "/v:10.72.40.61"
    Write-Host "Recuerda: En el RDP buscar 'Presupuesto' → clic derecho → Task → Back Up..." -ForegroundColor Yellow
}

# 2. OSTICKET
if (Test-Ping -ip "10.72.40.24") {
    Start-Process "http://10.72.40.24/phpmyadmin/index.php?route=/database/export&db=osticket"
    Write-Host "Exportar y descargar BD 'osticket' desde el navegador." -ForegroundColor Yellow# checklist_bd.ps1
# Autor: Richard Poma - Monitoreo de BD
# Fecha: 2025

function Test-Ping {
    param([string]$ip)
    if (Test-Connection -ComputerName $ip -Count 2 -Quiet) {
        Write-Host "PING $ip ---> OK" -ForegroundColor Green
        return $true
    } else {
        Write-Host "PING $ip ---> ERROR" -ForegroundColor Red
        return $false
    }
}

Write-Host "===== MONITOREO DE BASE DE DATOS =====" -ForegroundColor Cyan

# 1. PRESUPUESTO
if (Test-Ping -ip "10.72.40.61") {
    Start-Process "http://apppresupuestos.bdpst.com.bo/web/ingresoprincipal.aspx"
    Start-Process "mstsc.exe" -ArgumentList "/v:10.72.40.61"
    Write-Host "Recuerda: En el RDP buscar 'Presupuesto' → clic derecho → Task → Back Up..." -ForegroundColor Yellow
}

# 2. OSTICKET
if (Test-Ping -ip "10.72.40.24") {
    Start-Process "http://10.72.40.24/phpmyadmin/index.php?route=/database/export&db=osticket"
    Write-Host "Exportar y descargar BD 'osticket' desde el navegador." -ForegroundColor Yellow
}

# 3. UIF
Start-Process "http://svr-apph/phpmyadmin/db_export.php?db=intranet"
Write-Host "Exportar y descargar BD 'uif' desde navegador." -ForegroundColor Yellow

# 4. SCRIPT EN 10.72.40.23
if (Test-Ping -ip "10.72.40.23") {
    Start-Process "mstsc.exe" -ArgumentList "/v:10.72.40.23"
    Write-Host "Ejecutar el script manualmente en el servidor y cambiar fecha de documentos." -ForegroundColor Yellow
}

# 5. COPIA DE BACKUP DESDE 10.72.40.26
$destino = "$env:USERPROFILE\Downloads"
$origen = "\\10.72.40.26\c$\BACKUPS BD"
if (Test-Path $origen) {
    Get-ChildItem -Path "$origen" -Filter "*PRESUPUESTO*" | Copy-Item -Destination $destino -Force
    Write-Host "Copia de archivos PRESUPUESTO desde $origen a Descargas completada." -ForegroundColor Green
} else {
    Write-Host "No se pudo acceder a $origen" -ForegroundColor Red
}

# 6. COPIA DESDE 10.72.40.14
$bkbd = "\\10.72.40.14\j\BKBD"
if (Test-Path $bkbd) {
    Write-Host "Copiar manualmente archivos desde: $bkbd" -ForegroundColor YelloW
    Start-Process "explorer.exe" $bkbd
} else {
    Write-Host "No se pudo acceder a $bkbd" -ForegroundColor Red
}

Write-Host "MONITOREO DE BD FINALIZADO " -ForegroundColor Cyan
Pause

}

# 3. UIF
Start-Process "http://svr-apph/phpmyadmin/db_export.php?db=intranet"
Write-Host "Exportar y descargar BD 'uif' desde navegador." -ForegroundColor Yellow

# 4. SCRIPT EN 10.72.40.23
if (Test-Ping -ip "10.72.40.23") {
    Start-Process "mstsc.exe" -ArgumentList "/v:10.72.40.23"
    Write-Host "Ejecutar el script manualmente en el servidor y cambiar fecha de documentos." -ForegroundColor Yellow
}

# 5. COPIA DE BACKUP DESDE 10.72.40.26
$destino = "$env:USERPROFILE\Downloads"
$origen = "\\10.72.40.26\c$\BACKUPS BD"
if (Test-Path $origen) {
    Get-ChildItem -Path "$origen" -Filter "*PRESUPUESTO*" | Copy-Item -Destination $destino -Force
    Write-Host "Copia de archivos PRESUPUESTO desde $origen a Descargas completada." -ForegroundColor Green
} else {
    Write-Host "No se pudo acceder a $origen" -ForegroundColor Red
}

# 6. COPIA DESDE 10.72.40.14
$bkbd = "\\10.72.40.14\j\BKBD"
if (Test-Path $bkbd) {
    Write-Host "Copiar manualmente archivos desde: $bkbd" -ForegroundColor YelloW
    Start-Process "explorer.exe" $bkbd
} else {
    Write-Host "No se pudo acceder a $bkbd" -ForegroundColor Red
}

Write-Host "MONITOREO DE BD FINALIZADO " -ForegroundColor Cyan
Pause

