# Diccionario de Datos - HR Dataset

Este documento describe las columnas contenidas en el archivo `hr.csv`, utilizado para el análisis de recursos humanos y predicción de rotación de personal (attrition).

 # Sobre la Empresa
| ABC Corporation, fundada en 1980 en California, es una consultora tecnológica especializada en ofrecer soluciones de inteligencia artificial (IA) y aprendizaje automático (machine learning) a empresas de diversos sectores. Su enfoque principal radica en automatizar y optimizar procesos empresariales mediante tecnologías de vanguardia.

La empresa se distingue por tener un equipo multidisciplinario que abarca expertos en UX/UI, marketing, analistas, científicos de datos y otros campos relevantes. Esta diversidad permite una sinergia única entre conocimientos técnicos especializados y perspectivas variadas, lo que les permite ofrecer soluciones personalizadas adaptadas a las necesidades individuales de cada cliente. |

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

 # Proximos pasos 
 | Candidatas a eliminar: **EmployeeCount**, **Over18** | Tienen un unico dato |   HECHO
 | Modificar los datos para hacerlos mas legibles |
 | Revisar el tipo de dato: **Age** float | **JobSatisfaction** float | **MonthlyIncome** float |  **StandardHours** float |      **TrainingTimesLastYear** float | **YearsWithCurrManager** float | (datos que tienen nulos y por eso son float)
 |**DailyRate**	**HourlyRate** **MonthlyRate** cargarnos esas columnas | Los datos no estan actualizados | HECHO
 |**MaritalStatus** error en un valor "Marreid"  HECHO
 |**StandardHours** borramos columna porque no nos da ninguna información.


 # COLUMNAS CON NULOS A REVISAR
 | Columna | % Nulos |
| :--- | :--- |
|  Age                         | 5.0 | 🆗
|  BusinessTravel              | 8.0 | 🆗
|  Department                  | 2.0 | 🆗
|  EducationField              | 4.0 | 🆗
|  JobSatisfaction             | 2.0 | 🆗
|  MaritalStatus               | 9.0 | 🆗
|  MonthlyIncome               | 1.0 | 🆗
|  OverTime                    | 3.0 | 🆗
|  YearsWithCurrManager        | 10.0| 🆗
| TrainingTimesLastYear        | 6.0 | 🆗

| Columna | Nº Nulos |
| :--- | :--- |
| Age                         |  73 | 
| BusinessTravel              | 117 | 
| Department                  | 29  | 
| EducationField              | 58  | 
| JobSatisfaction             | 29  | 
| MaritalStatus               | 132 | 
| MonthlyIncome               | 14  | 
| OverTime                    | 44  | 
| TrainingTimesLastYear       | 88  | 
| YearsWithCurrManager        | 148 | 


# GESTIÓN NULOS REALIZADOS
- YearsWithCurrManager -> Lo hemos rellenado con la Mediana ya que nos daba los años enteros y respeta los valores estadísticos iniciales.
- MaritalStatus --> Tenemos casi un 9%, la moda es Casado pero tiene la diferencia igual con Single, después de sacar gráficas, no hay patrones claros, lo categorizamos como "desconocidos"
- BusinessTravel --> Con un bloxpot, vemos que los valores nulos tienen un patrón más parecido a los que viajan respecto con el salario, siendo los que viajan, salarios altos.
                    Hemos visto que no afecta el balance trabajo-vida por tener datos muy dispersos, no hay patron.
                    Ya que hemos profundizado, nos informa el cliente que los nulos son los que no viajan.

- EducationField --> Tras varios análisis, el porcentaje es muy bajo, no hay patrones y no influye en nuestra meta sobre la rotación, lo metemos en Others.
- TrainingTimesLastYear --> Tras analizarlo, no tenemos confirmación del cliente, interpretamos que los nulos son los valores de las personas que no ha tenido ningún tipo de formación, el sistema ha puesto nulo al no haberse hecho ningún curso.

- Age - Hemos realizado un knnImputer con el saladio y los años de la empresa para sustituir los nulos.
- OverTime -> Los nulos los interpretamos como si no hubieran hecho horas extras.
- Department -> Los nulos los ponemos como desconocidos.
- JobSatisfaction --> Rellenamos con knnimputer usando las otras dos de satisfacción (RelationshipSatisfaction, EnvironmentSatisfaction)
- MonthlyIncome --> Rellenamos con knnimputer usando JobLevel, Education.


# GESTIONES REALIZADAS
- Borramos columna YearsWithCurrManager original y la creada de la media y quedarnos con la de la mediana en su lugar para el análisis.
- Borramos columna Age inicial por la de creada con la del Knn, cambiandole el nombre de nuevo por la de Age.

# Cambios tipo de variables:

TrainingTimesLastYear, Age,  JobSatisfaction -> está como float y lo cambiamos a int.

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
| **EmployeeNumber** | Identificador único para cada empleado. |
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


## Preguntas Objetivo:

- ¿Quién se va de la empresa?
- ¿Porqué se van de la empresa?
- ¿Qué características (patrones)tienen los que se van?

# Preguntas a contestar:

- ¿Quiénes se van más? -> Ver en que departamentos o roles se concentran más salidas
- ¿Las horas extras influyen en la rotación?
- ¿Los empleados con menor environment_satisfaction se van más?
- ¿Qué áreas tienen menor satisfacción?


1. Análisis de Rotación (Attrition)
  El objetivo es entender por qué la gente se va (attrition == 'yes').

   * ¿Existe una brecha salarial entre los empleados que se quedan y los que se van?
       * Herramienta: sns.boxplot(x='attrition', y='monthly_income', data=df)
   * ¿El trabajo extra (Overtime) es un detonante para la rotación?
       * Herramienta: sns.countplot(x='over_time', hue='attrition', data=df)
   * ¿Influye la distancia al hogar en la decisión de abandonar la empresa?
       * Herramienta: sns.kdeplot comparando distance_from_home para ambos grupos de attrition.
   * ¿Qué departamentos o roles tienen la tasa de rotación más alta?
       * Herramienta: Gráfico de barras apiladas o sns.countplot con job_role o department.

  2. Análisis de Satisfacción y Clima
  Se centra en las métricas de bienestar (job_satisfaction, environment_satisfaction, work_life_balance).

   * ¿Cómo se distribuye la satisfacción laboral según el nivel del puesto (job_level)?
       * Herramienta: sns.violinplot(x='job_level', y='job_satisfaction', data=df)
   * ¿Existe relación entre el equilibrio vida-trabajo y la satisfacción en el entorno?
       * Herramienta: Matriz de contingencia (Heatmap) entre work_life_balance y environment_satisfaction.
   * ¿Los empleados con más años bajo el mismo manager tienen mayor satisfacción?
       * Herramienta: sns.lineplot o sns.barplot comparando years_with_curr_manager con job_satisfaction.

  3. Correlaciones y Factores Numéricos
  Para identificar qué variables se mueven juntas.

   * ¿Cuáles son las variables numéricas que más influyen en el ingreso mensual?
       * Herramienta: Mapa de calor de correlaciones (sns.heatmap(df.corr())) filtrando por monthly_income.
   * ¿Existe una correlación entre el porcentaje de aumento salarial (percent_salary_hike) y el desempeño (performance_rating)?
       * Herramienta: sns.scatterplot con regresión.
   * ¿Cómo afecta la edad y los años de experiencia al nivel de ingresos?
       * Herramienta: sns.jointplot para ver la distribución y la relación entre age y total_working_years.

  4. Estabilidad y Crecimiento
   * ¿Cuánto tiempo pasa desde la última promoción antes de que un empleado decida irse?
       * Herramienta: sns.boxenplot(x='attrition', y='years_since_last_promotion', data=df)
   * ¿Los empleados que han trabajado en muchas empresas (num_companies_worked) tienen mayor tendencia a la rotación?
       * Herramienta: Gráfico de barras de la media de attrition por número de empresas.

  Herramientas clave para tu análisis:
   1. Correlaciones: Usa df.corr(numeric_only=True) para identificar relaciones fuertes antes de graficar.
   2. Segmentación: Utiliza el parámetro hue='attrition' en casi todos tus gráficos de Seaborn para ver el contraste inmediato.
   3. Matplotlib: Úsalo para personalizar títulos, etiquetas y el tamaño de los gráficos (plt.figure(figsize=(10,6))).

- YearsAtCompany y YearsInCurrentRole: Es probable que estos dos valores estén relacionados entre sí, ya que ambos indican el tiempo que ha trabajado en la empresa actual.

- JobLevel y JobSatisfaction: Un aumento en el nivel jerárquico (JobLevel) podría estar asociado con una mayor satisfacción laboral (JobSatisfaction).

- PerformanceRating y StockOptionLevel: Una mejor calificación de desempeño (PerformanceRating) podría estar relacionada con un aumento en las opciones sobre acciones otorgadas (StockOptionLevel), ya que se supone que los empleados con mejor desempeño merecen más beneficios.

- DistanceFromHome y WorkLifeBalance: Un mayor tiempo de viaje para negocios o una ubicación lejos del hogar podría afectar negativamente la equilibrio entre vida laboral y personal (WorkLifeBalance).

- MonthlyIncome y YearsAtCompany: A medida que el empleado permanece más tiempo en la empresa, es probable que su ingreso mensual aumente.

- YearsWithCurrManager y PerformanceRating: El tiempo trabajando bajo la supervisión del gerente actual podría estar relacionado con una mayor calificación de desempeño (PerformanceRating), ya que se supone que el gerente ayuda a desarrollar al empleado.

- Education y JobLevel: Un nivel más alto de educación podría estar asociado con un nivel jerárquico más alto en la empresa, ya que las habilidades académicas son importantes para el desempeño profesional.

- OverTime y PerformanceRating: El trabajo de horas extras (OverTime) podría afectar negativamente la calificación de desempeño (PerformanceRating), ya que puede indicar una sobrecarga de trabajo o una falta de equilibrio entre trabajo y vida personal.

- YearsSinceLastPromotion y JobSatisfaction: El tiempo transcurrido desde el último ascenso podría estar relacionado con la satisfacción laboral, ya que un empleado que no ha recibido un ascenso en algún tiempo puede sentirse insatisfecho.

- TrainingTimesLastYear y YearsSinceLastPromotion: El número de capacitaciones realizadas el año pasado podría estar relacionado con el tiempo transcurrido desde el último ascenso, ya que el empleado puede haber estado recibiendo oportunidades de desarrollo profesional para avanzar en su carrera.

# Insights vistos

- Existe una brecha salarial entre los empleados que se quedan y los que se van, los que se quedan, el salario minimo que perciben es la media del salario de los que se van. Los que se van son los que perciben menos salario anual (monthly_income). Los que se quedan, percibeb más. 
    (Gráfico sns.boxplot(data=df_hr,x="attrition", y="monthly_income");)
    Los que permanecen tienen salarios variados y los que se marchan, tienen salarios concentrados bajos.

- Al ver la Edad con los años en la empresa,vamos que a partir de los 10 años de permanencia en la empresa, se empieza a perder talento, a partir de los 35 años.

- Las horas extras no son causa de la rotación de personal. (Gráfico sns.countplot(x='over_time', hue='attrition', data=df_hr)) un 19% de los que se han ido no echan horas extras, mientras que un 8% sí PERO el 80% de los que no se van, no lo echan.

- De los que se han ido sin echar horas extras, cuánto tiempo llevan trabajando o salario, satisfacciones..
        - Media de la gente que se va, de la gente que se queda.

- el 40% de los que se van viven a más de 10 millas.
- el 70% de las personas que se van tienen un salario bajo.
- No hay patrón claro del porcentaje de rotación por departamento, pero podemos indicar que el 53% de los que se van pertenecen a development, un 37% en ventas.
    Ventas (Sales) es el punto crítico:
        En el grupo de los que se quedan (no), representan el 28%.
        En el grupo de los que se van (yes), suben al 37%.
        Conclusión: El departamento de Ventas tiene una rotación proporcionalmente más alta que su peso en la empresa.

    Investigación y Desarrollo (R&D):
        Son la mayoría de la empresa. Representan el 66% de los que se quedan, pero "solo" el 53% de los que se van.
        Conclusión: Es un departamento más estable comparado con Ventas.


- 26% labotatory technician, 20% research scientist, 24% sales executive

Groupby attrition.
Transformar el Yes/No por 1/0, hacer un mapeo.
intervalos distancias 