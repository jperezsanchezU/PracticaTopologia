
## M2.851 - Tipología y ciclo de vida de los datos
## Práctica 2: Limpieza y validación de datos

Se analizarán los datos de precios de vivienda con el objetivo de poder generar un modelo predictivo del precio de las mismas según distintas características de los inmuebles, ubicación, tamaño, calidades, antigüedad, etc...

Para ello se empleará un dataset de la web kaggle sobre inmuebles, de la competición House Prices: Advanced Regression Techniques.

La descargar, limpieza y análisis de datos se hará en código R, documentándolo con rmarkdown. Se adjuntan en la propia cuenta github los ficheros fuente, Practica1_topología_jperezsanchez.Rmd y el generado pdf.

# House Prices: Advanced Regression Techniques

## Análisis del precio de venta de inmuebles según distintas características

Se basa en la competición *kaggle* sobre técnicas de regresión avanzadas en precios de viviendas.

[House Prices: Advanced Regression Techniques](https://www.kaggle.com/c/house-prices-advanced-regression-techniques)

## Autor

José Pérez Sánchez

### 1. Descripción del dataset. ¿Por qué es importante y qué pregunta/problema pretende responder?

En este dataset se describen distintas características de casas así como el precio de éstas. Se trataría de crear métodos de regresión que nos permitan predecir el precio de una casa a partir de sus características. Esto es útil tanto para futuros compradores, que pueden estimar así si una vivienda está cara o barata según sus características y zona donde se encuentra y para los vendedores, que pueden estimar los precios adecuados para sus viviendas, al menos según el estado del mercado.

El dataset viene [descrito en inglés](https://storage.googleapis.com/kaggle-competitions-data/kaggle/5407/data_description.txt)  en la propia web de *kaggle*, traducido, los campos son:

MSSubClass: Tipo de vivienda. Valor discreto, factor.

MSZoning: Calificacion urbanística  del suelo. Valor discreto, factor.

       A	Agrícola
       C	Comercial
       FV	Residencial flotante
       I	Industrial
       RH	Residencial alta densidad
       RL	Residencial baja densidad
       RP	Residencial baja densidad, parques
       RM	Residencial densidad media
	
LotFrontage: Longitud de la parte de la propiedad que limita con la calle, en pies

LotArea: Tamaño de la propiedad en pies cuadrados

Street: Tipo de carretera de acceso a la propiedad

       Grvl	Grava	
       Pave	Pavimentado
       	
Alley: Tipo de acceso final a la propiedad

       Grvl	Grava
       Pave	Pavimentado
       NA 	Sin acceso
		
LotShape: Forma genérica de la propiedad

       Reg	Regular	
       IR1	Ligeramente irregular
       IR2	Moderadamente irregular
       IR3	Irregular
       
LandContour: Nivelación de la propiedad

       Lvl	Casi plano.
       Bnk	Escalón - Subida rápida y significativa desde la calle al edificio
       HLS	Colina - Inclinación significativa de lado a lado
       Low	Depresión
		
Utilities: Servicios públicios disponibles
		
       AllPub	Todos (electricidad, gas, agua y alcantarillado)	
       NoSewr	Electricidad, gas y agua (fosa séptica)
       NoSeWa	Sólo electricidad y gas
       ELO	Solamente electricidad
	
LotConfig: Configuración de la parcela

       Inside	Parcela interior
       Corner	Esquina
       CulDSac	Cul-de-sac, calle sin salida
       FR2	Frontal exterior por dos lados de la propiedad
       FR3	Frontal exterior por tres lados de la propiedad
	
LandSlope: Inclinación de la propiedad
		
       Gtl	Ligera
       Mod	Moderada
       Sev	Severa
	
Neighborhood: Ubicación de la propiedad, entre distintos vecindarios.

       Blmngtn	Bloomington Heights
       Blueste	Bluestem
       BrDale	Briardale
       BrkSide	Brookside
       ClearCr	Clear Creek
       CollgCr	College Creek
       Crawfor	Crawford
       Edwards	Edwards
       Gilbert	Gilbert
       IDOTRR	Iowa DOT and Rail Road
       MeadowV	Meadow Village
       Mitchel	Mitchell
       Names	North Ames
       NoRidge	Northridge
       NPkVill	Northpark Villa
       NridgHt	Northridge Heights
       NWAmes	Northwest Ames
       OldTown	Old Town
       SWISU	South & West of Iowa State University
       Sawyer	Sawyer
       SawyerW	Sawyer West
       Somerst	Somerset
       StoneBr	Stone Brook
       Timber	Timberland
       Veenker	Veenker
			
Condition1: Proximidad a comunicaciones e infrastructuras
	
       Artery	Adyacente a calle principal
       Feedr	Adyacente a calle secundaria
       Norm	Normal	
       RRNn	A menos de 200 minutos del ferrocarril North-South
       RRAn	Adyacente al ferrorarril North-South
       PosN	cerca de parques, cinturón verde, etc.
       PosA	Adyacente a otras atracciones urbanas (parques, etc..)
       RRNe	A menos de 200 minutos del ferrocarril East-West
       RRAe	Adyacente al ferrocarril East-West
	
Condition2: Proximidad a comunicaciones e infrastructuras (si se da más de una)
		
       Artery	Adyacente a calle principal
       Feedr	Adyacente a calle secundaria
       Norm	Normal	
       RRNn	A menos de 200 minutos del ferrocarril North-South
       RRAn	Adyacente al ferrorarril North-South
       PosN	cerca de parques, cinturón verde, etc.
       PosA	Adyacente a otras atracciones urbanas (parques, etc..)
       RRNe	A menos de 200 minutos del ferrocarril East-West
       RRAe	Adyacente al ferrocarril East-West
	
BldgType: tipo de vivienda
		
       1Fam	Unifamiliar independiente
       2FmCon	Vivienda convertida en dos viviendas, inicialmente construida como unifamiliar
       Duplx	Dúplex
       TwnhsE	Vivienda adosadada esquina
       TwnhsI	Vivienda adosada ambos lados
	
HouseStyle: Estilo de vivienda
	
       1Story	Una planta
       1.5Fin	Planta y media: Segundo nivel terminado
       1.5Unf	Planta y media: Segundo nivel no terminado
       2Story	Dos plantas
       2.5Fin	Dos plantas y media: último nivel terminado
       2.5Unf	Dos plantas y media: último nivel no terminado
       SFoyer	Casa con dos plantas y sótano.
       SLvl	Vivienda en una planta de una casa.
	
OverallQual: Calidades del material y terminaciones de la casa

       10	Sobresaliente
       9	Excelente
       8	Muy bueno
       7	Bueno
       6	Encima de la media
       5	Medio
       4	Bajo la media
       3	Regular
       2	Malo
       1	Muy malo
	
OverallCond: Calificación del estado de la casa

       10	Sobresaliente
       9	Excelente
       8	Muy bueno
       7	Bueno
       6	Encima de la media
       5	Medio
       4	Bajo la media
       3	Regular
       2	Malo
       1	Muy malo
		
YearBuilt: Fecha inicial de construcción

YearRemodAdd: Fecha de renovación (la de construcción si no ha sido renovada)

RoofStyle: Tipo de tejado

       Flat	Plano
       Gable	Tejado inclinado, 2 lados
       Gambrel	Granero
       Hip	Tejado inclinado, 4 lados
       Mansard	Buhardilla
       Shed	Cobertizo
		
RoofMatl: Material del tejado

       ClyTile	Teja
       CompShg	Grava
       Membran	Membrana
       Metal	Metal
       Roll	Rollo de alquitrán
       Tar&Grv	Grava y alquitrán
       WdShake	Tablones de madera
       WdShngl  Tejas de madera
		
Exterior1st: Material de construcción exterior de la casa

       AsbShng	Asbesto
       AsphShn	Asfalto
       BrkComm	Ladrillo normal
       BrkFace	Ladrillo visto
       CBlock	Bloque de hormigón
       CemntBd	Cemento
       HdBoard	Hard Board
       ImStucc	Imitación estuco
       MetalSd	Metalico
       Other	Otro
       Plywood	Plywood
       PreCast	PreCast	
       Stone	Piedra
       Stucco	Estuco
       VinylSd	Vinilo
       Wd Sdng	Tablones de madera
       WdShing	Madera con forma
	
Exterior2nd: Cobertura exterior de la casa (si otro material del anterior)

       AsbShng	Asbesto
       AsphShn	Asfalto
       BrkComm	Ladrillo normal
       BrkFace	Ladrillo visto
       CBlock	  Bloque de cemento
       CemntBd	Cemento
       HdBoard	Hard Board
       ImStucc	Imitación estuco
       MetalSd	Metalico
       Other	  Otro
       Plywood	Plywood
       PreCast	PreCast	
       Stone	  Piedra
       Stucco 	Estuco
       VinylSd	Vinilo
       Wd Sdng	Tablones de madera
       WdShing	Madera con forma
		
MasVnrType: Tipo de muros interiores

       BrkCmn   Ladrillo común
       BrkFace	Ladrillo visto
       CBlock	  Bloque de cemento
       None	    Ninguno
       Stone	  Piedra
	
MasVnrArea: Área de construcción en pies cuadrados

ExterQual: Calidad del material exterior
		
       Ex	Excelente
       Gd	Bueno
       TA	Normal
       Fa	Regular
       Po	Malo
		
ExterCond: Estado actual del material del exterior
		
       Ex	Excelente
       Gd	Bueno
       TA	Normal
       Fa	Regular
       Po	Malo
		
Foundation: Tipo de cimientos
		
       BrkTil	Ladrillo y azulejo
       CBlock	Piedras, ladrillos, etc..
       PConc	Hormigón
       Slab	Losas
       Stone	Piedra
       Wood	Madera
		
BsmtQual: Altura de los cimientos

       Ex	Excelente (Más de 100 pulgadas)	
       Gd	Bueno (Entre 90-99 pulgadas)
       TA	Normal (80-89 pulgadas)
       Fa	Regular (70-79 pulgadas)
       Po	Pobre (menos de 70 pulgadas)
       NA 	Sin cimientos
		
BsmtCond: Estado general de los cimientos

       Ex	Excelente
       Gd	Bueno
       TA	Normal - Ligeras humedades permitidas
       Fa	Regular - Humedades, pequeñas roturas o asentamientos
       Po	Malo - Asentamientos, roturas o humedades graves
       NA	Sin cimientos
	
BsmtExposure: Estado de la salida o límites del jardin

       Gd	Buena
       Av	Media
       Mn	Mínimo
       No	Sin señalización del límite en la propiedad 
       NA	Sin especificar
	
BsmtFinType1: Clasificación de habitabilidad del sótano

       GLQ	Buenas habitaciones de vivienda
       ALQ	Habitaciones normales
       BLQ	Habitabilidad inferior al resto de la vivienda
       Rec	Habitabilidad media como trastero
       LwQ	Baja calidad
       Unf	No terminado
       NA	Sin sótano
		
BsmtFinSF1: Tamaño del área sótano en pies cuadrados terminados

BsmtFinType2: Clasificación de habitabilidad del sótano (si varios tipos)

       GLQ	Buenas habitaciones de vivienda
       ALQ	Habitaciones normales
       BLQ	Habitabilidad inferior al resto de la vivienda
       Rec	Habitabilidad media como trastero
       LwQ	Baja calidad
       Unf	No terminado
       NA	Sin sótano

BsmtFinSF2: Tamaño de la segundo área sótano en pies cuadrados terminados

BsmtUnfSF: Tamaño del área del sótano no terminada

TotalBsmtSF: Tamaño total del sótano

Heating: Tipo de calefacción
		
       Floor	Suelo radiante
       GasA	Calefacción por aire, usando gas
       GasW	Calefacción y agua caliente con gas
       Grav	Horno de gravedad (caldera de aire)
       OthW	Agua caliente o vapor no usando gas
       Wall	Muro calefactor
		
HeatingQC: Calidad y estado de la calefacción

       Ex	Excelente
       Gd	Bueno
       TA	Normal
       Fa	Regular
       Po	Malo
		
CentralAir: Aire acondicionado

       N	No
       Y	Sí
		
Electrical: Instalación eléctrica

       SBrkr	Circuito estándar
       FuseA	Caja de fusibles de más de 60 amperios (Normal)	
       FuseF	Caja de fusibles de 60 amperios o casi (regular)	
       FuseP	Caja de fusibles de menos de 60, (pobre)
       Mix	  Mixto
		
1stFlrSF: Tamaño primera planta
 
2ndFlrSF: Tamaño segunda planta

LowQualFinSF: Área de baja calidad, en todas las plantas

GrLivArea: Tamaño del salón, pies cuadrados

BsmtFullBath: Baños en el sótano

BsmtHalfBath: Aseos en el sótano

FullBath: Baños sobre planta baja

HalfBath: Aseos encima de planta baja

Bedroom: Dormitorios encima de planta baja o sótano

Kitchen: Cocinas sobre planta baja

KitchenQual: Calidad cocina

       Ex	Excelente
       Gd	Buena
       TA	Normal
       Fa	Regular
       Po	Mala
       	
TotRmsAbvGrd: Número de habitaciones encima del sótano (no incluye baños)

Functional: Funcionalidad

       Typ	Normal
       Min1	Deducciones mínimas 1
       Min2	Deducciones mínimas 2
       Mod	Deducciones moderadas
       Maj1	Deducciones mayores 1
       Maj2	Deducciones mayores 2
       Sev	Daños severos
       Sal	Sólo reconstrucción
		
Fireplaces: Número de chimeneas, estufas, hogares, etc...

FireplaceQu: Calidad de la hogar (chimenea)

       Ex	Excelente - Excepcional, en ladrillo.
       Gd	Bueno - En ladrillo, en la planta principal
       TA	Medio - Prefabricado o de ladrillo en el sótano
       Fa	Regular - Prefabricado en el sótano
       Po	Malo - Horno Ben Franklin (metálico)
       NA	Sin hogar para fuego.
		
GarageType: Ubicación del garaje
		
       2Types	Más de un tipo de garaje
       Attchd	Adosado a la casa
       Basment	Garaje de sótano
       BuiltIn	Empotrado (garaje parte de la casa, normalmente con una habitación arriba)
       CarPort	Tejadillo para coche
       Detchd	Separado de la casa
       NA	Sin garaje
		
GarageYrBlt: Año de construcción del garaje
		
GarageFinish: Terminación interior del garaje

       Fin	Terminado
       RFn	Casi terminado
       Unf	No terminado
       NA	Sin garaje
		
GarageCars: Tamaño del garaje en capacidad de coches

GarageArea: Tamaño del garaje en pies cuadrados

GarageQual: Calidad del garaje

       Ex	Excelente
       Gd	Bueno
       TA	Normal
       Fa	Regular
       Po	Malo
       NA	Sin garaje
		
GarageCond: Estado del garaje

       Ex	Excelente
       Gd	Bueno
       TA	Normal
       Fa	Regular
       Po	Malo
       NA	Sin garaje
		
PavedDrive: Entrada de vehículos pavimentada

       Y	Pavimentada
       P	Parcialmente pavimentada
       N	Nada, gravilla
		
WoodDeckSF: Área de terraza de madera en pies cuadrados

OpenPorchSF: Área del porche descubierto en pies cuadrados

EnclosedPorch: Área del porche cubierto en pies cuadrados

3SsnPorch: Tamaño de la veranda de obra en pies cuadrado

ScreenPorch: Área de veranda ligera en pies cuadrados

PoolArea: Tamaño de la piscina, pies cuadrados

PoolQC: Calidad de la piscina
		
       Ex	Excelente
       Gd	Buena
       TA	Normal
       Fa	Regular
       NA	Sin piscina
		
Fence: Calidad de la valla
		
       GdPrv	Buena privacidad
       MnPrv	Privacidad mínima
       GdWo 	Buena madera
       MnWw 	Mínima madera/alambrada
       NA	    Sin valla
	
MiscFeature: Otras características
		
       Elev	Ascensor
       Gar2	Segundo garaje (si no incluido en la sección garaje)
       Othr	Otro
       Shed	Cobertizo (más de 100 pies cuadrados)
       TenC	Pista de tenis
       NA	  Nada
		
MiscVal: Coste de otras características 

MoSold: Mes de venta (MM)

YrSold: Año de venta (YYYY)

SaleType: Condición de venta
		
       WD 	  Escritura convencional
       CWD	  Escritura de garantía, efectivo
       VWD	  Estritura con hipoteca
       New	  Casa recién construida y vendida
       COD	  Court Officer Deed/Estate
       Con	  Contrato con 15% de depósito normal
       ConLw	Contrato con bajo depósito y bajos intereses
       ConLI	Contrato bajo interés
       ConLD	Contrato bajo depósito inicial
       Oth	  Otro
		
SaleCondition: Tipo de venta

       Normal	  Normal
       Abnorml	Anormal - embargo, subasta, etc...
       AdjLand	Compra del solar de la vivienda
       Alloca	  Asignación: dos propiedades vinculadas con escrituras separadas, por ejemplo condominio con una unidad de garaje	
       Family	  Venta entre familiares
       Partial	Vivienda no terminada en momento de venta (normalmente para casas nuevas)

### 2. Integración y selección de los datos de interés a analizar.

Los datos proceden de la web de *kaggle*, de donde se descargan en formato CSV. Cada registro tiene un identificador de inmueble, y el resto de los datos de la vivienda.

El objetivo es el poder predecir el precio de una vivienda a partir de esos datos, por ello se comprobarán cuáles de los datos influyen más en el precio de una vivienda, si es la ubicación, el tamaño, el estado de la vivienda, etc...

### 3. Limpieza de los datos.

Los datos provistos parecen bastante completos, si bien en muchos de los datos cuantitativos está el indicador *NA* que indican datos no disponibles, y que habrá que tratar adecuadamente.

#### 3.1. ¿Los datos contienen ceros o elementos vacíos? ¿Cómo gestionarías cada uno de estos casos?

En el caso de ciertos datos ausentes se han aproximado según los k vecinos más cercanos y se ha realizado una selección de datos más significativos, su completitud también ha sido un factor para tenerlos presentes.

#### 3.2. Identificación y tratamiento de valores extremos.

Se han comprobado valor outliers y se han mostrado distintos boxplots para analizar la dispersión de los datos.

### 4. Análisis de los datos.

En el documento de la práctica adjunto se han implementado distintos análisis y se han realizado algunos modelos lineales para aproximar los precios según distintas características de las viviendas.

### 5. Representación de los resultados a partir de tablas y gráficas.

En el documento de la práctica adjunto se han implementado distintas gráficas relativas a los datos analizados.

### 6. Resolución del problema. A partir de los resultados obtenidos, ¿cuáles son las conclusiones? ¿Los resultados permiten responder al problema?

El análisis de los datos de venta de viviendas nos ha permitido identificar los factores más influyentes en el precio, así como analizar por zonas y por equipamiento de los inmuebles.

Los distintos modelos probados nos han dado una aproximación a la tasación de viviendas, siendo útiles tanto para vendedores, que conocen cuáles son los precios medios demandados según la ubicación y características de la vivienda, como para compradores, para optimizar sus búsquedas según deseos y poder adquisitivo.

Los datos han permitido implementar unos modelos lineales básicos para ello, además de permitirnos visualizar la evolución de precios.

Se confirman hipótesis iniciales del mundo inmobiliario, como es la importancia determinante de la localización, vencindarios y proximidad a infraestructuras, por encima de otras consideraciones como materiales de construcción y, en algunos casos, hasta el estado de la vivienda. 




### 7. Código: Hay que adjuntar el código, preferiblemente en R, con el que se ha realizado la limpieza, análisis y representación de los datos. 

La práctica ha sido implementada en código R, empleado la herramienta RStudio, formateando los resultados finales con *rmarkdown*. 

El codigo, fichero rmd, Practica1_topología_jperezsanchez.Rmd,  se encuentra en el repositorio github de la practica. Con él se ha generado el documento pdf principal entregable de la práctica.

Se han empleado las librerías R: RCurl, VIM, nortest, magrittr y dplyr.

Algunos scripts más largos se han mutado en el documento generado con la opción ECHO = FALSE, pero es consultable en el fichero Rmd. Éste ha sido codificado en utf-8.

El script al ejecutarse descarga los datos directamente del fichero csv de github, para cambiar a lectura local hay que descomentar la línea:

 -- inmuebles <- read.csv("Datos-Inmuebles.csv")

y comentar las líneas:

 downF <- getURL("https://raw.githubusercontent.com/jperezsanchezU/house-prices-advanced-regression-techniques/master/csv/Datos-Inmuebles.csv")
 inmuebles <- read.csv(text = downF)



## Recursos

Los siguientes recursos son de utilidad para la realización de la práctica:

● Megan Squire (2015). Clean Data. Packt Publishing Ltd.

● Jiawei Han, Micheine Kamber, Jian Pei (2012). Data mining: concepts and techniques. Morgan Kaufmann.

● Jason W. Osborne (2010). Data Cleaning Basics: Best Practices in Dealing with Extreme Scores. Newborn and Infant Nursing Reviews; 10 (1): pp. 1527-3369 .

● Peter Dalgaard (2008). Introductory statistics with R. Springer Science &Business Media.

● Wes McKinney (2012). Python for Data Analysis. O’Reilley Media, Inc.

● Tutorial de Github https://guides.github.com/activities/hello-world.

● Dataset de Precios de Casas en *kaggle* [House Prices: Advanced Regression Techniques](https://www.kaggle.com/c/house-prices-advanced-regression-techniques)


