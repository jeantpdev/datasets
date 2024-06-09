# Limpieza de datos

Data: "Salary_Data.csv"

# 1. Problema del negocio

NO HAY INFORMACIÓN AÚN

## Información de la data

La data cuenta con **6704 filas** y **6 columnas** con la siguiente información:

1. **"Age"**:  edad (numérica)
2. **"Gender"**: Género (categórica)
3. **"Education Level"**:  Nivel de educación (categórica)
4. **"Job Title"**: Nombre del trabajo (categórica)
5. **"Years of Experiencie"**:  años de experiencia (numérica)
6. **"Salary"**: salario (numérica)

## Etapas para la limpieza de datos

1. Datos faltantes en algunas celdas
2. Columnas irrelevantes (que no responden al problema que queremos resolver)
3. Registros (filas) repetidos
4. Valores extremos (*outliers*) en el caso de las variables numéricas. Se deben analizar en detalle pues no necesariamente la solución es eliminarlos
5. Errores tipográficos en el caso de las variables categóricas

### Etapa 1 - Datos Faltantes:

**Age** =                     2
**Gender** =                2
**Education Level** =        3
**Job Title** =             2
**Years of Experience** =    3
**Salary** =                 5

Contiene pocos datos faltantes por lo que se podrían eliminar.

# Etapa 2 - Revisión de columnas

En esta etapa no se eliminará alguna columna, pero, se le cambiará su nombre para evitar tener sus nombres con espacio de por medio.

### Renombramiento de columnas

Se renombran las siguientes columnas: 
1. **Education Level** a **Education_Level**
2. **Job Title** a **Job_Title**
3. **Years of Experiencie** a **Years_of_experience**

### Transformación de datos a minúscula

Las siguientes columnas se transformaron sus valores a minúscula
**Gender, Education_Level, Job_Title**

### Revisión de columnas categóricas y numéricas

**Columnas categóricas**: Todas contienen mas de un subnivel

**Columnas numéricas**: Todas las columnas numéricas tienen desviaciones estándar ("std") diferentes de cero, lo que indica que no tienen un único valor.

### Reducción de nombres en las columnas

#### Columna Education_Level

La columna de Education_Level contiene valores con el mimso nombre pero extensos, por lo cuál, se unirán esos valores a uno solo independientemente

#### Columna Job_Title

Contiene demasiados valores que tienen muchas cosas en común, pero escritas de otras maneras, se pueden unir y clasificar de una manera mas general:

1. Manager
2. Engineer 
3. Developer
4. Scientist
5. Analyst
6. Other
7. Director
8. Coordinator  
9. Associate






