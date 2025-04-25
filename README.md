[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=19144036&assignment_repo_type=AssignmentRepo)
# Lab03: Visualización de Datos en Raspberry Pi Zero W

## Integrantes

## Preguntas

1. ¿Qué función cumple ```plt.fignum_exists(self.fig.number)``` en el ciclo principal?

2. ¿Por qué se usa ```time.sleep(self.intervalo)``` y qué pasa si se quita?

3. ¿Qué ventaja tiene usar ```__init__``` para inicializar listas y variables?

4. ¿Qué se está midiendo con ```self.inicio = time.time()```?

5. ¿Qué hace exactamente ```subprocess.check_output(...)```?

6. ¿Por qué se almacena ```ahora = time.time() - self.inicio``` en lugar del tiempo absoluto?

7. ¿Por qué se usa ```self.ax.clear()``` antes de graficar?

8. ¿Qué captura el bloque ```try...except``` dentro de ```leer_temperatura()```?

9. ¿Cómo podría modificar el script para guardar las temperaturas en un archivo .```csv```?
# Documentacion 
# Monitor de Temperatura para Raspberry Pi

En este proyecto se utiliza Python para monitorear la temperatura de la CPU de una Raspberry Pi y graficarla en tiempo real. Además, los datos se almacenan en un archivo CSV para su posterior análisis.

Importación de librerías
Se importan las siguientes librerías:
- matplotlib.pyplot: Utilizada para graficar la temperatura en tiempo real.

- time: Para gestionar los tiempos de muestreo de la temperatura.

- subprocess: Permite ejecutar comandos del sistema, en este caso, vcgencmd, para obtener la temperatura de la Raspberry Pi.

- csv: Para guardar los datos de temperatura y tiempo en un archivo CSV.

- os: Se usa para verificar la existencia del archivo CSV.

 La funcion de este codigo se encarga de monitorear la temperatura de la CPU de una Raspberry Pi en tiempo real, 
 graficando los resultados y guardándolos en un archivo CSV para su posterior análisis.  Primero, se importa la librería **matplotlib** para la creación de la gráfica, **time** para gestionar el 
 tiempo de muestreo, **subprocess** para ejecutar comandos del sistema y obtener la temperatura, **csv** 
 para manejar la creación y escritura del archivo CSV, y **os** para verificar la existencia del archivo donde 
 se guardarán los datos.

La clase **MonitorTemperaturaRPI** modela el proceso de monitoreo. Se define con los parámetros de duración máxima, 
 intervalo de actualización y el archivo CSV donde se almacenarán los datos. Si el archivo no existe, se crea automáticamente 
 con las cabeceras correspondientes. Dentro de esta clase, se establece un gráfico en tiempo real con **matplotlib** 
 para mostrar la temperatura y los datos de tiempo a medida que se recogen.
la función **leer_temperatura** se encarga de obtener la temperatura de la Raspberry Pi utilizando el comando 
 **vcgencmd measure_temp**. Esta lectura se realiza de manera continua dentro del ciclo de monitoreo. Si se presenta un 
error al obtener la temperatura, se maneja con un mensaje para que el usuario sepa que algo salió mal. 

Cada vez que se actualizan los datos, **actualizar_datos** registra la temperatura obtenida junto con el tiempo 
 transcurrido desde el inicio del monitoreo. Los datos se almacenan en el archivo CSV y también se actualiza la gráfica. 
 En caso de que el tiempo de monitoreo supere el límite configurado, los datos más antiguos se eliminan para mantener 
la visualización y el almacenamiento organizados.

La función **graficar** actualiza la visualización de la gráfica en tiempo real, mostrando la relación entre 
 el tiempo transcurrido y la temperatura. Al mismo tiempo, **guardar_csv** asegura que cada medición de temperatura  y su correspondiente tiempo se registren correctamente en el archivo CSV para análisis posterior Por último, **ejecutar** es el método principal que arranca el monitoreo en un bucle continuo, actualizando los 
datos, graficando y almacenando la información, hasta que el usuario interrumpe el proceso manualmente con una 
 señal de interrupción.