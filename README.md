# Proyecto_Final_Tratamiento_MST
 Proyecto final Tratamiento de datos 
Parametros de configuración 

El ancho deseado de las imágenes de entrada a la red neuronal. Se establece en 224 píxeles.
La altura deseada de las imágenes de entrada a la red neuronal. También se establece en 224 píxeles.
El número de clases en el problema de clasificación. En este proyecto, se establece en 8 clases debido a las 4 carpetas de carnes definidas .

epochs: el número de veces que se entrenará la red neuronal en todo el conjunto de datos estará definida en 20.

El tamaño del lote (batch size), que representa el número de ejemplos de entrenamiento que se utilizarán en cada paso de actualización de los pesos de la red.

Ruta del Dataset 

Rutas de los directorios que contienen tus datos de entrenamiento y validación. 
El directorio "CarneDataset/train" contiene los datos de entrenamiento
El directorio "CarneDataset/test" contiene los datos de validación.

#Ruta del Dataset 
#train_data_dir = r'C:\Users\msantacruz\Downloads\Github2023\Proyecto_Final_Tratamiento_MST\CarneDataset\train'  
#validation_data_dir = r'C:\Users\msantacruz\Downloads\Github2023\Proyecto_Final_Tratamiento_MST\CarneDataset\test'
train_data_dir = 'CarneDataset/train'
validation_data_dir = 'CarneDataset/test'


Generador de imagenes 

Se configura generadores de imágenes con aumentación de datos para aplicar transformaciones aleatorias a las imágenes durante el entrenamiento y la evaluación del modelo. Luego, utilizo estos generadores para cargar los datos de entrenamiento y validación desde los directorios correspondientes. Esto es útil para aumentar la cantidad y la variedad de datos disponibles durante el entrenamiento, lo que puede mejorar el rendimiento y la generalización del modelo

Se configuran generadores de datos utilizando la clase ImageDataGenerator de Keras. Estos generadores se utilizan para realizar aumentación de datos y preparar los lotes de imágenes durante el entrenamiento y la validación del modelo.

Dentro de la generación se encuentra lo siguiente :

En el difrectorio train: 1633 imagenes distrinuidas en 8 classes.
En el difrectorio test: 810 imagenes distrinuidas en 8 classes.


Creación y entrenamientos 

# Creación y entrenamiento de modelo CNN

Dentro de la configuración de modelos se detallan  los siguientes :

Dentro de este modelo se presentaron 11 capas neuronales de lo que se obtuvo una respuesta de entrenamiento de 11180488

5 capas de convolución 2D (Conv2D).
2 capas de agrupamiento máximo (MaxPool2D).
1 capa de aplanamiento (Flatten).
3 capas completamente conectadas (Dense).
1 capa de salida completamente conectada (Dense) con función de activación softmax.

El número total de parámetros entrenables en el modelo es 11,180,488.

# Modelo VGG16
	
	El modelo VGG16 pre-entrenado, agrega una capa densa para la clasificación y crea un modelo personalizado,el código tiene un total de cuatro 	capas principales: una capa de entrada, las capas del modelo VGG16 pre-entrenado, una capa de salida y la capa del modelo personalizado.
	
	El número de parámetros no entrenables es de 134,260,544. Estos son los parámetros de las capas convolucionales y de agrupación del modelo 	VGG16 pre-entrenado
	
	El número de parámetros entrenables es de 32,776. Estos son los parámetros de la capa densa


#Modelo VGG16 Tunning
	
	Las características aprendidas por VGG16 en tareas generales de clasificación de imágenes, personalizar el modelo añadiendo capas 	adicionales, y realizar fine-tuning al permitir que algunas capas pre-entrenadas se actualicen durante el entrenamiento.
	
	En lugar de congelar completamente las capas pre-entrenadas. El proceso de "fine-tuning" implica permitir que algunas capas pre-entrenadas se 	actualicen durante el entrenamiento, mientras que otras se mantienen congeladas.

# Modelo Resnet 50 
	El modelo pre-entrenado ResNet50. Agrega capas densas adicionales, congela la mayoría de las capas pre-entrenadas y compila el modelo para su 	entrenamiento y evaluación en tu problema de clasificación de imágenes específico.

# Modelo VGG19 

	Mayor cantidad de parámetros y memoria requerida.
	Buen rendimiento.

Optimizador utilizado 

El optimizador utilizado es Adadelta y la métrica de precisión durante el entrenamiento y la evaluación. Esto permite que el modelo calcule y optimice la pérdida durante el entrenamiento, y muestre la precisión como una métrica de evaluación.




Conclusiones 

Los resultados que estás mostrando parecen ser las métricas de evaluación de un modelo de clasificación.

CLASS_01: 0,
CLASS_02: 1,
CLASS_03: 2,
CLASS_04: 3,
CLASS_05: 4,
CLASS_06: 5,
CLASS_07: 6,
CLASS_08: 7

	Clase	Precision recall     f1-score   support

           0     0.0000    0.0000    0.0000         1
           1     0.0625    0.0208    0.0312        48
           2     0.3151    0.4742    0.3786        97
           3     0.0833    0.1333    0.1026        45
           4     0.8463    0.8519    0.8491       459
           5     0.3333    0.0526    0.0909        19
           6     0.4906    0.4561    0.4727       114
           7     0.4000    0.0741    0.1250        27

    accuracy                         0.6160       810
   macro avg     0.3164    0.2579    0.2563       810
weighted avg     0.6158    0.6160    0.6069       810

Precisión
El cociente entre el número de verdaderos positivos y la suma de verdaderos positivos y falsos positivos.La precisión varía para cada clase, siendo la más alta para la clase 5 con un valor de 0.8463.

Recall:
La proporción de instancias positivas que fueron correctamente identificadas. Se calcula como el cociente entre el número de verdaderos positivos y la suma de verdaderos positivos y falsos negativos.El más alto para la clase 5 con un valor de 0.8519.

F1-score: 
Util cuando tienes clases desequilibradas. 
Se calcula como 2 * (precision * recall) / (precision + recall). 
El más alto para la clase 5 con un valor de 0.8491.


Accuracy : 
El accuracy es del 0.6160, lo que indica que aproximadamente el 61.6% de las muestras fueron clasificadas correctamente.

Macro avg  y weighted avg
Promedios de las métricas para todas las clases. La media macro calcula las métricas sin tener en cuenta el desequilibrio de clases, mientras que la media ponderada tiene en cuenta el soporte (support) de cada clase en el cálculo.


Comparación de predicción de modelos

VGG16 como MobileNet clasificaron correctamente una imagen en la clase CLASS_03. Estos resultados indican que ambos modelos lograron asignar correctamente la etiqueta de clasificación para esa imagen en particular.

VGG16
1/1 [==============================] - 1s 688ms/step
CLASS_03

Mobile NET 
1/1 [==============================] - 1s 610ms/step
CLASS_03
