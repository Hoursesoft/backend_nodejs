# backend_nodejs
Backend de proyecto node js


# POSIBLES ERRORES Y COMO SOLUCINARLO

```
sh: 1: nodemon: not found
```

Esto significa que **Render no encuentra el comando `nodemon`** al ejecutar `npm run dev`.

### Causa

`nodemon` está instalado **como dependencia de desarrollo (`devDependency`)**, y en ambientes de producción como Render, **por defecto no se instalan las `devDependencies`**.

### Soluciones

#### ✅ Opción 1: Cambia el script a usar `node` en vez de `nodemon`

Edita tu `package.json`:

```json
"scripts": {
  "start": "node src/index.js",
  "dev": "nodemon src/index.js"
}
```

Y en Render, configura que ejecute `npm run start` (no `dev`). Esto es lo recomendado para producción.

#### ✅ Opción 2: Instala `nodemon` como dependencia normal (no recomendada para producción)

```bash
npm install nodemon --save
```

Esto fuerza que `nodemon` esté disponible también en producción, pero **no es buena práctica usar `nodemon` en producción** porque está hecho para desarrollo (reinicia el servidor con cada cambio de archivo).

---

**Resumen:** Render ejecuta en un entorno de producción, donde solo se instalan dependencias normales. Usa `node` en lugar de `nodemon` para desplegar.


