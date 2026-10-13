# Primera prueba: Client y Server en la misma PC

Ejemplo para familiarizarte con Modbus Audit V1.0.7 usando memoria emulada.

## Preparar Server

1. En **Modbus Server**, agrega un dispositivo TCP.
2. Configura IP de escucha `127.0.0.1`, puerto `1502` e ID `1`. Guarda la conexión.
3. Crea un bloque FC03, base `0`, dirección inicial `0`, cantidad `4` y valores iniciales `0`.
4. En su mapa, selecciona tipo `UInt16` y orden `Normal`.
5. Inicia la escucha con el control del Server.

## Preparar Client

1. Agrega un dispositivo TCP en **Modbus Client**.
2. Configura destino `127.0.0.1`, puerto `1502` e ID `1`. Guarda.
3. Crea un bloque FC03, base `0`, dirección `0`, cantidad `4` e intervalo `1000` ms.
4. Selecciona `UInt16` y `Normal`; inicia el sondeo del bloque.

Deberías ver cuatro registros con valor cero. En el visor aparecerán las peticiones Client y las respuestas Server.

## Escribir y comprobar

Selecciona el primer tag Client y escribe `123`. Para un UInt16 individual se usa FC06. La lectura posterior debe recuperar `123`, y el primer registro del Server debe mostrar el mismo valor.

Para probar Float32, detén el sondeo y configura **ambos bloques** con `Float32` y orden `Normal`. Reinicia el sondeo, selecciona el primer registro y escribe `5.6`. Se usarán dos palabras y FC16. La interpretación puede mostrar una aproximación de 5.6 propia de la precisión Float32.

Prueba **Mapa Modbus → Exportar mapa** en cada rol para revisar sus CSV. Al terminar, usa **Detener Comunicaciones**.

Si el puerto 1502 está ocupado, usa otro puerto libre en ambos extremos. Si falla, consulta la [guía de problemas](solucion-de-problemas.md).
