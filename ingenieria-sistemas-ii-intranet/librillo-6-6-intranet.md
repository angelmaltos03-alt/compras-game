# Librillo 6.6 · Intranet Black Ops
**Ingeniería de Sistemas II · ST-0704 · Séptimo cuatrimestre**

> Este librillo y el laboratorio web forman una sola experiencia. El librillo explica conceptos y resuelve ejemplos; el laboratorio permite practicar, equivocarse, recibir retroalimentación y defender decisiones.

## Ruta de aprendizaje

| Capítulo | Contenido | Práctica web |
|---|---|---|
| 1 | Intranet, Internet y Extranet | Evaluación |
| 2 | Arquitectura por capas y flujo de acceso | Puzzle 01 |
| 3 | Autenticación, autorización, RBAC, MFA y mínimo privilegio | Puzzle 02 |
| 4 | Disponibilidad, respaldo, RTO y RPO | Puzzle 03 |
| 5 | Integración empresarial, gobierno documental e indicadores | Evaluación |
| 6–7 | Caso TITAN e incidentes | Caso de consultoría |
| 8–9 | Taller, cálculos y solucionario | Informe final |

## 1. La intranet como sistema sociotécnico

Una intranet es un entorno privado de información y servicios digitales de una organización. Utiliza tecnologías y protocolos de Internet para que empleados y usuarios autorizados consulten recursos, colaboren y ejecuten procesos internos bajo controles de identidad y acceso.

No es solamente una página web. Integra personas, procesos, datos, aplicaciones, infraestructura y políticas. Su valor depende de que la tecnología responda a necesidades reales de la organización.

- **Internet:** red pública mundial.
- **Intranet:** entorno privado para usuarios internos autorizados.
- **Extranet:** acceso controlado para terceros, como proveedores o clientes.

**Ejemplo:** los empleados consultan procedimientos en la intranet; un proveedor consulta exclusivamente sus órdenes de compra en un portal de extranet.

**Atención:** que una intranet sea privada no significa que sea automáticamente segura. La seguridad depende de la identidad, permisos, segmentación, cifrado, registros y mantenimiento.

## 2. Arquitectura de referencia

Una arquitectura de intranet puede organizarse en seis capas:

1. **Presentación:** portal, formularios, menús y paneles.
2. **Aplicación:** reglas de negocio, autorizaciones y procesos.
3. **Identidad y acceso:** autenticación, SSO, MFA y RBAC.
4. **Integración:** APIs o servicios para ERP, WMS, nómina y otros sistemas.
5. **Datos:** bases de datos y repositorios documentales.
6. **Infraestructura y seguridad:** red, servidores, firewall, monitoreo y respaldos.

### Flujo de acceso resuelto

**Orden correcto:**
1. El usuario abre el portal.
2. El proveedor de identidad verifica credenciales y MFA.
3. El sistema evalúa el rol y los permisos.
4. La aplicación consulta el servicio autorizado y registra la operación.

La autenticación responde «¿quién eres?». La autorización responde «¿qué puedes hacer?». No son lo mismo.

### Ejemplo de integración de compras

Producción registra una requisición. La aplicación valida que el supervisor esté autorizado. Un servicio consulta existencias en ERP/WMS. Si hay material, genera surtido; si no, inicia el flujo de compra. El estado queda registrado y el solicitante puede darle seguimiento.

La intranet no debe conectarse con privilegios irrestrictos a la base de datos del ERP. Una API controlada permite exponer operaciones específicas y registrar su uso.

## 3. Seguridad y permisos

- **Autenticación:** verificación de identidad.
- **Autorización:** definición de acciones permitidas.
- **MFA:** uso de más de un factor para autenticarse.
- **TLS:** protección criptográfica de las comunicaciones.
- **RBAC:** permisos asignados a roles y roles asignados a usuarios.
- **Trazabilidad:** evidencia de quién hizo qué, cuándo y sobre qué recurso.

### Matriz de permisos resuelta

| Perfil | Permiso adecuado |
|---|---|
| Operador | Consultar procedimientos vigentes y registrar reportes autorizados. |
| Supervisor | Consultar su área y aprobar operaciones definidas. |
| Recursos Humanos | Gestionar expedientes laborales autorizados. |
| Administrador TI | Administrar infraestructura; no obtiene automáticamente permisos de negocio. |
| Proveedor | Consultar sus propias órdenes en un portal externo. |

**Principio de mínimo privilegio:** cada identidad recibe únicamente los permisos indispensables para su función.

## 4. Continuidad y disponibilidad

- **Disponibilidad:** proporción del tiempo que el servicio está operativo.
- **Respaldo:** copia recuperable de datos o configuraciones.
- **Redundancia:** componente alterno para reducir puntos únicos de falla.
- **RTO:** tiempo objetivo para recuperar el servicio.
- **RPO:** pérdida máxima de datos tolerable, medida en tiempo.

### Puzzle 03 resuelto

Si TITAN define RTO de 2 horas y RPO de 15 minutos, requiere respaldos frecuentes y probados, redundancia adecuada y un procedimiento de recuperación ensayado. La frecuencia de respaldo debe ser compatible con el RPO; la restauración o conmutación debe ser compatible con el RTO.

La replicación no sustituye al respaldo: también puede replicar borrados o errores.

### Cálculo de disponibilidad

En un mes de 30 días hay 720 horas. Si el servicio está disponible 96%, la indisponibilidad es 4%:

**720 × 0.04 = 28.8 horas fuera de servicio.**

## 5. Gobierno documental e integración

Cada documento debe tener propietario, revisión, aprobación, número de versión, fecha de vigencia, permisos, historial y mecanismo de retiro de copias obsoletas.

Sistemas relacionados:
- ERP: recursos y procesos empresariales.
- WMS: administración de almacenes.
- MRP: requerimientos de materiales.
- DMS: gestión documental.
- BI: análisis e indicadores.

### Indicadores

- Adopción = usuarios activos / usuarios habilitados × 100.
- Disponibilidad = tiempo disponible / tiempo programado × 100.
- Atención = solicitudes atendidas / solicitudes recibidas × 100.
- Reducción de tiempo = (tiempo anterior − tiempo actual) / tiempo anterior × 100.

**Ejemplo:** 570 usuarios activos de 950 habilitados = 60% de adopción y 380 usuarios inactivos.

**Ejemplo:** una requisición baja de 48 a 30 horas. Reducción = (48 − 30) / 48 × 100 = 37.5%.

## 6. Caso TITAN Manufacturing

TITAN tiene 1,200 trabajadores, tres plantas, tres turnos, ocho departamentos, 85 proveedores y 950 usuarios habilitados. La intranet presenta:

| Hallazgo | Situación actual | Meta |
|---|---:|---:|
| Disponibilidad mensual | 96% | 99.9% |
| Usuarios activos | 570 | 950 |
| Documentos sin versión identificada | 320 | 0 |
| Solicitudes de compra pendientes | 180 | Menos de 30 |
| Incidentes de acceso | 14 | 0 no autorizados |
| Reportes extraviados | 27 | 0 |

Restricciones: no reemplazar el ERP; soportar tres plantas; controlar accesos por puesto; separar proveedores de información interna; justificar la inversión.

### Incidente 1: credenciales comprometidas

**Respuesta correcta:** revocar sesiones y tokens, bloquear temporalmente la identidad, preservar registros, investigar alcance y restablecer credenciales con MFA. No borrar evidencia.

### Incidente 2: caída del servidor

**Respuesta correcta:** activar continuidad, conmutar al entorno alterno si existe, recuperar conforme a RTO/RPO, validar integridad, comunicar y documentar.

### Incidente 3: procedimiento obsoleto

**Respuesta correcta:** detener el uso de la copia dudosa, confirmar versión aprobada con el propietario, publicar versión controlada, retirar copias operativas antiguas y notificar a los turnos.

### Incidente 4: proveedor y fuga de datos

**Respuesta correcta:** revocar enlace expuesto, revisar accesos y habilitar portal externo/extranet aislado con identidad individual, mínimo privilegio y auditoría.

## 7. Taller de aplicación

1. En un mes de 30 días hubo 7.2 horas de interrupción. Calcula disponibilidad.
2. De 950 usuarios habilitados, 665 están activos. Calcula adopción e inactivos.
3. El tiempo de autorización baja de 36 a 27 horas. Calcula reducción.
4. Diseña una matriz de permisos para operador, supervisor, RR. HH., administrador TI y proveedor.
5. Dibuja la arquitectura de seis capas y marca el flujo de un empleado y un proveedor.
6. La dirección reduce 30% del presupuesto. Prioriza controles y explica el riesgo residual.

### Solucionario

1. Horas programadas = 720. Disponibilidad = (720 − 7.2) / 720 × 100 = **99%**.
2. Adopción = 665 / 950 × 100 = **70%**. Inactivos = **285**.
3. Reducción = (36 − 27) / 36 × 100 = **25%**.
4. Usa la matriz del capítulo 3 y justifica mínimo privilegio.
5. Debe incluir las seis capas, controles de identidad, API, datos protegidos y portal externo segregado.
6. Se evalúa la justificación: conservar identidad, RBAC, respaldos probados, trazabilidad, control documental y segregación externa.

## 8. Cómo usar el laboratorio web

1. Estudia el capítulo correspondiente.
2. Abre la pestaña **Aula** para revisar la explicación breve.
3. Entra al puzzle indicado y realiza el reto.
4. Si fallas, lee la retroalimentación, consulta la solución del librillo y vuelve a intentarlo.
5. Resuelve el caso TITAN y compara tus decisiones con el solucionario.
6. Revisa el informe final y explica qué criterio necesitas reforzar.

**La ingeniería se demuestra:** una intranet eficaz conecta procesos, entrega información confiable, protege datos, permite continuidad y produce resultados medibles.
