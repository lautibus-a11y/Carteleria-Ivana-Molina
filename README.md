# Cartelera Inmobiliaria Digital – Ivana Molina & Asociados

Cartelera digital diseñada para ejecutarse de manera continua en Smart TVs en oficinas inmobiliarias, presentando propiedades con fotografía protagónica, diseño limpio y tipografía legible a distancia.

---

## 🎮 Controles y atajos de teclado

La cartelera está optimizada para controlarse fácilmente mediante teclado o control remoto:

| Tecla / Acción | Función |
| :--- | :--- |
| **B** | **Abrir / Cerrar el menú de administración y selector de propiedades**. |
| **Barra Espaciadora** | **Pausar / Reanudar** la reproducción automática (muestra indicador `⏸ Pausado`). |
| **Flecha Derecha (→)** | Avanzar a la **siguiente fotografía** o siguiente propiedad. |
| **Flecha Izquierda (←)** | Retroceder a la **fotografía anterior** o propiedad anterior. |
| **F** | Alternar modo **Pantalla Completa** (Full Screen). |
| **Esc** | Cerrar el menú de administración si está abierto. |

---

## 🔍 Menú de administración oculto (Tecla B)

Al presionar la tecla **B** se despliega el catálogo completo de propiedades:
1. **Pestañas de filtrado rápido**:
   - **Todas**: Muestra el catálogo total.
   - **Venta**: Filtra únicamente inmuebles en venta.
   - **Alquiler**: Filtra inmuebles en alquiler comercial o residencial.
2. **Buscador en tiempo real**: Escribí cualquier palabra clave (calle, localidad, tipo de propiedad, precio) para filtrar al instante.
3. **Selección inmediata**: Al hacer clic sobre cualquier propiedad, el menú se cierra y la cartelera salta directamente a proyectar dicho inmueble y sus fotografías en pantalla gigante.

---

## 🚀 Cómo ejecutar el proyecto localmente

Para que el navegador pueda cargar dinámicamente el archivo `data/propiedades.json` y todas las fotos sin restricciones de seguridad de origen local (CORS), se recomienda utilizar un servidor web estático liviano:

### Opción 1: Con Python (incorporado en Mac / Linux / Windows)
Abrí una terminal en la carpeta del proyecto y ejecutá:
```bash
python3 -m http.server 8080
```
Luego abrí en tu navegador:
```
http://localhost:8080
```

### Opción 2: Con Node.js (npx)
```bash
npx serve .
```

### Opción 3: Extensión de VS Code
Instalá la extensión **Live Server** y hacé clic en **"Go Live"** en la esquina inferior.

> [!NOTE]
> **Apertura directa con doble clic (`file://`)**:
> Si abrís `index.html` directamente haciendo doble clic desde el explorador de archivos, los navegadores modernos restringen las peticiones `fetch()` locales por seguridad. La cartelera cuenta con un mecanismo defensivo que cargará automáticamente las propiedades de respaldo desde `propiedades.js` para que nunca quede la pantalla en blanco.

---

## 📂 Estructura del proyecto

```text
Ivana Carteleria Blanca/
├── index.html                  # Aplicación principal para Smart TV
├── data/
│   └── propiedades.json        # Catálogo maestro de propiedades y configuración
├── assets/
│   ├── logo.png                # Logotipo oficial
│   ├── alquiler/               # Fotos de inmuebles en alquiler
│   ├── venta/                  # Fotos de inmuebles en venta
│   └── propiedades_de_presentacion/ # Fotos limpiadas en alta calidad
├── propiedades.js              # Respaldo de propiedades en memoria
├── README.md                   # Esta guía
└── Agenes.md                   # Especificación técnica y requerimientos del proyecto
```

---

## 📝 Cómo actualizar propiedades en `data/propiedades.json`

Podés abrir `data/propiedades.json` con cualquier editor de texto para:

### 1. Activar o desactivar una propiedad en la cartelera habitual
Modificá el campo `"activa"`:
```json
"activa": true    // Se mostrará en el ciclo automático de la cartelera
"activa": false   // No rotará en automático, pero seguirá disponible en el menú B
```

### 2. Cambiar tiempos de rotación
En la parte superior de `data/propiedades.json`:
```json
"configuracion": {
  "intervaloFotoMs": 7000,   // Tiempo por foto en milisegundos (7000 = 7 segundos)
  "transicionMs": 1500,      // Duración del fundido suave
  "repetir": true
}
```

### 3. Agregar una nueva propiedad
Agregá un bloque dentro del array `"propiedades"`:
```json
{
  "id": "nueva-propiedad-1",
  "activa": true,
  "orden": 1,
  "operacion": "EN VENTA",
  "titulo": "Casa Quinta Las Acacias",
  "ubicacion": "20 de Junio, La Matanza",
  "precio": "USD 180.000",
  "superficie": "1.200 m² terreno",
  "ambientes": "4 Amb.",
  "dormitorios": "3 Dorm.",
  "caracteristicas": [
    "Piscina",
    "Gran Parque"
  ],
  "imagenes": [
    "assets/venta/casas-quinta/nueva-propiedad/01.webp",
    "assets/venta/casas-quinta/nueva-propiedad/02.webp"
  ]
}
```

---

## 🌐 Publicación en Vercel

1. Subí los cambios a tu repositorio en GitHub:
   ```bash
   git add .
   git commit -m "feat: nuevas funcionalidades de cartelera"
   git push origin main
   ```
2. Al estar conectado a **Vercel**, el despliegue es completamente automático y el sitio web se actualizará en segundos.
3. En la Smart TV, abrí el navegador integrado con la URL de tu proyecto en Vercel. Presioná la tecla **F** para activar el modo pantalla completa.

