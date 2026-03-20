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
 |**MaritalStatus** error en un valor "Marreid" 