# Script creado para Powershell - Windows

Requisitos:
Tener privilegios de Administrador de Dominios o permisos delegados.
WinRM debe estar activo en los equipos cliente

Creación del Script
´´bash
# Definir el nombre del equipo remoto
$equipo = "NOMBRE-DEL-PC"

# Ejecutar el comando de forma remota
Invoke-Command -ComputerName $equipo -ScriptBlock {
    Write-Host "Obteniendo datos de red para: $env:COMPUTERNAME" -ForegroundColor Cyan
    Get-NetIPConfiguration | Select-Object InterfaceAlias, IPv4Address, IPv4DefaultGateway
}
´
