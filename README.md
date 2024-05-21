# Frubana


"Fuentes de datos requeridas: 

1. Tablas de ventas: 
12 archivos .pkl, un archivo por  mes correspondiente a las ventas del año 2023 para la región de Barranquilla. 
Los 12 archivos incluyen 502.154 registros y  14 columnas. 

2. Tabla de producto:
Formato CSV.
La tabla incluye 137 registros y 11 columnas. "	"Fuentes y caracteristicas de los datos: 
-Tabla de productos: debe especificar por id de producto, minimamente:
Nombre producto, categoria del producto.  
-Ordenes de venta: deben incluir el id de producto que corresponde a la llave respecto a la tabla de producto. Cada orden de venta debe incluir minimanente: 
id de producto,  fecha de venta, numero de orden de venta, unidades vendidas. 

Formatos o condiciones de los datos:
-Fecha de venta: formato fecha yyyy-mm-dd
-Unidades vendidas no puede contener valores menores o iguales a 0.

Principales transformaciones: 
-Unir los 12 archivos de ventas: consolidado de ventas.
-Creacion variable producto general en la tabla producto: ejemplo para 5 tipos de tomate, agruparlos como ""Tomate"".
 -Posteriormente unir el consolidado de ventas,  con la información de la tabla de producto de: Nombre producto, producto general y categoria a través de id producto. 
-Limpiar datos nulos según: id del producto, nombre producto, numero orden, categoria producto.
-Eliminar ordenes de venta cuya cantidad de venta por producto sea menor igual a 0. 
-Cálculo de frecuencia de ventas por pares de productos
-Construcción de matriz de frecuencias de ventas por pares de productos
-Cálculo de support y lift por pares de productos. 
-Cálculo de valor de refencia de ventas por producto (promedio de los últimos 6 meses, excluyendo el último mes)
-Creacion de umbrales para alertamiento  por producto general: 
Umbral inferior: promedio-sd
Umbral superior:  promedio+sd.
Se validara el desempeño del algoritmo de alertamiento con 1,2 y 3 desviaciones estándar.
-Flag anomalía por disminución: 1 aplica (valor referencia < umbral inferior), 0 no aplica
-Flag anomalía por aumento: 1 aplica (valor referencia > umbral superior), 0 no aplica."	"Preguntas a abordar: 
1. ¿Cuáles son los principales pares de productos  con asociación positiva y alta frecuencia de ventas?
2. ¿Cuáles son los principales productos qué presentan un comportamiento anómalo de ventas en el último mes? 
3. ¿Cuál es el comportamiento de ventas histórico por tipo de producto general (ejemplo: Tomate"") o por categoría (Ejemplo: Frutas)?.
4. ¿Cuál es la probabilidad de ocurrencia por par de productos en una misma venta? (Support).

El enfoque analitico es descriptivo. 

Técnicas y algoritmos a involucrar:
1. Market Basket Analysis: Matriz de frencuencia de ventas por pares de productos y el cálculo de support y lift.
2. Algoritmo de detección de anomalias con base en ventas históricas por producto en los últimos 6 meses,  definición de umbrales de alerta con base en desviación estándar respecto al promedio.
3. Gráficas de series de tiempo.
4. Técnicas de exploración y minería de datos


 "	"La herramienta para el desarrollo del dashboard es Power BI.

El procesamiento de datos se hará haciendo uso de: Excel y Python. 

Usuarios finales:  Gerente de ventas, Gerente de producto y analistas de datos asociados a dichas gerencias.

Las principales funcionalidades del dashboard incluyen:
 
-Matriz de frecuencia de ventas por pares de productos. 
-Top pares de productos según lift y frecuencia de ventas.
-Gráfica de ventas historicas con filtro por tipo producto general (ejemplo: Tomate)
-Top de alertas de productos con comportamiento anómalo de ventas en el último mes
filtro: Categoria de producto (Verduras, frutas, tubérculos). 
"	Market Basket Analysis	R1. Entrega de ranking de pares de productos con lift mayor a 1, según matriz de frecuencia de ventas como parte de Market Basket Analysis, que permita al negocio mejorar estrategias de venta cruzada de productos	Satisfacción del cliente mayor o igual al 70% mediante aplicación de encuesta	"La audiencia de nuestro artefacto corresponde al área de ventas y producto de Frubana.

Externalidades a tener en cuenta: situaciones puntuales que hayan afectado significativamente el comportamiento de ventas no fueron informadas por parte del cliente. Ejemplo: variaciones por cierre de operaciones y/o eventos promocionales. 

El artefacto final corresponde a un dashboard que contempla los principales resultados en relación a la venta de productos con 2 principales enfoques:
-Market basket analysis (por pares de productos)
-Detección de anomalias del comportamiento de ventas (por producto).

"
				Market Basket Analysis	R3. Consistencia del ranking de pares de productos según lift y frecuencia de ventas	"Los pares de productos en ranking deben:

1. Tener lift mayor a 1: Un valor de lift mayor que 1 indica una asociación positiva entre -A y B. Cuanto mayor sea el valor de lift, más fuerte es la asociación.
Fórmulas: 
-Lift(A -> B) = Soporte(A -> B) / (Soporte(A) * Soporte(B)).
-Soporte(A -> B) = Número de transacciones que contienen A y B / Número total de transacciones.

2. Estar organizados de mayor a menor frecuencia de ventas."	
				Detección de anomalias  respecto al comportamiento histórico de ventas por producto	R2. Entrega del top de alertas de productos  con  comportamiento anómalo (con mayor aumento y  disminución de ventas), que permita al negocio implementar acciones de control 	Satisfacción del cliente mayor o igual al 70% mediante aplicación de encuesta	
				Detección de anomalias  respecto al comportamiento histórico de ventas por producto	R4. Consistencia del algoritmo de alertamiento  para la identificación de productos con comportamientos anómalos de  ventas en el último mes con base en el comportamiento de los últimos 6 meses	"Verificación de reglas de alertamiento:

-El valor de referencia de ventas por producto se debe corresponder al promedio de ventas de los últimos 6 meses.

Los valores detectados como anomalias deben ser:
 -Menores a: promedio - sd 
 -o mayores a: promedio+ sd 
(Según el valor seleccionado para la desviación estándar:1sd,2sd o 3sd)"	
				Tablero de control	"R5. Visualización amigable del tablero de control, incluyendo 2 vistas: 
-Top pares de productos según lift y frecuencia de ventas
-Top de alertas de productos con comportamiento anómalo de ventas en el último mes"	Cumple	
				Tablero de control	R6. Tablero de Control desarrollado en Power BI	Cumple	
![image](https://github.com/christiansakerb/Frubana-Project-MB-AD/assets/47356178/0efbe5fe-1f8e-432f-b590-98a4ec5810de)

