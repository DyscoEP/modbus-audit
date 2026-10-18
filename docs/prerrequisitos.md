# Prerrequisitos · Modbus Audit

| Componente | Cuándo se necesita | Descarga |
|---|---|---|
| Windows x64 con red operativa | Para ejecutar y usar Modbus TCP | Usa los controladores de red de Windows o del fabricante de tu PC/NIC. |
| Controlador del adaptador USB–serial / USB–RS485 | **Necesario para RTU si tu adaptador requiere un driver y todavía no aparece como COM** | Descarga el controlador del fabricante del adaptador o del chip; enlaces oficiales debajo. |

Para RTU, instala únicamente el driver compatible con tu adaptador y Windows. Si ya aparece un puerto COM operativo, no hace falta instalar otro controlador. Un puerto serial nativo puede usar el controlador que ya proporciona Windows.

- **FTDI (chips FT232/FT2232 y otros compatibles):** [descargar controladores VCP oficiales](https://ftdichip.com/drivers/vcp-drivers/).
- **Silicon Labs CP210x:** [descargar controladores USB a UART VCP oficiales](https://www.silabs.com/software-and-tools/usb-to-uart-bridge-vcp-drivers).

Estas opciones son alternativas según el chip, no instalaciones obligatorias para todos. Para otros modelos, usa el soporte oficial del fabricante del adaptador. Puedes consultar el modelo o Id. de hardware en Administrador de dispositivos → Propiedades del dispositivo. El cableado RS232/RS485 y los parámetros seriales deben corresponder al equipo.


Los enlaces llevan al sitio oficial del proveedor para obtener el controlador vigente. Esta documentación no instala componentes ni modifica el portable publicado.
