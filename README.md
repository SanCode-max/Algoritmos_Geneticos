# Laboratorio: Algoritmos Genéticos

## Preparación del entorno

Verifiquen Python con `python --version` e instalen la extensión **Jupyter** en Visual Studio Code. Creen el entorno virtual en la raíz del proyecto y actívenlo:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
python -m pip install jupyter numpy
```

En Linux o macOS:

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install jupyter numpy
```

El archivo `.gitignore` excluye `.venv/`, `env/`, `venv/`, los checkpoints de Jupyter y los archivos temporales de Python.

## Repositorio y flujo de ramas

Un integrante crea el repositorio en GitHub e invita a los demás como colaboradores. Cada integrante parte de `main` y crea su rama de trabajo:

```bash
git switch main
git pull origin main
git switch -c feature/ejercicio-3
```

Cada ejercicio se desarrolla en su rama, se publica con un Pull Request hacia `main` y se revisa antes de unirlo. La entrega final es el enlace del repositorio con los Pull Requests unidos. El equipo debe acordar previamente qué ejercicio resuelve cada integrante.

## Actividad: optimización combinatoria y restricciones

Se usan genotipos binarios para resolver variantes del problema de la mochila con restricciones físicas o de negocio.

### Ejercicio 1: Portafolio de Inversiones

Se seleccionan proyectos para maximizar el retorno sin superar el presupuesto. El cromosoma binario se decodifica como una selección de proyectos. Si el costo total excede el presupuesto, se aplica una penalización fuerte al fitness para que las soluciones inviables pierdan prioridad.

### Ejercicio 2: Selección de Personal Estricta

Se seleccionan exactamente 5 integrantes entre 12 candidatos maximizando la habilidad técnica. Los cromosomas con un número de bits encendidos diferente de 5 reciben una penalización proporcional a la distancia respecto de la cantidad exigida.

### Ejercicio 3: Cruzamiento de dos puntos

En [Ejercicio_3.ipynb](Ejercicio_3.ipynb) se implementan los cruzamientos de uno y dos puntos. El operador de dos puntos selecciona dos índices distintos, los ordena y construye cada hijo conservando el prefijo y el sufijo de su padre, mientras intercambia el segmento central con el otro padre.

### Ejercicio 4: Análisis del factor de penalización

La penalización fuerte del Ejercicio 1 reduce rápidamente la supervivencia de los cromosomas cuyo costo total supera el presupuesto. Aunque una solución inviable pueda tener un retorno bruto alto, su fitness penalizado queda por debajo del de las soluciones factibles. Por ello tiene menos probabilidad de ser seleccionada y de transmitir sus genes a la siguiente generación.

Generación tras generación, la población tiende a concentrarse en combinaciones cuyo costo se encuentra dentro del presupuesto. La penalización fuerte prioriza el cumplimiento de la restricción y acelera la convergencia hacia soluciones válidas.

Con una penalización suave, las soluciones que exceden el presupuesto conservan una parte mayor de su retorno. En consecuencia, pueden sobrevivir durante más generaciones y seguir influyendo en el cruzamiento. Esto mantiene una mayor diversidad y puede ayudar a explorar combinaciones cercanas al límite del presupuesto.

La desventaja es que la convergencia puede ser más lenta y las soluciones físicamente inviables pueden competir durante más tiempo con las soluciones factibles. La penalización fuerte favorece la factibilidad y elimina rápidamente soluciones inválidas; la penalización suave favorece la exploración y la diversidad, pero permite una mayor supervivencia de soluciones inválidas.

Para comparar ambos factores de forma justa, deben mantenerse constantes la semilla aleatoria, la población inicial, el número de generaciones, la tasa de mutación y la tasa de cruzamiento. En cada generación conviene registrar el mejor fitness y el porcentaje de cromosomas factibles.
