# Cómo Solucionar Errores de Conexión DNS en Ubuntu Linux (20/22/24 LTS)

**Fecha:** 8 de junio de 2026  
**Nivel:** Principiante/Intermedio  
**Entorno:** Ubuntu Desktop/Server (CLI)  
**Tiempo estimado de resolución:** 10-20 minutos

---

## 🎯 Problema

Usuarios o servidores con Ubuntu reportan que no pueden navegar por web (ej. `google.com`), aunque la conexión a internet por IP funciona correctamente. Los errores comunes incluyen:
- `Temporary failure in name resolution`
- `Could not resolve host`
- Navegadores mostrando "No se pudo encontrar la dirección IP".

Esto suele indicar un fallo en la resolución de nombres (DNS), no en la conectividad física.

---

## 🔍 Diagnóstico

Antes de aplicar soluciones, verificamos el estado actual de la red y DNS.

### Paso 1: Verificar conectividad básica (por IP)
Primero confirmamos que el servidor tiene acceso a internet saltando la resolución de nombres.
```bash
ping -c 4 8.8.8.8
```

![image alt](https://github.com/dieg0s-it/mi-portafolio-soporte-it/blob/d0791185ae156c459742325491389b10806cd11b/docs/Captura%20desde%202026-06-08%2011-45-11.png)


## Paso 2: Verificar resolución de nombres
Ahora intentamos resolver un nombre de dominio.
```bash
ping -c 4 google.com
```
![image alt](https://github.com/dieg0s-it/mi-portafolio-soporte-it/blob/b7b3fd695dfaa265f19ec85f3e3a04b46497ae6d/docs/Captura%20desde%202026-06-08%2013-36-17.png)

## Paso 3: Revisar configuración DNS actual
En versiones actuales de Ubuntu lo realizamos con Netplan
```bash
sudo cat /etc/netplan/*.yaml
```
## Paso 4: Verificar el resolv.conf
Esto lo hacemos para comprobar qué servidores DNS está realmente usando el sistema
```bash
cat /run/systemd/resolve/resolv.conf
```
## ✅ Solución aplicada
Como alternativa rápida, y para no editar archivos, optamos por reinicira el servicio de resolución:
```bash
sudo systemctl restart systemd-resolved
```
y verificamos que esté activo:
```bash
systemctl status systemd-resolved
```
![image alt](https://github.com/dieg0s-it/mi-portafolio-soporte-it/blob/8ae10ec3906df6d7a0fab88e0c5672bbba83acbb/docs/Captura%20desde%202026-06-08%2013-50-12.png)

## Validación final
Verificamos que la solución funcionó ejecutando nuevamente los comandos de diagnóstico.

Prueba 1: Resolución exitosa
```bash
nslookup google.com
```
Salida esperada: Muestra la dirección IP de Google (ej. 142.250.x.x) y el servidor DNS usado (Server: 8.8.8.8).

## Recursos:
[Documentación oficial de Netplan](https://netplan.io)

[Guía de resolución de problemas de red en Ubuntu](https://help.ubuntu.com/community/NetworkDocumentation)

**Etiquetas:** `#Linux` `#Ubuntu` `#DNS` `#Redes` `#SysAdmin`
