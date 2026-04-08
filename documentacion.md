# 📊 Informe de Análisis Estratégico (EDA): Retención de Talento en ABC Corporation

## 1. Contexto de la Empresa
**ABC Corporation**, fundada en 1980 en California, es una consultora tecnológica especializada en **Inteligencia Artificial y Machine Learning**. La empresa se basa en un equipo multidisciplinar de expertos (UX/UI, Data Science, Marketing) cuya sinergia es vital para ofrecer soluciones personalizadas.

---

# 2. Diccionario de Datos - HR Dataset

Este documento describe las columnas contenidas en el archivo `hr.csv`, utilizado para el análisis de recursos humanos y predicción de rotación de personal (attrition).


| Columna | Descripción |
| :--- | :--- |
| **Age** | Edad del empleado. |
| **Attrition** | Indica si el empleado dejó la empresa (Yes/No). |
| **BusinessTravel** | Frecuencia de viajes de negocios (Travel_Rarely, Travel_Frequently, Non-Travel). |
| **DailyRate** | Tarifa diaria de pago. |
| **Department** | Departamento al que pertenece el empleado (Sales, Research & Development, Human Resources). |
| **DistanceFromHome** | Distancia entre el hogar y el lugar de trabajo. |
| **Education** | Nivel de educación (1: 'Below College', 2: 'College', 3: 'Bachelor', 4: 'Master', 5: 'Doctor'). |
| **EducationField** | Campo de estudio de su formación académica. |
| **EmployeeCount** | Conteo de empleados (generalmente es un valor constante de 1). |
| **EmployeeNumber** | Identificador único para cada empleado. |
| **EnvironmentSatisfaction** | Nivel de satisfacción con el entorno de trabajo (1: 'Low', 2: 'Medium', 3: 'High', 4: 'Very High'). |
| **Gender** | Género del empleado (Female, Male). |
| **HourlyRate** | Tarifa por hora de pago. |
| **JobInvolvement** | Nivel de involucramiento en el trabajo (1: 'Low', 2: 'Medium', 3: 'High', 4: 'Very High'). |
| **JobLevel** | Nivel jerárquico del puesto (1 a 5). |
| **JobRole** | Título o rol del puesto de trabajo. |
| **JobSatisfaction** | Nivel de satisfacción con el trabajo (1: 'Low', 2: 'Medium', 3: 'High', 4: 'Very High'). |
| **MaritalStatus** | Estado civil (Single, Married, Divorced). |
| **MonthlyIncome** | Ingreso mensual bruto. |
| **MonthlyRate** | Tarifa mensual. |
| **NumCompaniesWorked** | Número de empresas en las que ha trabajado anteriormente. |
| **Over18** | Indica si el empleado es mayor de 18 años (Y). |
| **OverTime** | Indica si el empleado trabaja horas extras (Yes/No). |
| **PercentSalaryHike** | Porcentaje de incremento salarial en el último año. |
| **PerformanceRating** | Calificación de desempeño (1: 'Low', 2: 'Good', 3: 'Excellent', 4: 'Outstanding'). |
| **RelationshipSatisfaction** | Satisfacción en sus relaciones laborales (1: 'Low', 2: 'Medium', 3: 'High', 4: 'Very High'). |
| **StandardHours** | Horas estándar de trabajo. |
| **StockOptionLevel** | Nivel de opciones sobre acciones otorgadas. |
| **TotalWorkingYears** | Total de años de experiencia laboral. |
| **TrainingTimesLastYear** | Número de capacitaciones realizadas el año pasado. |
| **WorkLifeBalance** | Equilibrio entre vida laboral y personal (1: 'Bad', 2: 'Good', 3: 'Better', 4: 'Best'). |
| **YearsAtCompany** | Años que lleva trabajando en la empresa actual. |
| **YearsInCurrentRole** | Años que lleva desempeñando su rol actual. |
| **YearsSinceLastPromotion** | Años transcurridos desde su último ascenso. |
| **YearsWithCurrManager** | Años que lleva trabajando bajo la supervisión del gerente actual. |


## 3. Calidad de Datos y Limpieza (Data Wrangling)

### **A. Acciones de Limpieza Realizadas**
* **Eliminación de Redundancias:** Se borraron las columnas `EmployeeCount`, `Over18` y `StandardHours` por contener un único valor constante y la columna `EmployeeNumber` por ser irrelevante.
* **Optimización Financiera:** Se eliminaron las columnas `DailyRate`, `HourlyRate` y `MonthlyRate`. Se detectó que estos datos **no estaban actualizados** y presentaban **incoherencias** entre ellos y al ingreso mensual (`MonthlyIncome`), por lo que se descartaron para evitar sesgos en el análisis.
* **Correcciones Críticas:** Se arregló el error tipográfico en `MaritalStatus` ("Marreid" → "Married").
* **Filtros de Coherencia:** Se eliminaron registros con errores lógicos (ej. más años en la empresa que años de experiencia total).

### **B. Estrategia Integral de Gestión de Nulos**

Se ha realizado un análisis exhaustivo de cada columna con valores faltantes para aplicar la técnica de imputación más coherente con la realidad del negocio:

| Columna | Técnica de Imputación | Justificación y Hallazgos |
| :--- | :--- | :--- |
| **YearsWithCurrManager** | **Mediana** | Se optó por la mediana para asegurar valores enteros coherentes y respetar la distribución estadística original sin sesgar los datos. |
| **MaritalStatus** | **Categoría "Unknown"** | Con un 9% de nulos y una moda (Married) muy cercana a la siguiente categoría (Single), el análisis gráfico no mostró patrones claros. Se decidió no inventar datos y categorizar como "desconocidos". |
| **BusinessTravel** | **Valor "Non-Travel"** | El análisis con Boxplot sugería una relación con salarios altos (propios de viajeros), pero la dispersión en el balance vida-trabajo no era concluyente. Finalmente, tras consulta directa, el cliente confirmó que los nulos corresponden a empleados que no viajan. |
| **EducationField** | **Categoría "Other"** | Debido a su bajo porcentaje de nulos y la ausencia de patrones de influencia en la rotación (attrition), se agruparon en la categoría de "Others". |
| **TrainingTimesLastYear**| **Valor 0** | Ante la falta de confirmación del cliente, se interpreta técnicamente que el nulo representa la ausencia de cursos realizados durante el último año. |
| **Age** | **KNN Imputer** | Imputación avanzada basada en la correlación entre la edad, el salario (`MonthlyIncome`) y la antigüedad en la empresa. |
| **OverTime** | **Valor "No"** | Se interpretan los nulos como la ausencia de registro de horas extras, asumiendo que el empleado cumple su jornada estándar. |
| **Department** | **Categoría "Unknown"** | Al no haber patrones claros que vinculen estos nulos con roles específicos, se marcan como desconocidos para evitar errores de asignación. |
| **JobSatisfaction** | **KNN Imputer** | Se utilizaron las variables de satisfacción complementarias (`RelationshipSatisfaction` y `EnvironmentSatisfaction`) para predecir el nivel de satisfacción laboral faltante. |
| **MonthlyIncome** | **KNN Imputer** | Imputación de alta precisión utilizando el nivel del puesto (`JobLevel`) y el nivel educativo (`Education`) como predictores principales. |
---


# Columnas definitivas
| Columna | Descripción |
| :--- | :--- |
| **Age** | Edad del empleado. |
| **Attrition** | Indica si el empleado dejó la empresa (Yes/No). |
| **BusinessTravel** | Frecuencia de viajes de negocios (Travel_Rarely, Travel_Frequently, Non-Travel). |
| **Department** | Departamento al que pertenece el empleado (Sales, Research & Development, Human Resources). |
| **DistanceFromHome** | Distancia entre el hogar y el lugar de trabajo. |
| **Education** | Nivel de educación (1: 'Below College', 2: 'College', 3: 'Bachelor', 4: 'Master', 5: 'Doctor'). |
| **EducationField** | Campo de estudio de su formación académica. |
| **EnvironmentSatisfaction** | Nivel de satisfacción con el entorno de trabajo (1: 'Low', 2: 'Medium', 3: 'High', 4: 'Very High'). |
| **Gender** | Género del empleado (Female, Male). |
| **JobInvolvement** | Nivel de involucramiento en el trabajo (1: 'Low', 2: 'Medium', 3: 'High', 4: 'Very High'). |
| **JobLevel** | Nivel jerárquico del puesto (1 a 5). |
| **JobRole** | Título o rol del puesto de trabajo. |
| **JobSatisfaction** | Nivel de satisfacción con el trabajo (1: 'Low', 2: 'Medium', 3: 'High', 4: 'Very High'). |
| **MaritalStatus** | Estado civil (Single, Married, Divorced). |
| **MonthlyIncome** | Ingreso mensual bruto. |
| **NumCompaniesWorked** | Número de empresas en las que ha trabajado anteriormente. |
| **OverTime** | Indica si el empleado trabaja horas extras (Yes/No). |
| **PercentSalaryHike** | Porcentaje de incremento salarial en el último año. |
| **PerformanceRating** | Calificación de desempeño (1: 'Low', 2: 'Good', 3: 'Excellent', 4: 'Outstanding'). |
| **RelationshipSatisfaction** | Satisfacción en sus relaciones laborales (1: 'Low', 2: 'Medium', 3: 'High', 4: 'Very High'). |
| **StockOptionLevel** | Nivel de opciones sobre acciones otorgadas. |
| **TotalWorkingYears** | Total de años de experiencia laboral. |
| **TrainingTimesLastYear** | Número de capacitaciones realizadas el año pasado. |
| **WorkLifeBalance** | Equilibrio entre vida laboral y personal (1: 'Bad', 2: 'Good', 3: 'Better', 4: 'Best'). |
| **YearsAtCompany** | Años que lleva trabajando en la empresa actual. |
| **YearsInCurrentRole** | Años que lleva desempeñando su rol actual. |
| **YearsSinceLastPromotion** | Años transcurridos desde su último ascenso. |
| **YearsWithCurrManager** | Años que lleva trabajando bajo la supervisión del gerente actual. |


## 4. Insights Estratégicos y Hallazgos Clave

### **💰 Salario: El Principal Motor de Fuga**
* **El Umbral Crítico:** El **70% de las renuncias** ocurren en el rango de **salario bajo (0 - 5k)**. 
* **Brecha Salarial:** Existe una clara diferencia; los empleados que permanecen tienen el sueldo mínimo situado en la mediana del sueldo de los que se van. Los que se quedan tienen salarios variados, mientras que los que se van están concentrados en el tramo bajo.

### **🏢 Departamentos en Riesgo**
* **Ventas (Sales) es el punto crítico:** Representa el **37% de las renuncias**, un porcentaje superior a su peso real en la empresa.
* **I+D (Research & Development):** Es el departamento más estable, concentrando la mayoría del personal que permanece.
* **Roles Críticos:** Los puestos con mayor rotación son **Laboratory Technician (26%)**, **Sales Executive (24%)** y **Research Scientist (20%)**.

### **🤝 El Factor Manager y Satisfacción**
* **La Crisis de los 5 Años:** Se observa un desplome drástico de la satisfacción laboral al cumplir 5 años con el mismo supervisor. Existe una tendencia descendente conforme aumenta el tiempo bajo el mismo mando.
* **El Techo de los 10 Años:** El año 10 marca un punto de inflexión de "agotamiento extremo" donde la satisfacción cae a niveles mínimos (1.5).

### **📈 Rendimiento vs. Retención**
* **El Triángulo de las Bermudas:** La rotación se concentra en empleados con **Desempeño Medio (Rating 3)** que reciben aumentos bajos (11-13%) y llevan entre 0 y 8 años en la compañía.
* **Efectividad del Aumento:** Un incremento del **25%** funciona como "anestésico" para retener a empleados estancados, pero la **promoción interna** es la herramienta más saludable a largo plazo para resetear el ciclo de satisfacción.

---

## 5. Conclusiones y Recomendaciones
1. **Acción Inmediata:** Revisar políticas de retención para el rango salarial inferior a 5k.
2. **Intervención de Liderazgo:** Implementar programas de rotación o cambio de manager para empleados que alcancen los 5 y 10 años de antigüedad.
3. **Fomento de Promociones:** Priorizar el cambio de rol frente a pequeños aumentos salariales para evitar el estancamiento en el desempeño nivel 3.