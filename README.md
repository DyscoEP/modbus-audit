# Modbus Audit

<img src="assets/mba-v1.png" alt="Icono oficial de Modbus Audit V1" width="180">

**Lee, escribe y entiende tus comunicaciones Modbus.**

Herramienta de escritorio portable para Windows x64, desarrollada por **DYSCO**, para probar dispositivos Modbus, emular memoria de un servidor y revisar las peticiones y respuestas de sus propias comunicaciones.

Pensada para diagnóstico, pruebas de integración y aprendizaje de Modbus TCP y Modbus RTU.

**Versión oficial V1.0.7 · compilación 3.16 · Windows x64 · Portable**

[**Descargar Modbus Audit para Windows x64**](https://github.com/DyscoEP/modbus-audit/releases/download/v1.0.7/Modbus-Audit-V1.0.7-build3.16-Windows-x64.zip)

Extrae el ZIP completo y ejecuta `Modbus-Audit.exe`. Incluye la guía de uso y los avisos de licencia.

[Guía de uso](docs/guia-de-uso.md) · [Ejemplo Client/Server](docs/prueba-local.md) · [Solución de problemas](docs/solucion-de-problemas.md) · [Reportar un problema](https://github.com/DyscoEP/modbus-audit/issues/new/choose)

## Qué puedes hacer

| Función | Características |
|---|---|
| Cliente Modbus | TCP y RTU; lectura de coils, discrete inputs, holding registers e input registers. |
| Bloques de tags | Dirección inicial, cantidad, prefijo e intervalo de sondeo configurable desde 50 ms; lectura de rangos amplios. |
| Escritura | Coils y holding registers, valores individuales o listas, con lectura posterior de comprobación. |
| Interpretación | UInt16/Int16, UInt32/Int32, UInt64/Int64, Float32 y Float64; orden de bytes y palabras configurable por bloque. |
| Direccionamiento | Base 0 o 1; dirección del usuario, dirección en trama y referencia clásica de 5 o 6 dígitos. |
| Servidor Modbus | Memoria TCP o RTU editable localmente; responde a lecturas y escrituras de clientes externos. |
| Analizador de tráfico | Peticiones y respuestas reales; hexadecimal/decimal, búsqueda, pausa del visor, copia de líneas y pantalla completa. |
| Exportación | Tags, mapas de bloques Client/Server y tráfico a CSV. |
| Proyectos | Guardar y abrir configuraciones y bloques en JSON. |
| Escritorio | Controles generales y locales, consulta de IPv4/MAC y ejecución minimizada en la bandeja de Windows. |

## Protocolos y funciones

| Operación | Funciones Modbus |
|---|---|
| Lectura | FC01, FC02, FC03, FC04 |
| Escritura | FC05, FC06, FC15, FC16 |

El visor muestra el tráfico que Modbus Audit envía o recibe. **No captura de forma pasiva todo el tráfico de la red.**

El cliente y el servidor tienen una conexión configurable cada uno y varios bloques. El intervalo efectivo de sondeo depende del tiempo de respuesta del dispositivo.

## Prerrequisitos y descargas oficiales

| Componente | Cuándo se necesita | Descarga |
|---|---|---|
| Windows x64 con red operativa | Para ejecutar y usar Modbus TCP | Usa los controladores de red de Windows o del fabricante de tu PC/NIC. |
| Controlador del adaptador USB–serial / USB–RS485 | **Necesario para RTU si tu adaptador requiere un driver y todavía no aparece como COM** | Descarga el controlador del fabricante del adaptador o del chip; enlaces oficiales debajo. |

Para RTU, instala únicamente el driver compatible con tu adaptador y Windows. Si ya aparece un puerto COM operativo, no hace falta instalar otro controlador. Un puerto serial nativo puede usar el controlador que ya proporciona Windows.

- **FTDI (chips FT232/FT2232 y otros compatibles):** [descargar controladores VCP oficiales](https://ftdichip.com/drivers/vcp-drivers/).
- **Silicon Labs CP210x:** [descargar controladores USB a UART VCP oficiales](https://www.silabs.com/software-and-tools/usb-to-uart-bridge-vcp-drivers).

Estas opciones son alternativas según el chip, no instalaciones obligatorias para todos. Para otros modelos, usa el soporte oficial del fabricante del adaptador. Puedes consultar el modelo o Id. de hardware en Administrador de dispositivos → Propiedades del dispositivo. El cableado RS232/RS485 y los parámetros seriales deben corresponder al equipo.

[Guía completa de prerrequisitos](docs/prerrequisitos.md)

## Requisitos de uso

- Windows de 64 bits con interfaz en español.
- Aplicación portable: extrae el paquete y ejecuta el programa.
- TCP: acceso de red al dispositivo y puerto configurado disponible.
- RTU: puerto COM operativo, controlador del adaptador y cableado compatible; velocidad, paridad e ID acordes con el equipo.
- Las direcciones, funciones y formatos deben corresponder al mapa Modbus del fabricante.

## Descargas y versiones

El paquete oficial está disponible en [Releases](https://github.com/DyscoEP/modbus-audit/releases/tag/v1.0.7). Contiene únicamente:

- `Modbus-Audit.exe`
- `LEEME.txt`
- `LICENSE.txt`
- `THIRD-PARTY-NOTICES.txt`

El [LEEME del paquete](LEEME.txt), la [licencia](LICENSE.txt) y los [avisos de terceros](THIRD-PARTY-NOTICES.txt) se conservan aquí con el mismo contenido que dentro del ZIP.

El botón **Code → Download ZIP** y los archivos automáticos **Source code** de GitHub descargan la documentación; el programa es el ZIP portable adjunto a la Release.

Consulta el [historial](CHANGELOG.md) para conocer el estado de publicación.

## Uso responsable

Las escrituras pueden cambiar valores del equipo conectado. Comprueba el destino, la función, la base y el mapa del fabricante antes de escribir. Para aprender, comienza con la [prueba local](docs/prueba-local.md).

## Soporte

Puedes [reportar un fallo o sugerir una mejora](https://github.com/DyscoEP/modbus-audit/issues/new/choose). Incluye versión, sistema operativo, protocolo y pasos para reproducirlo. Evita publicar credenciales, direcciones de instalaciones, datos de clientes o proyectos completos con información privada.

## Código y distribución

Este repositorio contiene documentación y distribución; el código fuente no se publica aquí. El código propio utiliza la [licencia MIT](LICENSE.txt) incluida en el paquete. Los componentes redistribuidos conservan sus licencias originales, reunidas en [THIRD-PARTY-NOTICES.txt](THIRD-PARTY-NOTICES.txt). Los logos Dysco y cloudLOGGER SCADA se conservan como identificadores de marca.

## Acerca de DYSCO

Desarrollado por **Dysco Exploration and Production**. Modbus Audit forma parte de **Field Tools de cloudLOGGER SCADA**. Visita [cloudLOGGER SCADA](https://cloudloggerscada.com) para conocer la suite.
