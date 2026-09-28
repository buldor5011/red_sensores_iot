# Bitacora individual - Semana [XX]

> Copia este archivo y renombralo como `s[XX]-[tu-nombre].md`.
> Completa todas las secciones con tus propias palabras. Esta bitacora es
> individual, aunque el codigo pueda haberse construido en equipo.

## 1. Datos de la actividad

- **Estudiante:Diego Alejandro Rodriguez Plazas
- **Equipo:** Yo solito
- **Semana:** Semana 3
- **Fecha del laboratorio:** idk
- **Fecha del taller:** lunes, 21 de septiembre de 2026
- **Tema principal:** Motor de consulta puntual
- **Pregunta de la semana:** ¿Cómo podemos encontrar un dato de manera eficiente cuando tenemos una gran cantidad de datos?

## 2. Prediccion antes de ejecutar

Antes de abrir o ejecutar el programa, responde:

1. **Que creo que va a ocurrir?**
   Creo que la búsqueda lineal va a revisar los datos uno por uno hasta encontrar el dato que estamos buscando
2. **Que parte del programa o del algoritmo puede fallar?**
   La búsqueda binaria puede fallar o entregar un resultado incorrecto si los datos no están ordenados
3. **Como comprobare mi prediccion?**
   Voy a probar los dos métodos buscando diferentes valores dentro de conjuntos de datos de distintos tamaños compararé la cantidad de pasos o comparaciones que necesita cada método para encontrar el dato

## 3. Evidencia del laboratorio

### Resultado observado

Durante la ingesta se almacenaron 201 lecturas, se descartaron 2 lecturas por formato y 8 por rango el promedio de PM2.5 almacenado en el repositorio fue de aproximadamente 17,05

También se obtuvo un perfil horario de la ciudad los valores más altos se presentaron principalmente en las horas de la mañana y de la tarde

### Diferencia entre la prediccion y el resultado

La predicción se cumplió principalmente en la comparación entre búsqueda lineal y binaria. La búsqueda binaria necesitó muchas menos comparaciones que la lineal cuando se buscó por timestamp.

Sin embargo, hubo un resultado inesperado en la búsqueda binaria por PM2.5: aunque los 20 valores existían y fueron encontrados mediante búsqueda lineal, la búsqueda binaria no encontró ninguno
### Error o comportamiento inesperado

- **Que ocurrio?** La búsqueda binaria por PM2.5 encontró 0 de los 20 valores que sí existían
- **Por que ocurrio?** La búsqueda binaria necesita que los datos estén ordenados según el mismo valor que se está buscando. Si la lista no está ordenada correctamente por PM2.5, las decisiones de ir hacia la izquierda o hacia la derecha pueden eliminar la posición donde realmente está el dato.
- **Como lo corregimos o que falta corregir?** Se debe verificar que los datos estén ordenados por PM2.5 antes de ejecutar la búsqueda binaria. También se debe comprobar que el orden utilizado por el algoritmo corresponda exactamente con el criterio de búsqueda.
## 4. Explicacion en lenguaje llano

Explica el concepto principal como se lo explicarias a una persona de doce
anos. Usa entre tres y cinco lineas y evita palabras tecnicas que no expliques.

> La búsqueda lineal busca un dato revisando uno por uno, como cuando buscamos un nombre recorriendo toda una lista. La búsqueda binaria primero revisa el centro y elimina una parte de la lista según el resultado. Por eso puede ser mucho más rápida con muchos datos. Pero para funcionar correctamente, los datos deben estar ordenados

### Ejemplo o analogia

Supongamos que tenemos un millón de números escritos en una lista

Con la búsqueda lineal, si queremos encontrar el último número, debemos revisar prácticamente toda la lista

Con la búsqueda binaria, si los números están ordenados, podemos revisar el número del medio si el número que buscamos es mayor, ignoramos todos los números menores y continuamos con la mitad restante

## 5. El vacio que encontre

Al intentar explicar el tema, identifica el punto que aun no comprendes bien.

- **Mi duda concreta es:** ¿Por qué la búsqueda binaria puede ser mucho más rápida que la lineal, pero dejar de funcionar correctamente cuando los datos no están ordenados?
- **Lo que ya puedo explicar es:** La búsqueda lineal revisa los elementos uno por uno y la búsqueda binaria va reduciendo el espacio de búsqueda
- **Para resolver la duda consulte:** Las pruebas realizadas durante la actividad y los resultados de los experimentos
- **Ahora lo entiendo asi:** La busqueda binaria es rapida porque descarta aproximadamente la mitad de los datos en cada comparación. Para poder descartar correctamente una mitad, necesita saber que los datos estan ordenados. Si no lo estan, puede descartar información que contiene el dato buscado

## 6. Trazado de la solucion

Escoge una ejecucion, recorrido o caso representativo y trazalo paso a paso.
Incluye los valores importantes despues de cada paso.

| Paso | Estado de los datos o estructura | Decision o resultado |
|---|---|---|
| 1 | [10, 20, 30, 40, 50, 60, 70, 80, 90] | Se revisa el valor central: 50 |
| 2 | [60, 70, 80, 90] | 70 es mayor que 50, por lo que se descarta la mitad izquierda |
| 3 | [60, 70] | Se revisa nuevamente la parte restante |
| 4 | [70] | Se encuentra el valor buscado |



## 7. Decision de diseño

Relaciona lo aprendido con la Plataforma de Monitoreo Ambiental Urbano.

- **Problema que debiamos resolver:** Encontrar rapidamente una lectura especifica dentro de una gran cantidad de datos generados por los sensores
- **Estructura, algoritmo o estrategia elegida:** Se compararon la busqueda lineal y la busqueda binaria para determinar como realizar consultas puntuales de manera eficiente
- **Alternativa descartada:** Utilizar unicamente busqueda lineal para grandes cantidades de datos
- **Por que elegimos la primera:** La busqueda binaria puede reducir considerablemente las comparaciones cuando los datos cumplen la condicion de estar ordenados. Sin embargo la busqueda lineal sigue siendo util cuando los datos no estan ordenados o cuando no se puede garantizar la precondicion


## 8. Aporte al proyecto

- **Archivo(s) o modulo(s) trabajado(s):** BuscadorLecturas.java, GeneradorDatos.java, BancoDePruebas.java y IngestaSensores.java.
- **Cambio realizado:** Se implementaron metodos de busqueda lineal y busqueda binaria para realizar consultas puntuales sobre las lecturas de los sensores. Tambien se creo un generador de datos sinteticos para realizar pruebas con diferentes cantidades de lecturas y un banco de pruebas para comparar los algoritmos
- **Como se conecta con la capa anterior:** RepositorioLecturas almacena las lecturas y se conecta con BuscadorLecturas para realizar las consultas. IngestaSensores funciona como punto de entrada y coordina el repositorio, los análisis y los experimentos
- **Que queda pendiente para la siguiente semana:** Continuar mejorando las pruebas y documentar con mayor detalle los resultados obtenidos

## 9. Commits realizados

Registra los commits que muestran tu aporte individual.

| Commit | Mensaje | Que demuestra |
|---|---|---|
| `[hash corto]` | `feat: agregar búsqueda lineal por timestamp` | Implementación de la busqueda lineal de lecturas por timestamp |
| `[hash corto]` | `feat: generar datos sintéticos ordenados` | Creación del generador de datos para realizar las pruebas |
| `[hash corto]` | `feat: implementar búsqueda binaria` | Implementación de la búsqueda binaria utilizando timestamps ordenados |

## 10. Reexplicacion final

Despues del taller, vuelve a responder la pregunta de la semana en cinco lineas
o menos. Esta respuesta debe ser mas precisa que la de la seccion 4 y debe
incluir la razon de tu decision tecnica.

> La busqueda lineal revisa los datos uno por uno, mientras que la busqueda binaria reduce el espacio de busqueda aproximadamente a la mitad en cada comparación. Por esta razon, la busqueda binaria puede realizar muchas menos comparaciones cuando existen grandes cantidades de datos. Sin embargo, necesita que los datos esten ordenados segun el criterio de busqueda. Por eso se utilizo la busqueda binaria para timestamps ordenados y se comprobo su problema al intentar utilizarla con PM2.5 sin ordenar

## 11. Reflexion individual

Responde con honestidad:

1. **Lo que ahora puedo hacer y antes no podia:**
   Ahora puedo diferenciar entre una busqueda lineal y una busqueda binaria y entender cuando puedo utilizar cada una
2. **El error o supuesto que mas me enseno:**
   El resultado de la búsqueda binaria con PM2.5 fue lo que más me enseño, porque demostro  que no basta con utilizar un algoritmo más rapido. Tambien hay que cumplir las condiciones necesarias para que funcione correctamente
3. **La pregunta que llevaria a la proxima clase:**
   Qué estructura de datos permitiría realizar busquedas rapidas sin tener que ordenar nuevamente todos los datos cada vez que se agregue una nueva lectura?
4. **Que parte del trabajo fue realmente mia:**
   Trabaje individualmente en la implementacion, ejecución y análisis de las pruebas de busqueda.

## Lista de verificacion antes de entregar

- [ x] Escribi la prediccion antes de consultar el resultado.
- [ x] Inclui evidencia concreta del laboratorio.
- [x ] Explique un concepto sin depender de jerga.
- [x ] Registre un vacio, una duda o un error real.
- [ x] Trace al menos un caso paso a paso.
- [ x] Justifique una decision del proyecto y una alternativa descartada.
- [ ] Registre mis commits y mi aporte individual.
- [ x] Deje claro que queda pendiente.
- [ ] Renombre el archivo con el formato `sXX-nombre.md`.
