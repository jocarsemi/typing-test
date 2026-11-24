# TYPING TEXT - Prueba IES Ricardo Marín

Aplicación web autocontenida para medir las **palabras por minuto (PPM)** y la precisión
de los alumnos de ESO y Bachillerato en un test de mecanografía.

> URL de ejemplo (sustitúyela por la tuya):
> `https://<tu-usuario>.github.io/typing-test/`

---

## 🚀 Despliegue en GitHub Pages (paso a paso)

### 1. Crear el repositorio
1. Entra en [github.com](https://github.com) y pulsa **New repository**.
2. Nombre sugerido: `typing-test`.
3. Marca **Public** y pulsa **Create repository**.

### 2. Subir los archivos
Puedes hacerlo de dos formas:

**Opción A — Desde la web de GitHub:**
1. Pulsa **Add file → Upload files**.
2. Arrastra `index.html` y `README.md`.
3. Escribe un mensaje de commit y pulsa **Commit changes**.

**Opción B — Desde terminal:**
```bash
git init
git add index.html README.md
git commit -m "Typing test IES Ricardo Marín"
git branch -M main
git remote add origin https://github.com/<tu-usuario>/typing-test.git
git push -u origin main
