# Script creado para Powershell - Windows

### 📋 Requisitos:

- Tener privilegios de Administrador de Dominios o permisos delegados.
- WinRM debe estar activo en los equipos cliente

# Creación del Script
Get-RemoteNetworkInfo.ps1 
```bash 

# Definir el nombre del equipo remoto
$equipo = "NOMBRE-DEL-PC"

# Ejecutar el comando de forma remota
Invoke-Command -ComputerName $equipo -ScriptBlock {
    Write-Host "Obteniendo datos de red para: $env:COMPUTERNAME" -ForegroundColor Cyan
    Get-NetIPConfiguration | Select-Object InterfaceAlias, IPv4Address, IPv4DefaultGateway
}
```

#### Solamente deberíamos cambiar el Nombre del equipo en el ejemplo anterior.

### ⚠️ Errores más comunes (Troubleshotting):
| Problema | Solución |
| :--- | :--- |
|Access Denied | Ejecuta el PowerShell ISE o VS Code como Administrador. |
|WinRM service is not running | Verifica si el servicio está habilitado en el cliente.|
|Computer name cannot be resolved |Haz ping al nombre del equipo primero para verificar conectividad.|

---
#Recursos:

[Instalación y configuración de la gestión remota de Windows](https://learn.microsoft.com/es-es/windows/win32/winrm/installation-and-configuration-for-windows-remote-management)

**Etiquetas:** #Windows #PowerShell #Scripts #SoporteIT #Troubleshooting








