# Funkos MTY

**Plataforma digital para la venta y distribución de Funko Pops en Monterrey, Nuevo León.**

---

## 📋 Descripción del Proyecto

Funkos MTY es una aplicación web interactiva que actúa como catálogo y plataforma de gestión para un negocio especializado en la venta de coleccionables Funko Pop. La plataforma permite a los clientes:

- Explorar un catálogo dinámico de figuras Funko Pop
- Filtrar productos por categoría
- Consultar puntos de entrega disponibles
- Gestionar pedidos desde tiendas internacionales (Funko Shop y Popcultcha)
- Contactar al vendedor vía WhatsApp

---

## 🎯 Características Principales

### 1. **Catálogo Dinámico**
- Integración con Google Drive API para mostrar imágenes en tiempo real
- Categorización automática de productos:
  - Anime / Cómics
  - Películas / TV
  - Accesorios
  - Novedades
  - Ofertas
- Sistema de búsqueda y filtrado por categoría
- Soporte para badges especiales (Remates, Daño en caja)

### 2. **Sistema de Pedidos**
- **Funko Shop**: Información sobre pedidos desde funko-shop.com
  - Tiempo de entrega: ~2 semanas
  - Reglas de liquidación y pago en efectivo
  - Gestión de stock y reemplazos
  
- **Popcultcha**: Información sobre pedidos desde popcultcha.com.au
  - Envíos desde Australia a México
  - Soporte para preventas
  - Tiempo de entrega: 1-1.5 meses

### 3. **Puntos de Entrega**
- Entregas entre semana (martes, miércoles, viernes)
  - Centro de Monterrey - Correos
  - Horarios definidos
  
- Entregas sabatinas en múltiples ubicaciones:
  - HEB Hacienda los Morales
  - Mercado la Y
  - Nuevo Sur
  - Walmart La Pastora

- Opciones de envío:
  - Paquetería local y nacional
  - Servicios de entrega tipo Didi/Uber

### 4. **Integración de Comunicación**
- Botones de WhatsApp en todo el sitio
- Modal personalizado para mensajes con datos del cliente
- Generación automática de mensajes contextualizados
- Rastreo de eventos para análisis

### 5. **Analytics**
- Integración con Google Analytics 4
- Seguimiento de eventos:
  - Visualización de figuras
  - Contactos por WhatsApp
  - Navegación entre páginas

---

## 💻 Tecnología

| Aspecto | Detalles |
|--------|---------|
| **Frontend** | HTML5, CSS3, JavaScript Vanilla |
| **Diseño** | Responsive, Mobile-first |
| **API** | Google Drive API v3 |
| **Analytics** | Google Tag Manager / GA4 |
| **Hospedaje** | Compatible con cualquier servidor web estático |

### Librerías Externas
- **Google Drive API**: Gestión de imágenes y catálogo
- **Google Tag Manager**: Análisis y seguimiento
- **Google Fonts**: Tipografías (Bebas Neue, DM Sans)

---

## 🎨 Diseño y Estilos

### Paleta de Colores (CSS Variables)
```css
--bg: #0e0e0e              /* Fondo principal (negro) */
--surface: #181818         /* Superficies secundarias */
--card: #1c1c1c            /* Tarjetas */
--accent: #f5c518          /* Amarillo dorado (principal) */
--accent2: #e8533a         /* Rojo (acentos secundarios) */
--green: #25d366           /* Verde WhatsApp */
--text: #f0f0f0            /* Texto principal */
--muted: #777              /* Texto atenuado */
```

### Componentes Principales
- **Top Navigation**: Navegación sticky con menú hamburguesa responsive
- **Category Bar**: Barra de categorías con dropdowns agrupados
- **Grid de Productos**: Disposición adaptable (2, 3 o 4 columnas según pantalla)
- **Lightbox**: Modal para visualizar detalles de figuras
- **Name Modal**: Captura de datos para personalizar mensajes WhatsApp
- **Footer**: Información y CTA principal

---

## 🚀 Instalación y Configuración

### Requisitos Previos
- Navegador web moderno (Chrome, Firefox, Safari, Edge)
- Conexión a Internet
- Clave API de Google Drive

### Pasos de Configuración

#### 1. Obtener Clave API de Google Drive

1. Ir a [Google Cloud Console](https://console.cloud.google.com)
2. Crear un nuevo proyecto
3. Habilitar la **Google Drive API**
4. Crear credenciales: **Clave de API**
5. Restringir acceso a:
   - Google Drive API
   - Tu dominio (ej: funkos-mty.com)

#### 2. Configurar el Código

Editar `index.html` y actualizar las constantes:

```javascript
const DRIVE_API_KEY   = 'TU_CLAVE_API_AQUI';
const ROOT_FOLDER_ID  = 'ID_DE_TU_CARPETA_RAIZ';
const WA              = '528110408730';  // Número WhatsApp Business
```

#### 3. Estructurar Google Drive

Crear una carpeta raíz con subcarpetas nombradas según las categorías definidas en `FOLDER_GROUPS`:

```
📁 Funkos MTY (ROOT_FOLDER_ID)
├── 📁 Marvel
├── 📁 DC Comics
├── 📁 Dragón Ball
├── 📁 One Piece
├── 📁 Star Wars
├── 📁 Disney
├── 📁 POKEMON
├── 📁 Cascos
├── 📁 Cajas Funko
└── 📁 REMATES
```

Cargar imágenes de las figuras en las carpetas correspondientes. Las imágenes se mostrarán automáticamente.

#### 4. Desplegar

Subir `index.html` a tu servidor web (cualquier hosting estático funciona: Netlify, Vercel, GitHub Pages, etc.)

---

## 📱 Uso

### Para Clientes
1. Abrir el sitio web
2. Explorar catálogo usando filtros de categoría
3. Hacer clic en figuras para ver detalles
4. Usar botón "Preguntar por WhatsApp" para contactar
5. Completar formulario con nombre y datos
6. Se abrirá WhatsApp con mensaje personalizado

### Para Administrador
1. Agregar/eliminar carpetas en Google Drive
2. Cargar/actualizar imágenes de productos
3. El catálogo se actualiza automáticamente
4. Monitorear eventos en Google Analytics

---

## 🔧 Personalización

### Agregar Nueva Categoría

En `index.html`, sección `FOLDER_GROUPS`:

```javascript
const FOLDER_GROUPS = {
  'Tu Nueva Carpeta': 'Grupo Existente o Nuevo',
  // ... resto de categorías
};
```

Si deseas badges especiales (Remate, Daño):

```javascript
const FOLDER_FLAGS = {
  'Tu Nueva Carpeta': 'tu_flag_aqui',
};
```

### Personalizar Mensajes WhatsApp

Editar función `buildMsg()` para cambiar templates de mensajes según contexto.

### Cambiar Colores

Modificar variables CSS en la etiqueta `<style>`:

```css
:root {
  --accent: #F5C518;  /* Cambiar color principal */
  --green: #25D366;   /* Cambiar verde WhatsApp */
  /* ... más variables */
}
```

### Puntos de Entrega

Editar sección **PAGE: PUNTOS DE ENTREGA** en HTML para actualizar ubicaciones y horarios.

---

## 📊 Analytics y Seguimiento

### Eventos Registrados
- `page_view`: Cambio de página
- `ver_figura`: Usuario visualiza una figura
- `contacto_whatsapp`: Usuario inicia contacto vía WhatsApp

Visualizar en [Google Analytics Dashboard](https://analytics.google.com)

---

## 🐛 Troubleshooting

### Catálogo no carga
- Verificar que `DRIVE_API_KEY` sea válida
- Verificar que `ROOT_FOLDER_ID` exista y sea accesible
- Revisar consola del navegador (F12) para errores

### Imágenes no se cargan
- Confirmar que carpetas tienen imágenes
- Verificar que la API tiene permiso para acceder a Google Drive
- Esperar a que se cargue completamente (puede tomar varios segundos)

### WhatsApp no abre
- Verificar número de WhatsApp (`WA` variable)
- Asegurar conexión a Internet
- Usar navegador compatible con `wa.me` protocol

---

## 📝 Estructura de Archivos

```
funkos-mty/
└── index.html          # Archivo principal (HTML + CSS + JS)
└── README.md          # Documentación (este archivo)
```

---

## 🤝 Contacto y Soporte

**Funkos MTY**
- 📍 Monterrey, Nuevo León, México
- 📱 WhatsApp: [+52 81 1040 8730](https://wa.me/528110408730)
- 🌐 Sitio: Está viendo este sitio

---

## 📄 Licencia

Este proyecto es privado y está hecho a medida para Funkos MTY.

---

## 📅 Changelog

### v1.0 (Actual)
- ✅ Catálogo dinámico con Google Drive
- ✅ Sistema de categorías agrupadas
- ✅ Integración WhatsApp
- ✅ Información de puntos de entrega
- ✅ Reglas de pedidos (Funko Shop, Popcultcha)
- ✅ Diseño responsive y mobile-first
- ✅ Analytics con Google Analytics 4

---

**Última actualización:** 17 de Mayo, 2026
