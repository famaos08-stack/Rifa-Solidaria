# 🐾 Rifa Solidaria · Salvemos a Fausto

Página web estática para la rifa solidaria por Fausto (moquillo canino).

## 📁 Archivos del proyecto

| Archivo | Propósito |
|---|---|
| `index.html` | Página principal (todo el código en un solo archivo) |
| `fausto.png` | Foto hero de Fausto |
| `formula-canglob-d.pdf` | Fórmula médica oficial (respaldo público) |
| `vendidos.json` | Lista de números vendidos (lo actualiza Power Automate) |
| `.nojekyll` | Evita que GitHub Pages procese con Jekyll |

## ⚙️ Antes de publicar — ajustar en `index.html`

Busca el bloque `CONFIG` al final del archivo y reemplaza:

```js
const CONFIG = {
  FORM_URL: 'https://forms.office.com/r/REEMPLAZAR_AQUI',  // ← Link del Microsoft Form
  FORM_PARAM: 'numero',                                      // ← Nombre del parámetro
  JSON_URL: 'vendidos.json',                                 // ← OK, dejar igual
  SORTEO_FECHA: '2026-06-01',                                // ← OK si es 1 de junio
  WA_MESSAGE: '...'                                          // ← OK, editable
};
```

También reemplaza el número Bre-B placeholder:
- Busca: `+57 300 000 0000` y ponlo con tu número real.

## 🚀 Deploy a GitHub Pages

1. Crea repo público en `famaos08-stack/rifa-fausto` (o el nombre que prefieras)
2. Sube los 5 archivos
3. Settings → Pages → Source: `main` / `/(root)` → Save
4. La URL será: `https://famaos08-stack.github.io/rifa-fausto/`

## 🔄 Cómo funciona la actualización de vendidos

1. Usuario hace clic en un número → abre Microsoft Form con `?numero=07`
2. Usuario diligencia el form + adjunta comprobante
3. Power Automate detecta nueva respuesta:
   - Guarda fila en Excel (OneDrive)
   - Lee toda la tabla
   - Genera `vendidos.json` actualizado
   - Lo sube al repo de GitHub via API (o a OneDrive público)
4. La página se actualiza cada 60 segundos automáticamente

## 📝 Pendientes

- [ ] Crear Microsoft Form y obtener URL pública
- [ ] Identificar parámetro real del primer campo del Form
- [ ] Crear flujo de Power Automate
- [ ] Configurar publicación de `vendidos.json`
- [ ] Reemplazar número Bre-B real
- [ ] Agregar datos bancarios reales (transferencia)
- [ ] Subir a GitHub Pages
