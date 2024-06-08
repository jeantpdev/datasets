# Limpieza de datos

Data: "dataset_banco.csv"

## 1. El problema del negocio

Una entidad bancaria contrata a una empresa de marketing encargada de contactar telefónicamente a posibles clientes para determinar si están interesados o no en adquirir un certificado de depósito a término con el banco.

¿Qué perfil tienen los clientes con mayor potencial de conversión?

## Información de la data

La data cuenta con un total de **45215 filas** y **17 columnas** de la cual se obtiene la siguiente información:


1. **"age"**:  edad (numérica)
2. **"job"**: tipo de trabajo (categórica: "admin.", "unknown", "unemployed", "management", "housemaid", "entrepreneur", "student", "blue-collar","self-employed", "retired", "technician", "services") 
3. **"marital"**: estado civil (categórica: "married", "divorced", "single")
4. **"education"**: nivel educativo (categórica: "unknown", "secondary", "primary", "tertiary")
5. **"default"**: si dejó de pagar sus obligaciones (categórica: "yes", "no")
6. **"balance"**: saldo promedio anual en euros (numérica)
7. **"housing"**: ¿tiene o no crédito hipotecario? (categórica: "yes", "no")
8. **"loan"**: ¿tiene créditos de consumo? (categórica: "yes", "no")
9. **"contact"**: medio a través del cual fue contactado (categórica: "unknown", "telephone", "cellular") 
10. **"day"**: último día del mes en el que fue contactada (numérica)
11. **"month"**: último mes en el que fue contactada (categórica: "jan", "feb", "mar", ..., "nov", "dec")
12. **"duration"**: duración (en segundos) del último contacto (numérica)
13. **"campaign"**: número total de veces que fue contactada durante la campaña (numérica)
14. **"pdays"**: número de días transcurridos después de haber sido contactado antes de la campaña actual (numérica. -1 indica que no fue contactado previamente)
15. **"previous"**: número de veces que ha sido contactada antes de esta campaña (numérica)
16. **"poutcome"**: resultado de la campaña de marketing anterior (categórica: "unknown", "other", "failure", "success")
17. **"y"**: categoría ¿el cliente se suscribió a un depósito a término? (categórica: "yes", "no")

## Etapas para la limpieza de datos

1. Datos faltantes en algunas celdas
2. Columnas irrelevantes (que no responden al problema que queremos resolver)
3. Registros (filas) repetidos
4. Valores extremos (*outliers*) en el caso de las variables numéricas. Se deben analizar en detalle pues no necesariamente la solución es eliminarlos
5. Errores tipográficos en el caso de las variables categóricas

### Etapa 1 - Datos Faltantes:

Las siguientes columnas contienen datos faltantes:

**job** = 2
**marital** = 1
**education** = 1
**balance** = 2
**duration** = 1
**pdays** = 1

Contiene pocos datos faltantes por lo que se podrían eliminar.

### Etapa 2 - Columnas Irrelevantes:

**Columnas categóricas**: Todas contienen mas de un subnivel

**Columnas numéricas**: Todas las columnas numéricas tienen desviaciones estándar ("std") diferentes de cero, lo que indica que no tienen un único valor.

### Etapa 3 - Filas repetidas:

El dataset hasta ahora tiene 45207 filas, luego de eliminar las repetidas, se tiene 45203 filas.

### Etapa 4 - Valores grandes:

#### Columna "age"

Contiene valores por encima de los 100 años

**Acción:** Se elimina los mayores a 100 años

#### Columna "balance"

Contiene un valor mayor a 500.000
**Acción:** Se mantiene el valor.


#### Columna "day"

Los valores se mantienen entre 1 y 31 
**Acción:** Se mantiene

#### Columna "duration"

Contiene valores negativos
**Acción:** Se eliminan los valores negativos

#### Columna "campaign"

Contiene valores por encima de 50
**Acción:** Se mantiene

#### Columna "pdays"

Contiene valores por encima de 800
**Acción:** Se mantiene

#### Columna "previous"

Contiene un valor por encima de 250
**Acción:** Se elimina

#### Resumen - Eliminación de valores grandes:

**age**: Se elimina los mayores a 100 años
**duration**: Se elimian los valores negativos
**previous**: Se seliminan valores por encima de 250

Antes de eliminar las columnas con datos grandes: 45203
Despues de eliminar las columnas con datos grandes: 45195

## Etapa 5 - Eliminación de errores tipográficos

#### Columna "job"

management - Management - MANAGEMENT
technician
entrepreneur
blue-collar
unknown
retired - Retired
administrative -admin.
services - Services
self-employed - Self-employed
unemployed
housemaid
student

#### Columna "marital"

married
single - Single
divorced - div. - DIVORCED

#### Columna "education"

tertiary - Tertiary
secondary - SECONDARY - Secondary - sec.
unknown - UNK
primary - Primary

#### Columna "loan"

no - No - NO
yes - YES - Yes

#### Columna "contact"

unknown
cellular
telephone
phone
mobile

#### Columna "poutcome"

unknown - UNK
failure
other
success - Success

Se tienen subniveles que se pueden unir y pertenecer a un solo subnivel ya que estan escritos con el mismo nombre, pero en minuscula o mayuscula, o con la primera letra en mayúscula.

1. Se transforman a minúscula.
2. Se reemplaza el resto.

**Se tiene un total de 45189 filas** 