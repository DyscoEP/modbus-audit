# Solución de problemas

## Server TCP no inicia

Comprueba que la IP pertenece a la PC y que ningún otro servicio usa el puerto. Para aislar un problema, prueba `127.0.0.1:1502` con el cliente en la misma PC.

El programa informa la dirección, puerto y error original. Para errores 10013/10048 consulta reservas y procesos en escucha; una consulta sin resultados no descarta otras causas. Si cambias el puerto, cámbialo también en el cliente.

## Client no recibe datos

Revisa destino, puerto, ID, función, base, dirección y timeout. El Server debe estar en escucha y el cliente en sondeo. Usa el visor para distinguir petición enviada, respuesta recibida y error. En TCP remoto comprueba también la conectividad y las reglas de acceso de tu red.

Si otro programa muestra datos pero Audit no registra peticiones recibidas, verifica que ese cliente apunte realmente a Audit; puede estar consultando otro destino, una caché o simulación.

## Valor incorrecto o Faltan registros

Comprueba la documentación del dispositivo: función, dirección, base, tipo y orden de bytes/palabras. Float32 requiere dos registros consecutivos y Float64 cuatro. La columna decimal crudo permite comparar la memoria recibida con su interpretación.

## Escritura rechazada o comprobación fallida

FC02/04 son de solo lectura. Selecciona el primer registro de un valor y comprueba que toda la escritura cabe en el bloque. El dispositivo remoto también puede restringir ciertas direcciones.

Una comprobación fallida no garantiza que la escritura haya fallado. Revisa el valor en el equipo antes de repetir la operación.

## RTU no comunica

Verifica controlador, COM, cableado, ID y parámetros seriales iguales en ambos extremos. El puerto no debe estar ocupado por otra aplicación. Client y Server de la misma PC necesitan COM distintos conectados entre sí.

## La ventana desapareció al minimizar

Se encuentra en la bandeja de Windows y puede seguir comunicando. Haz clic en su icono para abrirla; usa el menú del icono para detener o salir.

## Reportar un problema

Incluye versión, Windows, TCP/RTU, función/base/dirección, resultado esperado, resultado real y pasos para reproducir. Adjunta solo capturas o tramas depuradas de información privada. No publiques proyectos completos de clientes.
