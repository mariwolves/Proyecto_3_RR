# Proyecto_3_RR 📓💵
En este proyecto, se llevará a cabo un análisis de riesgo relativo y una validación de hipótesis utilizando una base de datos bancaria. Para ello, utilizaremos dos herramientas destacadas en el ámbito del análisis de datos: BigQuery y Looker Studio.



# Índice 
- [Introducción](#introducción)
- [Equipo 🤝](#equipo)
- [Herramientas :hammer_and_pick:](#herramientas)
- [Lenguajes](#lenguajes)
- [Procesamiento y análisis](#procesamiento-y-análisis)
  - [Procesamiento de los datos](#procesamiento-de-los-datos)
  - [Análisis exploratorio](#análisis-exploratorio)
  - [Validación de hipótesis](#validación-de-hipótesis)
- [Resultados](#resultados)
- [Hallazgos](#hallazgos)
- [Conclusiones](#conclusiones)
- [Recomendaciones](#recomendaciones)
- [Enlaces](#enlaces)
  
## Introducción
En el sector bancario, es crucial contar con la seguridad y certeza necesarias para tomar decisiones informadas y estratégicas. Para ello, se emplean diversas técnicas de análisis que permiten obtener una visión clara y fundamentada. Una de estas herramientas es el análisis del riesgo relativo, que nos proporciona un marco para evaluar probabilidades y tomar decisiones basadas en datos. Este análisis nos permitirá validar o refutar tres hipótesis clave.

En el desarrollo de estas hipótesis, se utilizarán dos poderosas herramientas de análisis de datos: BigQuery y Looker Studio, junto con una base de datos proporcionada por el banco "Super Caja". Estas herramientas facilitarán la comprensión y evaluación de los patrones de riesgo, permitiendo un enfoque basado en datos para la toma de decisiones financieras.


Hipótesis:
+ :one: “Los jóvenes tienen un mayor riesgo de impago”.
+ 2️⃣ “Las personas con más cantidad de préstamos activos tienen mayor riesgos de ser malos pagadores”.
+ 3️⃣ “Las personas que han retrasado sus pagos por más de 90 días tienen mayor riesgo de ser malos pagadores”.

Objetivos:
El propósito de este proyecto es verificar estas hipótesis a través del análisis de datos y ofrecer recomendaciones estratégicas fundamentadas en los resultados obtenidos, con la meta de mejorar las probabilidades de éxito del nuevo artista.
+	Desarrollar un marco de análisis: Establecer un método sistemático para analizar hitos financieros.
+	Contribuir a la solidez financiera: Aumentar la capacidad del banco para gestionar riesgos y optimiza   la toma de decisiones financieras.

## Equipo 
- [María José L](https://github.com/mariwolves)

## Herramientas
+ BigQuery  
+ Looker Studio
+ Excel
  
## Lenguajes
+ SQL
## Procesamiento y análisis
Este proceso se dividió en tres etapas, en cada una de las cuales se aplicaron técnicas y programas específicos de acuerdo con los objetivos planteados.
##  Procesamiento de los datos 
El tratamiento de los datos se realizó en BigQuery utilizando comandos SQL. Los pasos seguidos fueron los siguientes:
+ Identificar valores nulos a través COUNTIF e IS NULL.
+ Manejar datos nulos con COALESCE
+ Identificar duplicados a través de COUNT, GROUP BY, HAVING.
+ Manejar variables que no son útiles en el análisis a través de EXCEPT.
+ Convertir una cadena de texto a minúsculas con LOWER
+ Identificar datos discrepantes (outliers) en variables numéricas con MAX, MIN, AVG, STDDEV_POP y MEDIAL
+ Comprobar y modificar tipos de datos con SAFE_CAST y CAST.
+ Manejar valores outliers con winsorización: APPROX_QUANTILES(x, 100)[OFFSET(0)] y APPROX_QUANTILES(x, 100)[OFFSET(97)] Para establecer los límites de las variables a modificar, se llevó a cabo una investigación exhaustiva sobre cada una de ellas con el fin de determinar un punto de corte adecuado.
	+ [Edad mínima al momento del otorgamiento crédito MX](https://www.bbva.mx/educacion-financiera/creditos/ppi-como-solicitar-un-prestamo-personal.html#:~:text=Tener%20una%20edad%20mínima%20de,días%20al%20momento%20del%20otorgamiento)
	+ [Edad minima para crédito hipotecario CL](https://www.bancoestado.cl/content/bancoestado-public/cl/es/home/home/centro-de-ayuda/productos/creditos---bancoestado-personas/hipotecario---dudas-transversales---bancoestado-personas/-cual-es-la-edad-minima-y-maxima-para-contratar-un-credito-hipot.html#/)
	+ [Encuesta Nacional de Ingresos y Gastos de los Hogares 2022 (ENIGH) MX](https://www.inegi.org.mx/contenidos/programas/enigh/nc/2022/doc/enigh2022_ns_presentacion_resultados.pdf)
	+ [Tamaño promedio de los hogares CL](https://datasocial.ministeriodesarrollosocial.gob.cl/fichaIndicador/640/2)
+ Construir tablas auxiliares utilizando WITH.
+ Unir las tablas utilizando LEFT JOIN.

## Análisis exploratorio
+ Agrupar datos según variables categóricas a través de tablas y gráficas
+ Visualizar las variables categóricas a través de gráficos de barras y líneas
+ Aplicar medidas de tendencia central y dispersión (avg, median, max, min, standard deviation)
  
	+ Datos generales clientes
		+ ![image](https://github.com/user-attachments/assets/07658beb-e155-42bf-bfed-e279b0f53fbe)
 		+ ![image](https://github.com/user-attachments/assets/8859a223-e781-44d1-b6e9-d57d58b737fe)
     
   	+ Préstamos
   	  	+ ![image](https://github.com/user-attachments/assets/cb96f8d9-af2d-45b7-9f44-2829d9563de3)
		+ ![image](https://github.com/user-attachments/assets/527cb8e1-ab19-4282-94b1-da519e11a949)
		+ ![image](https://github.com/user-attachments/assets/5afdf699-0378-46ae-9074-f0315c4f9f42)
   	  
	+ Morosidad
		+ ![image](https://github.com/user-attachments/assets/189bc3b6-5890-4f99-8256-4aec55528687)
		+ ![image](https://github.com/user-attachments/assets/5c03d862-a0be-47af-882d-ae7b83523049)
    
	+ Salud financiera: Ratio de utilización en líneas de crédito y Relación deuda - patrimonio
   		+ ![image](https://github.com/user-attachments/assets/35246b24-9b93-4645-b2d2-d1ac24a2a4c3)
		+ ![image](https://github.com/user-attachments/assets/aa5b90cf-085a-49ed-a932-2b2203afddc8)
		+ ![image](https://github.com/user-attachments/assets/c3e0dc23-5e79-4a2d-a7ab-0d0d259bf6d5)

## Validación de hipótesis
La validación de hipótesis se realizó en BigQuery, y los resultados se visualizaron en gráficos mediante Looker studio
+ Análisis de riesgo relativo (RR)

## Resultados
### Validación de hipótesis
  + **Hipótesis 1**: “Los adultos jóvenes tienen un mayor riesgo de impago”
    + **Conclusión**: ✔️: 	Los datos confirman la hipótesis de que los adultos jóvenes tienen un mayor riesgo de impago en comparación con los adultos mayores y seniors. En particular, los adultos jóvenes (18-40 años) son el grupo que muestra mayor 					cantidad de malos pagadores, lo que sugiere un riesgo financiero más alto en este segmento etario.
				Los cuartiles con mayor riesgo relativo están en los rangos más bajos de edad. El cuartil 1, con personas de menor edad, presenta un riesgo relativo de 2.15, lo cual refuerza la idea de que los individuos más jóvenes dentro de 				los adultos tienen más probabilidad de ser malos pagadores.
     
![image](https://github.com/user-attachments/assets/cb8e1448-980e-4a0f-8413-e86a640e743c)
![image](https://github.com/user-attachments/assets/f4e01702-e35e-461f-afa7-7067173fef74)


  + **Hipótesis 2**: “Las personas con más cantidad de préstamos activos tienen mayor riesgos de ser malos pagadores”
    + **Conclusión**: ❌:	Los datos refutan la hipótesis, ya que el cuartil con mayor número de préstamos activos (cuartil 4) tiene el menor número de malos pagadores (104) y un riesgo relativo bajo (0.61). En cambio, el cuartil 1, con menos préstamos 				activos (1-5 préstamos), tiene el mayor número de malos pagadores (257) y el riesgo relativo más alto (2.15). A medida que la cantidad de préstamos activos aumenta, el riesgo relativo disminuye, lo que indica que las personas con 				más préstamos parecen tener un mejor comportamiento de pago en comparación con aquellas que tienen menos préstamos.	
      
![image](https://github.com/user-attachments/assets/1a129273-79b4-4bd3-9042-0a4593043c7a)
![image](https://github.com/user-attachments/assets/cc076cc4-d0ee-4698-b1ac-8b65a2dc148c)


  + **Hipótesis 3**: “Las personas que han retrasado sus pagos por más de 90 días tienen mayor riesgo de ser malos pagadores”
    + **Conclusión**: ✔️: 	Los datos validan la hipótesis. El cuartil 4, que representa a personas con mayor morosidad (retrasos de pago de más de 90 días), tiene 576 malos pagadores y un riesgo relativo extremadamente alto (44.31), esto nos confirma que 				tiene más de 40 veces el riesgo de impago comparado con aquellos que tienen un historial de morosidad más bajo. El riesgo relativo aumenta drásticamente con el nivel de morosidad. Las personas en el cuartil con mayor morosidad 				(cuartil 4) tienen un riesgo significativamente mayor de ser malos pagadores, comparado con los cuartiles de menor morosidad.
      
![image](https://github.com/user-attachments/assets/53e3d7f1-6e5d-469b-bea0-e031e93e43f0)
![image](https://github.com/user-attachments/assets/62c88d09-4db7-44bd-91bb-995451112e7f)

## Hallazgos

Las hipótesis presentadas no abordan el tema de salud financiera. Por esta razón, se ha decidido analizar los datos correspondientes a este apartado con el fin de identificar información adicional o relevante que pueda contribuir a las recomendaciones. Se aplicará la misma metodología utilizada para analizar las hipótesis con el fin de comprender a los malos pagadores y su comportamiento en el uso de líneas de crédito no garantizadas, así como su relación deuda-patrimonio.
![image](https://github.com/user-attachments/assets/c79007bd-9eeb-459d-b4db-47c9ababf01a)

+ Como podemos observar en la gráfica, en el cuartil con el mayor porcentaje de uso de crédito, se registra un total de 572 malos pagadores. Esto indica que una gran cantidad de estos prestatarios han utilizado el total de su crédito disponible (100%) o incluso ha excedido el límite asignado (más del 100%) en líneas de crédito no garantizadas.
+ La relación deuda/patrimonio es un indicador clave del riesgo de impago. Un incremento en esta relación se asocia con una mayor probabilidad de que los deudores se conviertan en malos pagadores, sugiriendo la necesidad de monitorear este indicador como parte de la evaluación del riesgo crediticio. Los prestatarios tienen una proporción muy alta de deudas en comparación con sus activos. Esto sugiere que están altamente apalancados, lo que significa que dependen más de dinero prestado que de su propio patrimonio.
  
![image](https://github.com/user-attachments/assets/949e3dc4-222b-4ea9-bbc8-3d826af7be53)
+ Uso de crédito / Retrasos totales: Las categorías "Muy Alto" y "Alto" tanto en relación deuda-patrimonio como en uso de crédito son las que tienen la mayor cantidad de retrasos totales. Específicamente, el segmento con relación deuda-patrimonio alta y uso de crédito muy alto presenta 2,615 retrasos. Esto indica que quienes tienen una relación deuda-patrimonio alta tienden a tener más retrasos cuando además su uso de crédito es elevado. Las categorías con bajos niveles de uso de crédito presentan una menor cantidad de retrasos en todas las relaciones deuda-patrimonio, lo que sugiere que hay una correlación inversa entre el uso moderado o bajo del crédito y los retrasos.
+ Uso de crédito / Préstamos totales: Los usuarios con relación deuda-patrimonio alta y uso de crédito moderado también tienen un número elevado de préstamos totales (19,152), aunque significativamente menor en comparación con el grupo de uso muy alto.
En general, mientras más alto es el uso de crédito, mayor es el total de préstamos, independientemente de la relación deuda-patrimonio.

## Conclusiones

El análisis realizado permite validar algunas hipótesis mientras que otras son refutadas, proporcionando información relevante sobre el comportamiento de los malos pagadores y los factores que inciden en el riesgo de impago. A continuación, se presentan las conclusiones principales:

+ Adultos jóvenes y riesgo de impago: La primera hipótesis se confirma: los adultos jóvenes, específicamente aquellos entre 18 y 40 años, presentan un mayor riesgo de impago en comparación con los adultos mayores y seniors. Los datos muestran que los más jóvenes dentro de este grupo son quienes enfrentan el mayor riesgo.

+ Número de préstamos activos y riesgo de impago: La segunda hipótesis es refutada, ya que los datos indican que las personas con menos préstamos activos tienen un mayor riesgo de impago. Contrario a lo esperado, aquellos con más préstamos tienden a tener un mejor comportamiento de pago.

+ Retrasos en pagos y riesgo de impago: La tercera hipótesis se confirma: los prestatarios con retrasos en los pagos superiores a 90 días muestran un riesgo extremadamente alto de impago. Este grupo tiene más de 40 veces el riesgo de impago en comparación con quienes tienen un historial de pagos más regular.

+ Salud financiera y uso de crédito: El análisis adicional sobre la salud financiera revela que los individuos con una alta relación deuda/patrimonio y un uso elevado de crédito tienen un mayor riesgo de retrasos en los pagos. Los que han utilizado o superado su límite de crédito disponible representan el mayor número de impagos. Además, se observa una relación inversa entre el uso moderado de crédito y la cantidad de retrasos, sugiriendo que un uso excesivo del crédito combinado con altos niveles de deuda es un indicador claro de riesgo financiero.

En resumen, los resultados muestran que los factores clave que contribuyen al riesgo de impago son la juventud, la morosidad en los pagos y el uso excesivo del crédito no garantizado.

## Recomendaciones

Con base en las conclusiones, se recomienda:
+ Nueva evaluación de clientes: Se recomienda realizar una reevaluación de los clientes, basada en los hallazgos de este informe, con el fin de actualizar los grupos de malos pagadores y sus comportamientos. Esto permitirá optimizar y minimizar los riesgos al momento de otorgar préstamos, evitando así impactos financieros negativos en el banco "Super Caja".

+ Establecimiento de políticas de mitigación de riesgos para clientes jóvenes: Dado que los clientes jóvenes presentan un mayor riesgo de impago, es recomendable implementar políticas de evaluación más rigurosas para este grupo. Esto podría incluir un análisis más profundo de su capacidad de pago o la exigencia de ingresos adicionales para determinados tipos de préstamos.

+ Evaluaciones más estrictas para la morosidad a largo plazo: El elevado riesgo de impago en clientes con morosidad superior a 90 días sugiere la necesidad de adoptar políticas de intervención temprana. Implementar estrategias más agresivas de prevención y recuperación de deuda en estos casos podría contribuir a mitigar el riesgo de pérdidas.

+ Revisión de los criterios para la concesión de múltiples préstamos: Aunque los clientes con múltiples préstamos no presentan un riesgo elevado en este momento, es fundamental realizar un seguimiento continuo de su capacidad de pago. A medida que aumenta el número de obligaciones crediticias, se deberá efectuar un análisis más detallado de su situación financiera global para evitar un posible deterioro de su comportamiento crediticio.

+ Monitoreo de la relación deuda-patrimonio: Los clientes con una alta relación deuda-patrimonio deben ser clasificados como de alto riesgo. Esto resalta la importancia de limitar el crédito otorgado a aquellos con una exposición financiera significativa. Desarrollar políticas que incentiven la reducción de esta relación podría mejorar la salud financiera general de los clientes y reducir el riesgo para la entidad.

Estas recomendaciones permitirán optimizar la gestión del riesgo crediticio, garantizando un enfoque más proactivo y eficaz en la evaluación y manejo de los clientes.




## Enlaces
### [Drive con Contenido](https://drive.google.com/drive/u/0/folders/1Z1Nknb1UHz6J3L0p2i6b0m6L6Q1o3OZn)

