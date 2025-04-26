[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=19144036&assignment_repo_type=AssignmentRepo)
# Lab03: Visualización de Datos en Raspberry Pi Zero W

## Integrantes
[Brayan Cufiño]()

[Ivan Castaño ](https://github.com/IFC999)
## Documentación 

## Preguntas

1. ¿Qué función cumple ```plt.fignum_exists(self.fig.number)``` en el ciclo principal?
RTA:Este Verifica si la ventana de la gráfica sigue abierta; si se cierra, el bucle termina.

2. ¿Por qué se usa ```time.sleep(self.intervalo)``` y qué pasa si se quita?
RTA:Pausa el programa entre lecturas; si se quita, el monitoreo será demasiado rápido y cargará el CPU innecesariamente.

3. ¿Qué ventaja tiene usar ```__init__``` para inicializar listas y variables?
RTA:Permite que cada instancia tenga sus propios datos y asegura que todo esté listo al crear el objeto.

4. ¿Qué se está midiendo con ```self.inicio = time.time()```?
RTA:Su funcion es guarda el instante de inicio del monitoreo para calcular el tiempo transcurrido.

5. ¿Qué hace exactamente ```subprocess.check_output(...)```?
RTA: Este ejecuta un comando del sistema y devuelve su salida como texto.

6. ¿Por qué se almacena ```ahora = time.time() - self.inicio``` en lugar del tiempo absoluto?
RTA:Sirve Para mostrar el tiempo relativo desde que empezó el monitoreo, lo cual es más útil en la gráfica.

7. ¿Por qué se usa ```self.ax.clear()``` antes de graficar?
RTA:Su funcion es limpia la gráfica anterior para evitar que los datos se dibujen encima y se sobrecargue visualmente.

8. ¿Qué captura el bloque ```try...except``` dentro de ```leer_temperatura()```?
RTA:El ecuentra los errores al ejecutar el comando o convertir la salida a número, evitando que el programa se detenga.

9. ¿Cómo podría modificar el script para guardar las temperaturas en un archivo .```csv```?RTA:Ya lo hace con self.**guardar_csv(tiempo, temperatura)**; no necesitas modificar nada más
# Documentacion 
# Monitor de Temperatura para Raspberry Pi

En este proyecto se utiliza Python para monitorear la temperatura de la CPU de una Raspberry Pi y graficarla en tiempo real. Además, los datos se almacenan en un archivo CSV para su posterior análisis.

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