# Visualización de datos usando t-SNE
Se realizan visualizaciones de datos multidimensionales en gráficos 2D y 3D usando el algoritmo t-SNE (*t-Distributed Stochastic Neighbor Embedding*)
sobre 3 *datasets* distintos:

- **Dataset de dígitos**: Correspondiente a imágenes de dígitos entre 0 y 9 escritos a mano (similar a MNIST). 
- **Dataset de paises**: Cada *datapoint* corresponde a un país, con estadísticas como GDP, población, área, etc.
- **Dataset de pokemons**: Cada *datapoint* correponde a un pokemon de la 1° generación, con sus estadisticas en videojuegos como características.
  
Sobre cada *dataset* se procede de manera símilar:
- Se importan librerías y datos.
- Se preprocesan los datos.
- Se importa y entrena un modelo t-SNE de Scikit Learn.
- Se visualizan los resultados.

# Visualización de Dígitos

Código implementado y explicado en detalle en **Visualización de Dígitos.ipynb**.

## Importación de datos y librerías
- Se importan las librerías:
  - Numpy 
  - Matplotlib
- Los datos se importan directamente de Scikit Learn:
  - from sklearn.datasets import load_digits

## Preprocesamiento de datos
- Los datos disponibles tienen dimensiones (1797, 64):
  - Hay 1797 *datapoint* cada uno correspondiente a un dígito entre 0 y 9 escrito a mano.
  - Cada *dataponit* corresponde a una imagen de 8x8 pixeles, aplanado a un vector de 64 componentes.
  - Cada pixel es un valor entre 0 y 255.
- Los datos además contienen la etiqueta correcta del número representado, lo que servirá para evaluar los resultados.
- No se requiere realizar transformaciones sobre los datos.

## t-SNE

- Se importa t-SNE desde Scikit-Learn.
- Se crea instancia con *n_components = 2*.
- Se transforman los datos, obteniendo representación con 2 componentes

## Visualización de resultados

- Se grafica cada *datapoint* en un gráfico tipo *scatter* usando *pyplot* de Matplotlib.
- Se grafican las etiquetas de los números sobre los cúmulos para una visualización más fácil.

<p align="center"><img src="images/visualizacion digitos.svg" width=600 height = "auto"></img></p>

- En el gráfico se colorea cada *datapoint* según la etiqueta real.
- Se puede ver que el algoritmo t-SNE separa de manera satisfactoria los dígitos distintos en cúmulos claramente diferenciados entre ellos.

# Visualización de Paises
Código implementado y explicado en detalle en **Visualización de Paises.ipynb**.

## Importación de datos y librerías
- Se importan las librerías:
  - Numpy
  - Pandas
  - Plotly
- Los datos se obtuvieron de Kaggle:  
  - [Global Country Information Dataset 2023](https://www.kaggle.com/datasets/nelgiriyewithana/countries-of-the-world-2023)

## Preprocesamiento de datos
- Se tienen estadísticas de 195 paises.
- Se eliminan los paises con datos faltantes y se reduce a 110 paises.
- Se dejan solo las características numéricas.
- Se limpian y transforman datos numericos en formato *string* a *float*. 
- Se normaliza usando Min-Max.

## t-SNE

- Se importa t-SNE desde Scikit-Learn y se declara instancia con *n_components = 2*.
- Se transforman los datos, obteniendo representación con 2 componentes

## Visualización de resultados
> Se usa la librería Plotly para generar gráficos interactivos.  
> Al colocar cursor sobre *datapoint* se muestra *pop-up* con todos los datos del país.  
> A continuación se muestra una imagen plana, pero al cliquearla se abre el gráfico interactivo en otra pestaña.

- Se grafica cada paises en un gráfico tipo *scatter* según las dos componentes encontradas con t-SNE.

[<img src="images/paises_by_gdp.svg" width=800 height = "auto"></img>](https://rhoffmannv.github.io/t-sne/html/paises-tsne.html)

Ver gráfico interactivo [aquí 📊](https://rhoffmannv.github.io/t-sne/html/paises-tsne.html)

- El gráfico interactivo contiene un desplegable para seleccionar la estadística que se quiere usar para colorear los *datapoints*.
- La imagen estática colorea los paises por GDP y se puede ver una tendiencia, donde los paises en la esquina superior izquierda tienen bajo GDP comparado con los paises de la esquina inferior derecha.
- En el gráfico interactivo se constata que los paises en la esquina superior izquierda corresponden en su mayoría a paises poco desarrollado de África y que paises en el lado derecho corresponden a paises más desarrollados, generalmente europeos o paises de la Mancomunidad Británica de Naciones.
- A su vez, se puede ver que China y la India aparecen agrupados juntos y en el lado derecho, lo que tiene sentido ya que son paises con gran poder económico y con características similares, como la gran cantidad de habitantes.


# Visualización de Pokemons
Código implementado y explicado en detalle en **Visualización de Pokemons.ipynb**.

## Importación de datos y librerías
- Se importan las librerías:
  - Numpy 
  - Pandas
  - Plotly
- Los datos se obtuvieron de Kaggle:  
  - [Pokemon with stats](https://www.kaggle.com/datasets/abcsds/pokemon)

## Preprocesamiento de datos
- Se tienen datos de 721 Pokemones.
- Por cada Pokemon se tiene estadísticas de juego como *attack*, *defense*, *primary type*, *secondary type*, etc.
- Se dejan solo los Pokemon de la primera generación (151).
- Se normaliza con Min-Max los datos númericos.
- Se transforman los valores booleanos a 0 y 1 (si es o no legendario). 
- Se transforman las categorias a codificación One-Hot (para *primary type* y *secondary type*).
- Se eliminan columnas innecesarias como el nombre del Pokemon, etc.

## t-SNE

- Se importa t-SNE desde Scikit-Learn y se declara instancia con *n_components = 2*.
- Se transforman los datos, obteniendo representación con 2 componentes.

## Visualización de resultados
> Se usa la librería Plotly para generar gráficos interactivos.  
> Al colocar cursor sobre *datapoint* se muestra *pop-up* con todas las estadíticas del Pokemon.  
> A continuación se muestran imágenes planas, pero se pueden abrir los gráficos interactivos cliqueándolas.  

### Gráfico por tipo primario
En el siguiente gráfico se ubican los Pokemon según los componentes de t-SNE y se colorean según su *tipo primario*.

[<img src="images/by_type.svg" width=800 height = "auto"></img>](https://rhoffmannv.github.io/t-sne/html/by_type_text.html)

Ver gráfico interactivo [aquí 📊](https://rhoffmannv.github.io/t-sne/html/by_type_text.html)  

- Se puede ver que el algoritmo t-SNE separa claramente los Pokemon según su *tipo primario*.
- En el gráfico interactivo se puede ver como agrupa de manera correcta Pokemons y sus evoluciones.
- También agrupa los Pokemon legendarios aun cuando tienen *tipos* distintos.
- Resulta interesante que agrupa a Charizard cerca de los legendarios, lo que tiene sentido puesto que es uno de los Pokemons más fuertes.

### Gráfico por tipo secundario
En el siguiente gráfico se ubican los Pokemon según los componentes de t-SNE y se colorean según su *tipo secundario*. 

[<img src="images/by_type_2.svg" width=800 height = "auto"></img>](https://rhoffmannv.github.io/t-sne/html/by_type_2_text.html)

Ver gráfico interactivo [aquí 📊](https://rhoffmannv.github.io/t-sne/html/by_type_2_text.html)  

- Se puede ver que el algoritmo t-SNE también separa claramente los Pokemon según su *tipo secundario*.
- Se muestran todos los Pokemon sin *tipo secundario* en rojo y se puede ver que quedan también agrupados en el lado izquierdo del gráfico.

### Gráfico 3D

- Se crea gráfico interactivo 3D con Plotly.
- Para esto se requiere ajustar el algoritmo t-SNE con 3 componentes.
- Se grafica coloreando los Pokemons según su *tipo principal*. El tamaño de las esferas se determina a partir del poder total de los Pokemon.

Ver gráfico interactivo 3D [aquí 📊](https://rhoffmannv.github.io/t-sne/html/pokemon_3d.html)  
