# Laboratorio interactivo de Compras y Abastecimiento

Aplicación educativa para los temas 3.2–3.5 de Administración de Compras y Abastecimiento.

## Contenido
- **3.2. Proceso electrónico de datos:** sistemas de compra, controles, trazabilidad, validación y flujos de aprobación.
- **3.3. Relación con la organización:** coordinación con solicitantes, Producción, Mantenimiento, Almacén, Calidad, Ingeniería y Finanzas.
- **3.4. Requisición de compras:** formulario interactivo, validación de nueve criterios, vista previa y descarga de resumen TXT.
- **3.5. Programación de compras:** calculadora de requerimiento neto, múltiplos de compra y programación hacia atrás por días hábiles.
- **Evaluación:** 12 preguntas, retroalimentación por respuesta, progreso y resultados por tema.

## Publicación
Esta aplicación está en la carpeta laboratorio-3-2-3-5 del repositorio compras-game. El flujo de GitHub Actions en .github/workflows/pages.yml publica la raíz del repositorio y conserva el index.html existente; esta aplicación queda disponible en una ruta independiente:

https://angelmaltos03-alt.github.io/compras-game/laboratorio-3-2-3-5/

La primera publicación puede tardar unos minutos. Revisa **Actions** en GitHub y confirma que el flujo **Deploy static site to GitHub Pages** termine correctamente.

## Privacidad y alcance
La evaluación y los simuladores funcionan en el navegador. La aplicación no envía respuestas ni datos de la requisición a un servidor ni los guarda en una base de datos. La descarga genera un resumen de texto en el dispositivo del alumno.

Los resultados son didácticos. La fecha calculada excluye fines de semana, pero no festivos, cierres de planta, tareas en paralelo o márgenes de riesgo. En una organización real deben aplicarse sus autorizaciones y procedimientos.
