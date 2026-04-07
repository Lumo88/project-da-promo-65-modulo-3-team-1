# Tendencias
- Las horas extras no son causa de la rotación de personal. (Gráfico sns.countplot(x='over_time', hue='attrition', data=df_hr)) un 19% de los que se han ido no echan horas extras, mientras que un 8% sí PERO el 80% de los que no se van, no lo echan.

- Se observa una leve tendencia descendente en la satisfacción laboral conforme aumentan los años con el mismo supervisor, a los 5 años cae la satisfacción y vuelve a caer a los 10 años, aunque la relación no es fuerte y presenta alta variabilidad. Estabilidad Inicial (Años 0 a 4): Los empleados suelen estar bastante satisfechos. La mediana es 3 y la mayoría se mueve entre 2 y 4. Es la etapa de "luna de miel" con el manager. La crisis de los 5 años: ¡Ojo aquí! Hay un desplome masivo en la satisfacción. La mediana cae a 1.0. Esto sugiere que algo pasa cuando alguien lleva exactamente 5 años con el mismo jefe. ¿Falta de promoción? ¿Estancamiento? ¿Fatiga en la relación? Recuperación y Ciclos: Curiosamente, en los años 6, 7, 8 y 9 la satisfacción vuelve a subir. Los que sobreviven al año 5 parecen recuperar el entusiasmo, hasta que llegamos al año 10 y 14, donde vemos nuevas caídas importantes. Valores Erráticos al final (Año 15+): Verás que las cajas se vuelven raras (como en el año 16 que es solo una línea en el 1). Esto suele pasar porque hay muy pocos datos. Probablemente solo tengas una o dos personas que lleven 16 años con el mismo manager, por lo que el gráfico no puede formar una "caja" real.



# Areas de mejora
- No hay patrón claro del porcentaje de rotación por departamento, pero podemos indicar que el 53% de los que se van pertenecen a development, un 37% en ventas. Ventas (Sales) es el punto crítico: En el grupo de los que se quedan (no), representan el 28%. En el grupo de los que se van (yes), suben al 37%. Conclusión: El departamento de Ventas tiene una rotación proporcionalmente más alta que su peso en la empresa.

- Investigación y Desarrollo (R&D): Son la mayoría de la empresa. Representan el 66% de los que se quedan, pero "solo" el 53% de los que se van. Conclusión: Es un departamento más estable comparado con Ventas.

- Al ver los años en la empresa junto con el porcentaje salarial,vemos que dentro de los 10 años de permanencia en la empresa,es donde mayor fuga de talento hay, y que, una subida de salario no condiciona la permanecia, que existen otros factores.





# Fortalezas dentro de la empresa

- La mayoría de empleados, independientemente de su satisfacción con el entorno, reporta un balance vida-trabajo nivel 3 (medio-alto). Esto sugiere que el work-life balance es relativamente estable y no depende tanto del entorno.



# Causas rotación

- Existe una brecha salarial entre los empleados que se quedan y los que se van, los que se quedan, el salario minimo que perciben es la mediana del salario de los que se van. Los que se van son los que perciben menos salario anual (monthly_income). Los que se quedan, perciben más. (Gráfico sns.boxplot(data=df_hr,x="attrition", y="monthly_income");) Los que permanecen tienen salarios variados y los que se marchan, tienen salarios concentrados bajos.

- el 40% de los que se van viven a más de 10 millas.

- el 70% de las personas que se van tienen un salario bajo.

- Al ver los años en la empresa junto con el porcentaje salarial,vemos que dentro de los 10 años de permanencia en la empresa,es donde mayor fuga de talento hay, y que, una subida de salario no condiciona la permanecia, que existen otros factores.

- El "Epicentro" de las Renuncias (Azul): Mira la mancha azul oscura. Está concentrada entre los 0 y 5 años de antigüedad y con un aumento de sueldo bajo (entre 11% y 15%).

- El porcentaje de aumento no es lo que diferencia a los que se van de los que se quedan. ¡El factor clave es el tiempo en la empresa!

# Conclusión:

Si quieres retención a largo plazo y salud financiera, promoverlos es mejor. Si el empleado es un "crack" que no quieres que se lleve la competencia mañana mismo y no tienes una vacante arriba, el aumento del 25% es tu única salida de emergencia.
