# Registro de Medidas – Franja Inferior (Footer)

Este documento registra los valores y clases originales de la franja inferior (footer) de la cartelera digital, permitiendo restaurarla a su configuración inicial en cualquier momento.

---

## 📐 Medidas Originales (Previas al ajuste)

### 1. Contenedor principal (`<footer>`)
- **Altura mínima:** `min-h-[140px]` (140 píxeles).
- **Relleno vertical (Padding Y):** `py-6` (24px arriba y abajo).
- **Relleno horizontal (Padding X):** `px-10` (40px a los lados).
- **Clase completa en HTML:**
  ```html
  <footer class="bg-zinc-100 text-zinc-900 py-6 min-h-[140px] px-10 flex justify-between items-center flex-shrink-0 z-10 shadow-[0_-4px_6px_-1px_rgba(0,0,0,0.1)]">
  ```

---

### 2. Bloque izquierdo (Título, Ubicación y Detalles)
- **Contenedor:**
  ```html
  <div class="flex flex-col justify-center gap-1.5">
  ```
- **Título de la propiedad (`#prop-title`):**
  - Tamaño de fuente: `text-3xl` (30px / 1.875rem).
  - Peso tipográfico: `font-semibold` (600).
  - Espaciado entre letras: `tracking-wide`.
  - Color: `text-zinc-800`.
- **Ubicación (`#prop-location`):**
  - Tamaño de fuente: `text-lg` (18px / 1.125rem).
  - Tamaño de icono SVG de ubicación: `w-5 h-5` (20px × 20px).
  - Separación icono-texto: `gap-2` (8px).
  - Color: `text-zinc-600`.
- **Detalles y características (`#prop-features`):**
  - Tamaño de fuente: `text-base` (16px / 1rem).
  - Separación entre características: `gap-6` (24px).
  - Margen superior: `mt-1` (4px).
  - Tamaño de iconos SVG (m², ambientes, dormitorios, parque/pileta): `w-5 h-5` (20px × 20px).
  - Color: `text-zinc-500`.

---

### 3. Bloque derecho (Precio)
- **Contenedor:**
  ```html
  <div class="flex flex-col justify-center items-end">
  ```
- **Precio (`#prop-price`):**
  - Tamaño de fuente: `text-5xl` (48px / 3rem).
  - Peso tipográfico: `font-light` (300).
  - Espaciado entre letras: `tracking-tight`.
  - Color: `text-zinc-900`.

---

### 4. Cálculo en JavaScript (`resizeCanvas`)
- En la función `resizeCanvas()` dentro de `index.html`:
  ```javascript
  canvas.height = container.clientHeight || (window.innerHeight - 140);
  ```

---

## 🔄 Cómo volver a estas medidas originales
Para restablecer estas medidas, simplemente reemplazá el bloque `<footer>` en `index.html` con las clases indicadas arriba y asegurate de que en `resizeCanvas()` reste `140`.

