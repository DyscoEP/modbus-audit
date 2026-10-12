# Modbus Audit

**Lee, escribe y entiende tus comunicaciones Modbus.**

Herramienta de escritorio portable para Windows x64, desarrollada por **DYSCO**, para probar dispositivos Modbus, emular memoria de un servidor y revisar las peticiones y respuestas de sus propias comunicaciones.

Pensada para diagnóstico, pruebas de integración y aprendizaje de Modbus TCP y Modbus RTU.

> **Descarga pendiente.** Este repositorio contiene la documentación del producto. Todavía no hay ejecutables ni una versión pública disponible. La documentación describe la versión de desarrollo **3.8**.

[Guía de uso](docs/guia-de-uso.md) · [Prueba TCP local](docs/prueba-local.md) · [Solución de problemas](docs/solucion-de-problemas.md) · [Reportar un problema](https://github.com/DyscoEP/modbus-audit/issues/new/choose)

## Qué puedes hacer

| Función | Características |
|---|---|
| Cliente Modbus | TCP y RTU; lectura de coils, discrete inputs, holding registers e input registers. |
| Bloques de tags | Dirección inicial, cantidad, prefijo e intervalo de sondeo configurable desde 50 ms; segmentación de lecturas grandes. |
| Escritura | Coils y holding registers, valores individuales o listas, con lectura posterior de comprobación. |
| Interpretación | UInt16/Int16, UInt32/Int32, UInt64/Int64, Float32 y Float64; orden de bytes y palabras configurable por bloque. |
| Direccionamiento | Base 0 o 1; dirección del usuario, dirección en trama y referencia clásica de 5 o 6 dígitos. |
| Servidor Modbus | Memoria TCP o RTU editable localmente; responde a lecturas y escrituras de clientes externos. |
| Visor de tráfico | Peticiones y respuestas reales, bytes en hexadecimal o decimal y contexto Client/Server. |
| Exportación | Tags, mapas de bloques Client/Server y tráfico a CSV. |
| Proyectos | Guardar y abrir configuraciones y bloques en JSON. |
| Escritorio | Controles generales y locales, consulta de IPv4/MAC y ejecución minimizada en la bandeja de Windows. |

## Protocolos y funciones

| Operación | Funciones Modbus |
|---|---|
| Lectura | FC01, FC02, FC03, FC04 |
| Escritura | FC05, FC06, FC15, FC16 |

El visor muestra el tráfico que Modbus Audit envía o recibe. **No captura de forma pasiva todo el tráfico de la red.**

El cliente y el servidor tienen una conexión configurable cada uno y varios bloques. Los bloques Client comparten el canal y se atienden en secuencia; el intervalo efectivo depende de la respuesta del dispositivo.

## Requisitos y estado de validación

- Windows de 64 bits. La validación de desarrollo se realizó en **Windows 11**; Windows 10 está pendiente de validar.
- La distribución portable no requiere instalar Python ni un servicio.
- Para RTU: adaptador serial con su controlador y puerto COM disponibles, más cableado y parámetros compatibles con el equipo.
- Interfaz en español.

Se documentaron 30 pruebas de protocolo, memoria, interfaz y controles en desarrollo, además de una escritura Float32 con comprobación entre Client y Server TCP locales. **La validación con un adaptador RTU físico está pendiente.** Esto no constituye una certificación de compatibilidad con todos los equipos.

## Descargas y versiones

Cuando se publique una versión, el paquete portable y sus notas estarán en [Releases](https://github.com/DyscoEP/modbus-audit/releases). El botón **Code → Download ZIP** descarga la documentación del repositorio; no instala el programa.

Consulta el [historial](CHANGELOG.md) para conocer el estado de publicación.

## Uso responsable

Las escrituras pueden cambiar valores del equipo conectado. Comprueba el destino, la función, la base y el mapa del fabricante antes de escribir. Para aprender, comienza con la [prueba local](docs/prueba-local.md).

## Soporte

Puedes [reportar un fallo o sugerir una mejora](https://github.com/DyscoEP/modbus-audit/issues/new/choose). Incluye versión, sistema operativo, protocolo y pasos para reproducirlo. Evita publicar credenciales, direcciones de instalaciones, datos de clientes o proyectos completos con información privada.

## Código y distribución

Este es el repositorio público de documentación y distribución de Modbus Audit; el código fuente se mantiene privado. La visibilidad del repositorio no convierte el producto en software de código abierto. Las condiciones de uso del ejecutable se incluirán antes de su primera publicación.

## Acerca de DYSCO

Modbus Audit forma parte de las herramientas de DYSCO para instrumentación y comunicación industrial. Visita [DYSCO](https://dyscoep.com/) para conocer la empresa y sus servicios.
