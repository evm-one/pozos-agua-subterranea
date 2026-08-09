# Landing — Pozos de Agua Subterránea, S.A. de C.V.

Landing page de una sola vista para una empresa de perforación y equipamiento de pozos profundos, estudios hidráulicos y geohidrológicos, y obras hidráulicas.

**Esto es una preview de trabajo, no la versión de lanzamiento.** La página lleva `noindex` mientras queden los pendientes de abajo.

## Ver la página

- **Publicada:** GitHub Pages (rama `main`, carpeta raíz)
- **En local:** abre `index.html` en el navegador. No necesita servidor ni build.

## Cómo está hecha

Un solo archivo `index.html` con Tailwind por CDN y tokens de marca definidos en línea. Sin dependencias, sin paso de compilación.

- **Tipografía:** Archivo (display, con eje de anchura), IBM Plex Sans (cuerpo), IBM Plex Mono (datos técnicos)
- **Paleta:** derivada del logotipo — la tierra es la base, el azul-agua se reserva como acento de acción
- **Estructura:** 14 secciones, de header sticky a footer

### Elemento distintivo

La sección de trayectoria es un **corte estratigráfico**: cada etapa profesional es un estrato cuya altura es proporcional a su duración, y el descenso avanza en el tiempo hasta terminar en el acuífero, donde el marcador se convierte en el motivo del logotipo. Se revela con scroll y respeta `prefers-reduced-motion`.

## Calidad verificada

- Sin desbordamiento horizontal a 375 / 768 / 1024 / 1440 px
- Contraste de texto ≥ 4.5:1 en todos los pares (objetos gráficos ≥ 3:1)
- Foco de teclado visible en los 37 elementos interactivos
- `prefers-reduced-motion` respetado; sin él, el contenido se muestra igual
- Íconos en SVG inline, sin emojis
- Imágenes con `width`/`height` declarados y `loading="lazy"` salvo el hero

## Pendientes antes de publicar

| Pendiente | Detalle |
|---|---|
| **Autorización de clientes** | Pepsico, IBM, Omnilife y demás aparecen sin permiso confirmado |
| **Fotografía real** | Las 8 imágenes son temporales generadas por IA; sustituir por fotos del cliente |
| **Testimonios** | La sección existe comentada en el código; faltan testimonios reales |
| **Datos de contacto** | Teléfonos, WhatsApp, horario y domicilio sin confirmar |
| **Correo corporativo** | Se recomienda sustituir el `@hotmail` actual |
| **Activar FormSubmit** | El formulario envía a `pozosub@hotmail.com` vía FormSubmit. Falta que alguien con acceso a ese buzón pulse el enlace del correo de confirmación del primer envío |
| **Aviso de privacidad** | Por redactar y enlazar |
| **Logotipo vectorial** | El archivo entregado es un PNG dentro de un envoltorio SVG, no vector real |
| **Trámites CONAGUA** | Fila de objeciones y pregunta de FAQ comentadas hasta confirmar el servicio |
| **Tailwind por CDN** | Compilar a CSS local antes de lanzar |
| **Quitar `noindex`** | Sólo cuando lo anterior esté resuelto |

Todo lo no confirmado está marcado en el código con `<!-- POR VALIDAR: ... -->`.

## Estructura

```
index.html                     la landing completa
img/                           imágenes y logotipo web
design-system/                 sistema de diseño del proyecto
assets/                        documentos internos (fuera del repo, ver .gitignore)
```

## Formulario

El formulario de cotización usa [FormSubmit](https://formsubmit.co/), que no requiere servidor ni registro.

- **Destino:** `pozosub@hotmail.com`
- **Método:** `POST` a `https://formsubmit.co/pozosub@hotmail.com`
- **Tras enviar:** redirige a `gracias.html`
- **Antispam:** campo señuelo `_honey`; el captcha va desactivado para no meter una pantalla intermedia entre el usuario y el envío

### Activación (obligatoria, una sola vez)

FormSubmit no reenvía nada hasta que el buzón de destino confirma. Al primer envío manda un correo a `pozosub@hotmail.com` con un enlace de activación; hasta que alguien lo pulse, los envíos se pierden.

Después de activar, FormSubmit facilita un alias con el que sustituir la dirección en el `action` para que el correo no quede a la vista de rastreadores de spam.
