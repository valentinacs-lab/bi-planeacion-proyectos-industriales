# bi-planeacion-proyectos-industriales
Business Intelligence dashboard for project planning and budget control (simulated data)
# Dashboard de Planeación y Control de Proyectos Industriales

## Descripción
Dashboard de Business Intelligence desarrollado en Power BI para el seguimiento de planeación, presupuesto y avance operativo de proyectos industriales.

La solución permite analizar:
- Presupuesto planeado vs ejecutado
- Avance físico por actividad
- Variaciones presupuestales
- Identificación de actividades en riesgo
- Control operativo por responsable y estado

## Datos
Los datos utilizados son **simulados**, basados en escenarios reales de negocio, y fueron creados exclusivamente con fines demostrativos y de portafolio.  
No contienen información confidencial ni sensible.

## Modelo de Datos
- Tabla de hechos: Planeación del Proyecto
- Dimensiones:
  - Calendario
  - Actividad
  - Responsable
  - Estado del proyecto

Modelo en esquema estrella optimizado para análisis temporal y operacional.

## Indicadores Clave (KPIs)
- Presupuesto Planeado
- Presupuesto Ejecutado
- Variación Presupuestal (%)
- Avance Ejecutado (%)
- % de Actividades en Riesgo

## Tecnologías
- Power BI
- DAX
- Modelado Dimensional
- Visualización ejecutiva

## Contenido del Repositorio
- `/data`: datasets simulados (CSV)
- `/dashboard`: archivo Power BI (.pbix)
`/imagenes`: capturas del dashboard
- `/docs`: documentación en PDF

## Nota
Dashboard desarrollado con fines demostrativos y de portafolio, utilizando datos anonimizados y escenarios de negocio realistas.

_ _ _ _ _ _

### Medidas DAX
Presupuesto Planeado =SUM ( Fact_Planeacion_Nutresa[Presupuesto_Planeado] )

Presupuesto Ejecutado =SUM ( Fact_Planeacion_Nutresa[Presupuesto_Ejecutado] )

Variación Presupuesto =[Presupuesto Ejecutado] - [Presupuesto Planeado]

Variación Presupuesto % =DIVIDE ( [Variación Presupuesto], [Presupuesto Planeado], 0 )

Avance Planeado % =AVERAGE ( Fact_Planeacion_Nutresa[Avance_Planeado] )

Avance Ejecutado % =AVERAGE ( Fact_Planeacion_Nutresa[Avance_Ejecutado] )

Desviación Avance % =[Avance Ejecutado %] - [Avance Planeado %]

Actividades en Riesgo =CALCULATE (COUNTROWS ( Fact_Planeacion_Nutresa ),Fact_Planeacion_Nutresa[Estado] <> "En tiempo")

Total Actividades =COUNTROWS ( Fact_Planeacion_Nutresa )

% Actividades en Riesgo =DIVIDE ( [Actividades en Riesgo], [Total Actividades], 0 )

Presupuesto Planeado Evolución =[Presupuesto Planeado]

Presupuesto Ejecutado Evolución =[Presupuesto Ejecutado]

Alerta Presupuesto = IF ( [Variación Presupuesto %] > 0.05, "Sobre presupuesto", "Controlado" )



