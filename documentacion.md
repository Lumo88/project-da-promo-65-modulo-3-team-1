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

 # Pasos realizados  
- Candidatas a eliminar: **EmployeeCount**, **Over18** | Tienen un unico dato |   HECHO
- Modificar los datos para hacerlos mas legibles |
- Revisar el tipo de dato: **Age** float | **JobSatisfaction** float | **MonthlyIncome** float |  **StandardHours** float |      **TrainingTimesLastYear** float | **YearsWithCurrManager** float | (datos que tienen nulos y por eso son float)
- **DailyRate**	**HourlyRate** **MonthlyRate** cargarnos esas columnas | Los datos no estan actualizados | HECHO
- **MaritalStatus** error en un valor "Marreid"  HECHO
- **StandardHours** borramos columna porque no nos da ninguna información.
- **EmployeeNumber** borramos porque no aporta ahora mucho.
- Borramos columna YearsWithCurrManager original y la creada de la media y quedarnos con la de la mediana en su lugar para el análisis.
- Borramos columna Age inicial por la de creada con la del Knn, cambiandole el nombre de nuevo por la de Age.
- Filtramos los datos cuyas personas tienen coherencia entre la edad, los años trabajados y años en la empresa ya que habia datos erróneos.


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

# Variables analizadas
 1. attrition - monthly
 2. over_time - attrition
 3. distance_from_home - attrition
 4. department - attrition
 5. job_level - attrition
 6. job_level - department
 7. job_rol - attrition
 8. job_level - job_satisfaction
 9. work_life_balance & environment_satisfaction
 10. years_with_curren_manager & job_satisfaction
 11. monthly_income con todas una tabla de correlación
 12. years_at_company & percent_salari_hike, attrition
 13. perfomance_rating & percent_salari_hike
 14. attrition, years_since_last_promotion, percent_salari_hike
 15. attrition, years_since_last_promotion
 16. age - total_working_years
 17. age -  years_at_company
 18. age - years_in_current_role
 19. 



# Insights vistos

- Existe una brecha salarial entre los empleados que se quedan y los que se van, los que se quedan, el salario minimo que perciben es la mediana del salario de los que se van. Los que se van son los que perciben menos salario anual (monthly_income). Los que se quedan, perciben más. 
    (Gráfico sns.boxplot(data=df_hr,x="attrition", y="monthly_income");)
    Los que permanecen tienen salarios variados y los que se marchan, tienen salarios concentrados bajos.

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
- La mayoría de empleados, independientemente de su satisfacción con el entorno, reporta un balance vida-trabajo nivel 3 (medio-alto).
    Esto sugiere que el work-life balance es relativamente estable y no depende tanto del entorno.

- Se observa una leve tendencia descendente en la satisfacción laboral conforme aumentan los años con el mismo supervisor, a los 5 años cae la satisfacción y vuelve a caer a los 10 años, aunque la relación no es fuerte y presenta alta variabilidad.
Estabilidad Inicial (Años 0 a 4): Los empleados suelen estar bastante satisfechos. La mediana es 3 y la mayoría se mueve entre 2 y 4. Es la etapa de "luna de miel" con el manager.
La crisis de los 5 años: ¡Ojo aquí! Hay un desplome masivo en la satisfacción. La mediana cae a 1.0. Esto sugiere que algo pasa cuando alguien lleva exactamente 5 años con el mismo jefe. ¿Falta de promoción? ¿Estancamiento? ¿Fatiga en la relación?
Recuperación y Ciclos: Curiosamente, en los años 6, 7, 8 y 9 la satisfacción vuelve a subir. Los que sobreviven al año 5 parecen recuperar el entusiasmo, hasta que llegamos al año 10 y 14, donde vemos nuevas caídas importantes.
Valores Erráticos al final (Año 15+): Verás que las cajas se vuelven raras (como en el año 16 que es solo una línea en el 1). Esto suele pasar porque hay muy pocos datos. Probablemente solo tengas una o dos personas que lleven 16 años con el mismo manager, por lo que el gráfico no puede formar una "caja" real.

- Al ver los años en la empresa junto con el porcentaje salarial,vemos que dentro de los 10 años de permanencia en la empresa,es donde mayor fuga de talento hay, y que, una subida de salario no condiciona la permanecia, que existen otros factores.

- grafico jointplot de years_at_company_
    
Este gráfico es mucho más revelador para entender el comportamiento de los empleados:

    El "Epicentro" de las Renuncias (Azul): Mira la mancha azul oscura. Está concentrada entre los 0 y 5 años de antigüedad y con un aumento de sueldo bajo (entre 11% y 15%). Es el "Triángulo de las Bermudas" de la empresa: si un empleado cae ahí, es muy probable que se vaya.

    La Estabilidad (Naranja): La mancha naranja es mucho más grande y se extiende hacia la derecha. Esto confirma que los que se quedan (no) tienen una distribución de años mucho más amplia. Hay una "cima" naranja muy clara cerca de los 3-5 años, pero se mantiene sólida a lo largo del tiempo.

    Aislamiento de Variables (Gráficos laterales):

        Arriba: Mira las "montañitas" de antigüedad. La azul (renuncias) cae en picado después de los 10 años. Casi nadie se va después de esa meta.

        Derecha: Mira las curvas de aumento de sueldo. Son casi idénticas en forma. Esto confirma nuestra sospecha inicial: el porcentaje de aumento no es lo que diferencia a los que se van de los que se quedan. ¡El factor clave es el tiempo en la empresa!

- La rotación de personal está ocurriendo en el grupo de "Desempeño Medio" (Rating 3), especialmente entre aquellos que reciben los aumentos más bajos (11% y 13%), cuyo años de la empresa son de 0 a 8 años.

-- grafico de barras entre aumento, attrition, y

Si miramos el gráfico, vemos que la empresa está usando dos estrategias distintas para retener a la gente que lleva 4 años sin ascenso:

    La estrategia del "Billetazo" (Aumento del 25%): * El gráfico muestra que en el grupo no (los que se quedan), hay barras muy altas con aumentos del 22-25%.
        Conclusión: El dinero funciona como un "anestésico". Puedes retener a alguien estancado si le pagas muy por encima de la media. Es efectivo, pero caro para la empresa.

    La estrategia de la "Promoción" (Cambio de puesto):
        Si miras el grupo yes (los que se van), muchos tienen aumentos bajos (11-15%) y llevan más de 3 años sin ascenso.
        Conclusión: Si no tienes presupuesto para un aumento del 25%, promoverlos es la opción más lógica. Al moverlos de puesto, sus "años desde la última promoción" volverían a 0, y como vimos en los gráficos de densidad, la gente recién movida o nueva tiende a quedarse más tiempo mientras aprende su nuevo rol.

    Veredicto de la Profe: Si quieres retención a largo plazo y salud financiera, promoverlos es mejor. Si el empleado es un "crack" que no quieres que se lleve la competencia mañana mismo y no tienes una vacante arriba, el aumento del 25% es tu única salida de emergencia.

-- boxplot de years_since_last_promotion, attrition