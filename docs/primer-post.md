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




