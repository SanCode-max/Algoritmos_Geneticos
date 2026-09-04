# Laboratorio: Algoritmos Genéticos

**Universidad de Cundinamarca - Seccional Ubaté**  
**Programa:** Ingeniería de Sistemas y Computación  
**Materia:** Algoritmos Avanzados / Inteligencia Artificial  
**Docente:** Fabio Alejandro Sastoque Rincón  

---

## 🛠️ Configuración del Entorno de Desarrollo

Para la correcta ejecución del proyecto y el mantenimiento de las buenas prácticas de programación:

1. **Clonar el repositorio:**
   ```bash
   git clone [https://github.com/SanCode-max/Algoritmos_Geneticos.git] (https://github.com/SanCode-max/Algoritmos_Geneticos.git)
   ----Ingresar a la carpeta con el comando-----
    cd Algoritmos_Geneticos

2. Crear y activar el entorno virtual:

# En Windows (PowerShell)
```bash
python -m venv env 
.\env\Scripts\activate

# En Linux / macOS
python3 -m venv env
source env/bin/activate

3. Instalar dependencias necesarias:
pip install numpy jupyter

4. Archivos ignorados en Git: El archivo .gitignore incluye la carpeta env/ y los archivos temporales de Jupyter Notebook para prevenir la subida de elementos innecesarios al repositorio.

- Resumen de Ejercicios Implementados

- Ejercicio 1: Portafolio de Inversiones (Optimización Combinatoria)

    Objetivo: Maximizar el retorno total de inversión seleccionando una combinación factible entre 10 proyectos posibles

    Manejo de Restricción: Si el costo total de los proyectos elegidos supera el presupuesto máximo permitido ($100), se aplica una función de penalización directamente sobre el valor de aptitud (fitness).

Ejercicio 2: Selección de Personal Estricta

    Objetivo: Seleccionar el mejor equipo de desarrollo disponible buscando maximizar la sumatoria de habilidad técnica entre 12 candidatos.

    Manejo de Restricción Estricta: El equipo debe contar con exactamente 5 integrantes. Cualquier cromosoma que no sume exactamente 5 bits encendidos (1s) sufre un castigo severo en su función de aptitud proporcional a la distancia del tamaño requerido.

