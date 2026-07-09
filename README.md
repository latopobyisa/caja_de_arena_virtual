# Caja de Arena Virtual — Simulador 3D de Relieve Topográfico

Simulador interactivo de una caja de arena de realidad aumentada, hecho para navegador con Three.js. Esculpe terreno con el cursor, observa curvas de nivel calculadas en tiempo real, y explora un mar animado que ocupa siempre la cota más baja del modelo.

> Inspirado en los proyectos de AR Sandbox (UC Davis / Lawrence Hall of Science), pero construido desde cero para funcionar solo con navegador, sin Kinect ni proyector.

**[▶ Probar la demo en vivo](#)** — reemplaza este enlace por tu URL de GitHub Pages una vez publicado.

---

## Qué hace

- **Escultura sin clic:** el cursor levanta o hunde el terreno automáticamente al pasar sobre él, como una mano moviendo arena real. Mantén `Shift` para invertir la herramienta activa.
- **Curvas de nivel en tiempo real:** calculadas con un algoritmo de *marching squares* sobre la malla de elevación, con líneas maestras cada 5 intervalos, igual que un mapa topográfico impreso.
- **Mar animado:** ocupa siempre la cota 0 m (el valor más bajo posible del modelo), con oleaje generado proceduralmente, color que cambia según la profundidad, y espuma en la línea de costa donde rompen las olas.
- **Herramientas de escultura:** Levantar, Hundir, Suavizar, Nivelar — cada una con tamaño y fuerza de pincel ajustables.
- **Carga de DEM real:** importa tu propio modelo de elevación como imagen en escala de grises (por ejemplo, exportado desde QGIS) para esculpir sobre terreno real en vez de generado proceduralmente.
- **Calculadora de corte y relleno:** compara el estado actual del terreno contra un estado base y estima los volúmenes de corte, relleno y balance neto en m³, ajustando el tamaño de celda real.
- Rotación de cámara con el mouse, zoom con la rueda, y modo de rotación automática para presentaciones.

## Cómo usarlo

1. Abre `index.html` en cualquier navegador — no requiere instalación ni build.
2. Pasa el cursor sobre el terreno para esculpirlo con la herramienta activa en el panel derecho.
3. Arrastra para rotar la cámara; la rueda del mouse hace zoom.
4. Activa o desactiva curvas de nivel y mar desde el panel, y ajusta la equidistancia, el oleaje, el tamaño de pincel y la fuerza a tu gusto.
5. Para trabajar sobre un terreno real, exporta un DEM como imagen en escala de grises (blanco = mayor elevación) y cárgalo con el botón **"Cargar imagen de elevación"**.

## Stack técnico

- **Three.js** (r128) para el render 3D, geometría de malla manual, y `OrbitControls` para la cámara.
- **Marching squares** implementado desde cero para generar las curvas de nivel como segmentos vectoriales sobre la malla de elevación.
- **Canvas 2D** para generar la textura de color del terreno (LUT de colores por elevación) y componerla con las curvas antes de aplicarla como mapa en el material 3D.
- Vanilla JavaScript, sin frameworks ni build step — un solo archivo HTML.

## Ideas para extender

- Delineación de cuencas hidrográficas a partir del modelo de elevación.
- Modo multijugador/colaborativo para esculpir el mismo terreno entre varios usuarios.
- Exportar el modelo esculpido como malla `.glb` o el mapa de curvas como `.geojson`.
- Guía docente para uso en talleres de topografía y geomorfología.

## Créditos

Desarrollado por **Isabella Armendariz Miranda** ([@latopobyisa](https://www.instagram.com/latopobyisa)), estudiante de Ingeniería Topográfica (Universidad del Valle), en colaboración con Claude (Anthropic).

## Licencia

MIT — úsalo, modifícalo y compártelo libremente, incluso en contextos educativos.
