# Visualización de datos usando t-SNE
Se realizan visualizaciones de datos multidimensionales en gráficos 2D y 3D usando el algoritmo t-SNE (*t-Distributed Stochastic Neighbor Embedding*)
sobre 3 *datasets* distintos:

- **Dataset de dígitos**: Correspondiente a imágenes de dígitos entre 0 y 9 escritos a mano (similar a MNIST).
- **Dataset de paises**: Cada *datapoint* corresponde a un país, con estadísticas como GDP, población, área, etc.
- **Dataset de pokemons**: Cada *datapoint* correponde a un pokemon de la 1° generación, con sus estadisticas en videojuegos como características.

El código implementado para cada *dataset* se encuentra en los Jupyter Notebooks, respectivamente:
- **Visualización de Dígitos.ipynb**
- **Visualización de Paises.ipynb**
- **Visualización de Pokemons.ipynb**

Sobre cada *dataset* se procede de manera símilar:
- Se importan librerías y datos.
- Se preprocesan los datos.
- Se importa y entrena un modelo t-SNE de Scikit Learn.
- Se visualizan los resultados.

# Visualización de Dígitos
<img src="images/visualizacion digitos.svg" width=600 height = "auto"></img>


# Visualización de Pokemons

<img src="images/by_type.svg" width=600 height = "auto"></img>   
Ver gráfico interactivo [aquí 📊](https://rhoffmannv.github.io/t-sne/html/by_type_text.html)

<img src="images/by_type_2.svg" width=600 height = "auto"></img>

Ver gráfico interactivo [aquí 📊](https://rhoffmannv.github.io/t-sne/html/by_type_2_text.html)

# Visualización de Paises

<img src="images/paises_by_gdp.svg" width=600 height = "auto"></img>

Ver gráfico interactivo [aquí 📊](https://rhoffmannv.github.io/t-sne/html/paises_by_gdp_text.html)
