# Guía de uso

Esta guía describe Modbus Audit V1.0.7, compilación 3.16. Consulta también el [LEEME incluido en el paquete](../LEEME.txt).

## Inicio y proyectos

Extrae todo el ZIP a una carpeta y ejecuta `Modbus-Audit.exe`. El programa comienza con un proyecto vacío. En **Archivo** puedes abrir y guardar proyectos JSON.

El explorador contiene **Modbus Client** y **Modbus Server**. En cada rol agrega el dispositivo, configura y guarda su conexión y después crea sus bloques. Seleccionar un dispositivo o un mapa solo cambia la vista; no inicia ni detiene la comunicación.

## Configurar el cliente

Para TCP configura IP/host remoto, puerto, ID Modbus y timeout. Para RTU configura COM, baudios, paridad, bits de datos, bits de parada, ID y timeout. El ID admitido es de 1 a 247.

Agrega un bloque con función de lectura, base, dirección inicial, cantidad, prefijo de tags e intervalo. El mínimo configurable es 50 ms. Los bloques comparten el canal y se atienden en secuencia: un equipo lento puede ampliar el intervalo real.

| FC | Área | Escritura remota |
|---|---|---|
| 01 | Coils | Sí: FC05/15 |
| 02 | Discrete inputs | No |
| 03 | Holding registers | Sí: FC06/16 |
| 04 | Input registers | No |

Los barridos grandes se dividen en solicitudes conforme a los límites del protocolo.

## Direcciones y mapa

Introduce las direcciones en decimal. Base 0 admite 0–65535; base 1, 1–65536. El bloque completo debe caber en ese rango.

La dirección en trama es siempre base 0: `dirección del usuario − base`. Base 0/dirección 0 y base 1/dirección 1 representan el mismo primer registro.

Para ese primer registro, las referencias clásicas son 00001 (coil), 10001 (discrete input), 40001 (holding register) y 30001 (input register). En 6 dígitos, el primer holding register es 400001. El prefijo es visual: no se transmite como parte de la dirección.

## Interpretación

Cada bloque conserva su tipo, orden y notación de mapa. La palabra decimal cruda permanece visible.

| Tipos | Registros por valor |
|---|---|
| UInt16, Int16 | 1 |
| UInt32, Int32, Float32 | 2 |
| UInt64, Int64, Float64 | 4 |

Orden disponible: normal, invertir bytes, invertir palabras o invertir bytes y palabras. Los registros posteriores al inicio de un valor se indican como continuaciones. Si falta espacio, aparece **Faltan registros**. Cambiar el formato reinterpreta los bytes; no modifica la memoria automáticamente. Coils y discrete inputs se representan como bits 0/1.

## Escribir desde Client

1. Selecciona el primer registro del valor en el mapa.
2. Comprueba tipo, orden y dirección del bloque.
3. Introduce el valor decimal; para Float usa punto decimal. Una lista separada por comas escribe valores consecutivos del mismo tipo.
4. Revisa el desglose: tag, mapa, base, dirección en trama, función, cantidad, palabras y bytes.
5. Ejecuta la escritura y revisa la lectura de comprobación.

La función se selecciona automáticamente: FC05/15 para coils y FC06/16 para holding registers. La lista completa debe caber en el bloque. No se permite comenzar una escritura desde una continuación ni escribir en FC02/04.

Con sondeo activo, la escritura se atiende entre lecturas. Si falla la comprobación, la escritura pudo haber llegado al equipo: verifica el destino antes de repetirla. Doble clic en la columna Tag permite renombrar un tag Client.

## Configurar Server

Para TCP selecciona una IP local y un puerto. `127.0.0.1` permite pruebas en la misma PC; `0.0.0.0` escucha en todas las interfaces. El cliente debe usar una IP de destino alcanzable, no `0.0.0.0`.

Para RTU selecciona un COM instalado y parámetros iguales a los del cliente externo. Client y Server RTU en la misma PC requieren puertos COM distintos conectados entre sí.

Crea bloques de las cuatro áreas de memoria. Los valores iniciales son palabras crudas decimales: un valor para repetir o una lista de la cantidad configurada. No se permiten rangos superpuestos dentro de la misma familia.

Puedes editar localmente un tag usando el formato de su bloque. Las escrituras remotas FC05/06/15/16 modifican la memoria. FC02/04 permiten edición local, pero siguen siendo de solo lectura para el cliente remoto.

**Iniciar Broadcast** es el nombre del control de escucha del Server en esta interfaz. No implica difusión de paquetes ni el uso del ID Modbus 0: el servidor responde a las solicitudes de los clientes.

## Controles y bandeja

**Iniciar Comunicaciones** inicia el Server configurado y el sondeo de todos los bloques Client. **Detener Comunicaciones** detiene ambos. Los controles locales del mapa Client afectan solo a su bloque; el control Server afecta a la escucha y al mapa completo del dispositivo.

Clic derecho en un dispositivo ofrece iniciar/detener y eliminar; en un bloque permite eliminarlo. El borrado detiene primero la comunicación correspondiente.

Minimizar oculta la ventana y conserva la ejecución. El icono de bandeja permite abrir, iniciar, detener y salir. Cerrar la ventana o seleccionar Salir termina el programa. Windows puede silenciar la notificación de segundo plano.

## Tráfico y exportaciones

Client muestra **TX REQUEST LOCAL / RX RESPUESTA REMOTA**. Server muestra **RX REQUEST REMOTA / TX RESPUESTA LOCAL**. El visor incluye hora, rol, protocolo, ID, función, extremo y bytes; permite hexadecimal o decimal, limpiar, seguir y exportar. Conserva hasta 5000 entradas. Las vistas previas no transmiten solicitudes.

Clic derecho en **Mapa Modbus → Exportar mapa** genera un CSV del bloque Client o Server, incluso detenido. Incluye direcciones, función, tipo, orden, palabra cruda, interpretación y estado. Client exporta sus últimos valores; sin lecturas deja los valores vacíos. Server exporta una instantánea de su memoria.

Archivo y la barra ofrecen también exportación de tags y tráfico CSV.

## Analizador de tráfico y presentación

Buscar filtra por texto de hora, nivel, origen, evento y bytes. Quitar filtro restaura las líneas disponibles. Pausar visor congela la vista; Client y Server continúan operando y el historial sigue rotando hasta 5000 registros. Pantalla completa conserva los mismos datos y filtros; Volver o Esc cierra esa vista sin detener la adquisición. Seleccionar una línea la copia; también puedes usar Copiar línea, Ctrl+C o el menú contextual.

El splash de inicio muestra la identidad del producto y se cierra al terminar la preparación. Ayuda → Acerca de reutiliza esa presentación con Cerrar y Ver licencia MIT. Las conexiones y bloques de ambos roles usan recuadros titulados y acciones arriba a la derecha.
