<div align="center">

# Elisa

**El cliente de APIs que habla todos tus formatos.**

Importa colecciones y entornos de Postman, Insomnia, OpenAPI y más. Prueba, automatiza y comparte con un motor nativo en Rust.

[![Última versión](https://img.shields.io/github/v/release/CesarMartinez7/elisa-releases?label=versi%C3%B3n&color=e36b5b)](https://github.com/CesarMartinez7/elisa-releases/releases/latest)
[![Descargas](https://img.shields.io/github/downloads/CesarMartinez7/elisa-releases/total?label=descargas&color=f5968b)](https://github.com/CesarMartinez7/elisa-releases/releases)
![Plataforma](https://img.shields.io/badge/Windows-10%20%7C%2011-0078d4)
![Hecha con](https://img.shields.io/badge/Rust%20%2B%20Tauri%202-orange)

[**Descargar para Windows**](https://github.com/CesarMartinez7/elisa-releases/releases/latest) · [Usar en el navegador](https://elisa.rest) · [Todas las versiones](https://github.com/CesarMartinez7/elisa-releases/releases)

</div>

---

> [!NOTE]
> Este repositorio **solo publica los instaladores** de Elisa y el archivo que usan las actualizaciones automáticas. El código fuente vive en otro repositorio.

## Descarga

Entra a la [última versión](https://github.com/CesarMartinez7/elisa-releases/releases/latest) y descarga uno de estos archivos:

| Archivo | Para qué sirve |
| --- | --- |
| `Elisa_<versión>_x64-setup.exe` | **Recomendado.** Instalador para tu usuario (no pide permisos de administrador). |
| `Elisa_<versión>_x64_en-US.msi` | Instalador MSI, útil para instalaciones administradas en empresas. |
| `*.sig` | Firmas de los instaladores (las usa el actualizador). |
| `latest.json` | Manifiesto de actualizaciones automáticas. No hace falta descargarlo. |

### Requisitos

- Windows 10 u 11 de 64 bits.
- [Microsoft Edge WebView2](https://developer.microsoft.com/microsoft-edge/webview2/). Ya viene en Windows 11 y en Windows 10 actualizado; si falta, el instalador lo descarga.

### Instalación

1. Descarga el `.exe` de la última versión.
2. Ábrelo y sigue los pasos.
3. Si Windows muestra **"Windows protegió su PC"** (SmartScreen), haz clic en **Más información → Ejecutar de todas formas**. Aparece porque el instalador aún no tiene un certificado de firma de código de Windows; las actualizaciones sí van firmadas (ver [Seguridad](#seguridad)).

## ¿Qué trae Elisa?

- **Motor nativo en Rust**: en escritorio las peticiones salen desde Rust, sin CORS, con timeouts, multipart y cookies.
- **Importa lo que ya tienes**:
  - **Colecciones:** Postman (v2.0 y v2.1), OpenAPI 3, Swagger 2, Insomnia (v4 y v5), HAR, SoapUI, Markdown y cURL.
  - **Entornos:** Postman, Insomnia, `.env` y JSON.
- **Generador de código**: cURL, fetch, Axios, Python, Go, C#, Java, PHP, PowerShell y HTTPie.
- **Paleta de comandos** (`Ctrl + K`) y atajos configurables.
- **Scripts pre-request y tests** compatibles con la API `pm` de Postman.
- **Workspaces en equipo** con roles (propietario, editor, lector) y cambios en tiempo real.
- **SmartDocs**: documentación automática de tus colecciones.
- **Modo local**: úsala sin cuenta, todo se guarda en tu equipo.
- **Más de 18 temas**: Dracula, Nord, Tokyo Night, Catppuccin, Carolina…

## Actualizaciones

Elisa se actualiza sola: al abrirla busca una versión nueva y, si la hay, la descarga, verifica su firma, la instala y se reinicia.

En **Configuración → Acerca de** puedes:

- ver la versión instalada y si hay una nueva;
- activar o desactivar las **actualizaciones automáticas**;
- instalar cualquier versión publicada, **también una anterior**. Al volver a una versión anterior se desactivan las actualizaciones automáticas para que no se reinstale la última sola; puedes activarlas de nuevo cuando quieras.

> [!IMPORTANT]
> Si tienes la **v1.0.7**, instala a mano la [última versión](https://github.com/CesarMartinez7/elisa-releases/releases/latest). Esa versión abría la ventana en blanco y no alcanza a actualizarse sola. Desde la v1.0.8 las actualizaciones funcionan normalmente.

## Seguridad

Cada instalador se publica con su firma (`.sig`), generada con [minisign](https://jedisct1.github.io/minisign/) por el pipeline de publicación. La app **solo instala actualizaciones cuya firma coincide** con esta clave pública, que va incluida en Elisa:

```text
untrusted comment: minisign public key: 407B20E8A4FF08EF
RWTvCP+k6CB7QJus4gvTOWFVpQT5fwglskvshOtbC4OJc53gjEmjBOAA
```

Para verificar un instalador a mano, guarda la clave como `elisa.pub` y el `.sig` descargado, y ejecuta:

```bash
# El .sig de Tauri viene en base64: primero se decodifica
base64 -d Elisa_1.0.9_x64-setup.exe.sig > Elisa_1.0.9_x64-setup.exe.minisig
minisign -Vm Elisa_1.0.9_x64-setup.exe -x Elisa_1.0.9_x64-setup.exe.minisig -p elisa.pub
```

Si ves `Signature and comment signature verified`, el archivo es auténtico.

## Versión web

¿No quieres instalar nada? Elisa también funciona en el navegador: **[elisa.rest](https://elisa.rest)**. La versión web siempre está al día. Algunas funciones de escritorio (motor Rust sin CORS, actualizaciones) son solo de la app instalada.

## Problemas conocidos

| Problema | Solución |
| --- | --- |
| La ventana abre en blanco (v1.0.7) | Instala la última versión a mano. |
| SmartScreen bloquea el instalador | **Más información → Ejecutar de todas formas**. |
| No se actualiza sola | Revisa que las actualizaciones automáticas estén activas en **Configuración → Acerca de** y que tengas internet; también puedes pulsar **Buscar actualizaciones**. |

---

<div align="center">
Hecha con Rust, Tauri y React.
</div>
