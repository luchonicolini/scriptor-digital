# Scriptor Digital

> **English:** An institutional website for academic guidance and digital development services. Built with Next.js and TypeScript, with service-specific routes, validated contact forms and server-side email delivery.

[Ver demo](https://scriptordigital.vercel.app/) · [Reportar un problema](https://github.com/luchonicolini/scriptor-digital/issues)

El sitio organiza dos líneas de servicio que necesitan mensajes y recorridos diferentes: orientación académica y desarrollo de soluciones digitales.
Presenta la propuesta, las páginas de servicio y un formulario que permite convertir una consulta en un contacto por correo.

**Estado:** sitio con URL pública. Su presencia en el portafolio no acredita por sí sola una relación laboral ni métricas comerciales.

## Vista previa

[COMPLETAR: captura de la portada y del formulario de contacto en escritorio y móvil]

## Funcionalidades

- Rutas para orientación académica, soluciones tecnológicas, casos, equipo y contacto.
- Tema claro y oscuro; interfaz adaptable.
- Formulario con validación en cliente y servidor.
- Envío de consultas mediante Resend.
- Notificación interna opcional por WhatsApp mediante CallMeBot.
- Metadatos, sitemap, robots y datos estructurados.
- Páginas de privacidad y términos.

## Stack y arquitectura

| Área | Implementación |
| --- | --- |
| Aplicación | Next.js 16, App Router, React 19 y TypeScript |
| Estilos e interacción | Tailwind CSS 4, Radix UI y Framer Motion |
| Formularios | React Hook Form y Zod |
| Servidor | Server Action para validar y enviar consultas |
| Integraciones | Resend, CallMeBot opcional y Vercel Analytics |
| Calidad disponible | ESLint y compilación de Next.js; sin suite automatizada propia |

El esquema compartido de contacto mantiene las reglas de validación en `lib/contact-schema.ts`.
La acción de servidor comprueba los datos y las credenciales antes de solicitar el envío;
el fallo de una notificación de WhatsApp no descarta un correo enviado correctamente.

| Ubicación | Responsabilidad |
| --- | --- |
| `app/` | Rutas, layout, metadatos y acción de contacto |
| `components/` | Secciones y componentes compartidos |
| `components/ui/` | Primitivas de interfaz |
| `lib/` | Esquemas, datos y utilidades |
| `public/` | Recursos estáticos |

## Cómo ejecutarlo

1. Instalá Node.js 20.9 o posterior y npm.
2. Cloná el repo e instalá sus dependencias:

   ```bash
   git clone https://github.com/luchonicolini/scriptor-digital.git
   cd scriptor-digital
   npm ci
   cp .env.example .env.local
   ```

3. Ajustá `.env.local` según el entorno:

   | Variable | Uso |
   | --- | --- |
   | `NEXT_PUBLIC_SITE_URL` | URL canónica; para desarrollo podés usar `http://localhost:3000` |
   | `RESEND_API_KEY` | Clave privada necesaria para enviar correos reales |
   | `WHATSAPP_PHONE_NUMBER` | Número de la notificación opcional |
   | `WHATSAPP_API_KEY` | Clave privada de CallMeBot; opcional junto con el número |

   Los valores de `.env.example` son ejemplos. Sin una clave válida de Resend, el sitio se puede recorrer,
   pero el formulario no entregará correos. Dejá vacías las variables de WhatsApp si no vas a usarlo.
   Antes de probar envíos reales, revisá el remitente y destinatario de `app/actions.ts`.

4. Iniciá la aplicación:

   ```bash
   npm run dev
   ```

5. Abrí [localhost:3000](http://localhost:3000).

## Verificación

```bash
npm run lint
npm run build
npm run start
```

Estos comandos analizan y compilan; no equivalen a tests de entrega de correo ni a pruebas de accesibilidad.
Las credenciales de proveedores deben permanecer en el servidor.
No hay un workflow de CI ni tests unitarios añadidos en este PR de documentación.

## Próximos pasos

- Agregar pruebas del esquema de contacto y de los resultados de la acción de servidor.
- Verificar estados de error, teclado y lector de pantalla en formularios.
- Documentar la configuración del proveedor y dominio de correo para cada entorno.
- Registrar casos y resultados comerciales solo cuando exista evidencia verificable.

## Colaboración y derechos de uso

Consultá [CONTRIBUTING.md](CONTRIBUTING.md) y [SECURITY.md](SECURITY.md).
Este repositorio contiene un sitio comercial: no se concede permiso de reutilización,
redistribución o explotación comercial sin autorización expresa de sus titulares.

## Pendientes de presentación

- [COMPLETAR: captura de la portada y del formulario de contacto en escritorio y móvil]

## Autor

[Luciano Nicolini](https://github.com/luchonicolini) · iOS Developer (Swift, SwiftUI), con experiencia full stack en proyectos con Next.js y Supabase.
