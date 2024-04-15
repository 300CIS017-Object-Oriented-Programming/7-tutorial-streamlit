A continuación verás información para usar botones, imprimir texto, checkbox, radio buttons, file_loader  y otros. 
Información de todos los posibles componentes de Streamlit está disponible en la documentación oficial y también en:
https://cheat-sheet.streamlit.app/


### st.button

`st.button` permite mostrar un botón.

#### Que estamos construyendo?

Una simple aplicación que imprime condicionalmente diferentes mensajes dependiendo si el botón fue presionado o no.

Comportamiento de la aplicación:

1. Por defecto, la aplicación imprime `Goodbye`
2. Una vez que se hace click sobre el botón, la aplicación imprime `Why hello there`

#### Demo app

La aplicación de Streamlit debería verse como la mostrada en el siguiente link:

[![Streamlit App](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/dataprofessor/st.button/)

#### Código

Aquí tenemos el código para implementar la aplicación previamente mencionada: Guarda este código como app_button.py

```python
import streamlit as st

st.header('st.button')

if st.button('Say hello'):
     st.write('Why hello there')
else:
     st.write('Goodbye')
```

El código para ejecutar esta app seria: 

#### Explicación linea por linea

Lo primero que tenemos que hacer cuando creamos una aplicación de Streamlit es comenzar importando la librería `streamlit` de la siguiente manera:

```python
import streamlit as st
```

Seguimos por crear un encabezado de texto para la aplicación:

```python
st.header('st.button')
```

Siguiente, vamos a usar los condicionales `if` y `else` para imprimir los correspondientes mensajes.

```python
if st.button('Say hello'):
     st.write('Why hello there')
else:
     st.write('Goodbye')
```

Como podemos ver en el anterior código, el comando `st.button()` admite el argumento `label` con el valor `Say hello`, el cual es el texto que el botón muestra.

El comando `st.write` es usado para imprimir mensajes tales como `Why hello there` o `Goodbye` dependiendo si el botón fue presionado o no, lo cual es implementado de la siguiente manera:


```python
st.write('Why hello there')
```

y

```python
st.write('Goodbye')
```

Es importante tener en cuenta que los `st.write` están colocados debajo de las condiciones `if` y `else` para realizar el mencionado proceso de mostrar mensajes alternativos.


### st.write
`st.write` permite imprimir texto y datos en la Streamlit app. 

Además de poder mostrar texto, también se puede mostrar lo siguiente mediante el comando `st.write()`:


- Muestra cadenas; funciona como `st.markdown()`
- Muestra un `dict` de Python
- Muestra `pandas` DataFrame se puede mostrar como una tabla
- Gráficos/Esquemas/Representaciones de `matplotlib`, `plotly`, `altair`, `graphviz`, `bokeh`
- Y mas (ver [st.write en la documentación de Streamlit](https://docs.streamlit.io/library/api-reference/write-magic/st.write))

#### Que estamos construyendo?

Una aplicación sencilla que muestra las diversas formas de utilizar el comando `st.write()` para mostrar texto, números, marcos de datos y gráficos.

#### Demo app

La aplicación de Streamlit debería verse como la mostrada en el siguiente link:

[![Streamlit App](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/dataprofessor/st.write/)

#### Código

Así es como se usa st.write:

```python
import numpy as np
import altair as alt
import pandas as pd
import streamlit as st

st.header('st.write')

# Ejemplo 1

st.write('Hello, *World!* :sunglasses:')

# Ejemplo 2

st.write(1234)

# Ejemplo 3

df = pd.DataFrame({
     'first column': [1, 2, 3, 4],
     'second column': [10, 20, 30, 40]
     })
st.write(df)

# Ejemplo 4

st.write('Below is a DataFrame:', df, 'Above is a dataframe.')

# Ejemplo 5

df2 = pd.DataFrame(
     np.random.randn(200, 3),
     columns=['a', 'b', 'c'])
c = alt.Chart(df2).mark_circle().encode(
     x='a', y='b', size='c', color='c', tooltip=['a', 'b', 'c'])
st.write(c)
```

#### Explicación linea por linea

Lo primero que tenemos que hacer cuando creamos una aplicación de Streamlit es comenzar importando la librería `streamlit` de la siguiente manera:

```python
import streamlit as st
```

Seguimos por crear un encabezado de texto para la aplicación:

```python
st.header('st.write')
```

**Ejemplo 1**
Su caso de uso básico es mostrar texto y texto con formato Markdown:

```python
st.write('Hello, *World!* :sunglasses:')
```

**Ejemplo 2**
Como se mencionó anteriormente, también se puede usar para mostrar otros formatos de datos, como números:

```python
st.write(1234)
```

**Ejemplo 3**
Los DataFrames también se pueden mostrar de la siguiente manera:

```python
df = pd.DataFrame({
     'first column': [1, 2, 3, 4],
     'second column': [10, 20, 30, 40]
     })
st.write(df)
```

**Ejemplo 4**
Puedes pasar múltiples argumentos:

```python
st.write('Below is a DataFrame:', df, 'Above is a dataframe.')
```

**Ejemplo 5**
Finalmente, también puede mostrar gráficos pasándolos a una variable de la siguiente manera:

```python
df2 = pd.DataFrame(
     np.random.randn(200, 3),
     columns=['a', 'b', 'c'])
c = alt.Chart(df2).mark_circle().encode(
     x='a', y='b', size='c', color='c', tooltip=['a', 'b', 'c'])
st.write(c)
```

#### Demo app

La aplicación de Streamlit debería verse como la mostrada en el siguiente link:

[![Streamlit App](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/dataprofessor/st.write/)


### st.slider

`st.slider` permite la visualización de un control deslizante.

Se admiten los siguientes tipos de datos: int, float, date, time y datetime.

#### Que estamos construyendo?

Una aplicación simple que muestra diferentes maneras de como aceptar datos del usuario con el control deslizante

Comportamiento de la aplicación:
1. El usuario selecciona el valor ajustando el control deslizante
2. La aplicación imprime el valor seleccionado

#### Demo app

[![Streamlit App](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/dataprofessor/st.slider/)


#### Código
He aquí cómo usar st.slider:

```python
import streamlit as st
from datetime import time, datetime

st.header('st.slider')

# Ejemplo 1

st.subheader('Slider')

age = st.slider('How old are you?', 0, 130, 25)
st.write("I'm ", age, 'years old')

# Ejemplo 2

st.subheader('Range slider')

values = st.slider(
     'Select a range of values',
     0.0, 100.0, (25.0, 75.0))
st.write('Values:', values)

# Ejemplo 3

st.subheader('Range time slider')

appointment = st.slider(
     "Schedule your appointment:",
     value=(time(11, 30), time(12, 45)))
st.write("You're scheduled for:", appointment)

# Ejemplo 4

st.subheader('Datetime slider')

start_time = st.slider(
     "When do you start?",
     value=datetime(2020, 1, 1, 9, 30),
     format="MM/DD/YY - hh:mm")
st.write("Start time:", start_time)

```

## Explicación línea por línea
Lo primero que debe hacer al crear una aplicación Streamlit es comenzar importando la biblioteca `streamlit` como `st` así:
```python
import streamlit as st
from datetime import time, datetime
```

A esto le sigue la creación de un texto de encabezado para la aplicación::
```python
st.header('st.slider')
```

**Ejemplo 1**

Deslizador:

```python
st.subheader('Slider')

age = st.slider('How old are you?', 0, 130, 25)
st.write("I'm ", age, 'years old')
```

Como podemos ver, el comando `st.slider()`
se utiliza para recopilar información del usuario sobre la edad de los usuarios.

El primer argumento de entrada muestra el texto justo encima del componente **slider** que pregunta `'How old are you?'`.

Los siguientes tres enteros `0, 130, 25` representan los valores mínimo, máximo y predeterminado, respectivamente.

**Ejemplo 2**

Slider de rango:

```python
st.subheader('Range slider')

values = st.slider(
     'Select a range of values',
     0.0, 100.0, (25.0, 75.0))
st.write('Values:', values)
```

El control deslizante de rango permite la selección de un par de valores límite inferior y superior.

El primer argumento muestra el texto justo encima del control deslizante de **rango** que pregunta `'Select a range of values'`.

Los siguientes tres argumentos `0.0, 100.0, (25.0, 75.0)` representan los valores mínimo y máximo, mientras que la última tupla indica los valores predeterminados que se utilizarán como valores límite inferior (25.0) y superior (75.0) seleccionados.

**Ejemplo 3**

Deslizador para rango de tiempo:

```python
st.subheader('Range time slider')

appointment = st.slider(
     "Schedule your appointment:",
     value=(time(11, 30), time(12, 45)))
st.write("You're scheduled for:", appointment)
```

El control deslizante de rango de tiempo permite la selección de un par de valores límite inferior y superior de fecha y hora.

El primer argumento muestra el texto justo encima del control deslizante de **rango de tiempo** que pregunta `'Schedule your appointment:`.

Los valores predeterminados para los pares de valores límite inferior y superior de fecha y hora se establecen en 11:30 y 12:45, respectivamente.

**Ejemplo 4**

Datetime slider:

```python
st.subheader('Datetime slider')

start_time = st.slider(
     "When do you start?",
     value=datetime(2020, 1, 1, 9, 30),
     format="MM/DD/YY - hh:mm")
st.write("Start time:", start_time)
```

El control deslizante de datetime permite la selección de una fecha y hora.

El primer argumento muestra el texto justo encima del control deslizante **datetime** que pregunta `'When do you start?'`.

El valor predeterminado para la fecha y hora se estableció mediante la opción `value` para que sea el 1 de enero de 2020 a las 9:30

#### Otras lecturas
También puede explorar el siguiente componente relacionado:
- [`st.select_slider`](https://docs.streamlit.io/library/api-reference/widgets/st.select_slider)

### st.selectbox

`st.selectbox` permite la visualización de un componente de selección.

#### Que estamos construyendo?

Una sencilla aplicación que pregunta al usuario cuál es su color favorito.

Comportamiento de la aplicación:
1. El usuario selecciona un color
2. La aplicación imprime el color seleccionado

#### Demo app
La aplicación Streamlit implementada debería parecerse a la que se muestra en el siguiente enlace:

[![Streamlit App](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/dataprofessor/st.selectbox/)

#### Codigo
Aquí está el código para implementar la aplicación mencionada anteriormente:
```python
import streamlit as st

st.header('st.selectbox')

option = st.selectbox(
     'What is your favorite color?',
     ('Blue', 'Red', 'Green'))

st.write('Your favorite color is ', option)
```

#### Explicación línea por línea
Lo primero que debe hacer al crear una aplicación Streamlit es comenzar importando la librería `streamlit` como `st` de la siguiente manera:
```python
import streamlit as st
```

A esto le sigue la creación de un texto de encabezado para la aplicación:
```python
st.header('st.selectbox')
```

A continuación, crearemos una variable llamada `option` que aceptará la entrada del usuario a través del comando "st.selectbox()".

```python
option = st.selectbox(
     'What is your favorite color?',
     ('Blue', 'Red', 'Green'))
```
Como podemos ver en el cuadro de código anterior, el comando `st.selectbox()` acepta 2 argumentos:
1. El texto que va encima del componente de selección, es decir, `'What is your favorite color?'`
2. Los valores posibles para seleccionar `('Blue', 'Red', 'Green')`

Finalmente, imprimiremos el color seleccionado de la siguiente manera:
```python
st.write('Your favorite color is ', option)
```

#### Referencias
Más información sobre [`st.selectbox`](https://docs.streamlit.io/library/api-reference/widgets/st.selectbox)

### st.checkbox

`st.checkbox` muestra un componente de casilla de verificación.

#### Demo app

[![Streamlit App](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/dataprofessor/st.checkbox/)

#### Código
Aquí se explica cómo usar `st.checkbox`:
```python
import streamlit as st

st.header('st.checkbox')

st.write ('What would you like to order?')

icecream = st.checkbox('Ice cream')
coffee = st.checkbox('Coffee')
cola = st.checkbox('Cola')

if icecream:
     st.write("Great! Here's some more 🍦")
    
if coffee: 
     st.write("Okay, here's some coffee ☕")

if cola:
     st.write("Here you go 🥤")
```

#### Explicación línea por línea
Lo primero que debe hacer al crear una aplicación Streamlit es comenzar importando la librería `streamlit` como `st` de la siguiente manera:
```python
import streamlit as st
```

A esto le sigue la creación de un encabezado para la aplicación:
```python
st.header('st.checkbox')
```

A continuación, haremos una pregunta a través de `st.write`:
```python
st.write ('What would you like to order?')
```

Luego vamos a proporcionar algunos elementos de menú para seleccionar:
```python
icecream = st.checkbox('Ice cream')
coffee = st.checkbox('Coffee')
cola = st.checkbox('Cola')
```

Finalmente, vamos a imprimir texto personalizado según la casilla de verificación que se seleccionó:
```python
if icecream:
     st.write("Great! Here's some more 🍦")
    
if coffee: 
     st.write("Okay, here's some coffee ☕")

if cola:
     st.write("Here you go 🥤")
```  

##### Otras lecturas
- [`st.checkbox`](https://docs.streamlit.io/library/api-reference/widgets/st.checkbox)

### st.file_uploader

`st.file_uploader` muestra un componente para subir archivos [[1](https://docs.streamlit.io/library/api-reference/widgets/st.file_uploader)].

De forma predeterminada, los archivos cargados están limitados a 200 MB. Puede configurar esto usando server.maxUploadSize. Para obtener más información sobre utilizar las opciones de configuración, consulte [[2](https://docs.streamlit.io/library/advanced-features/configuration#set-configuration-options)].

#### Demo app

[![Streamlit App](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/dataprofessor/st.file_uploader/)

#### Código
Aquí se explica cómo usar `st.file_uploader`:
```python
import streamlit as st
import pandas as pd

st.title('st.file_uploader')

st.subheader('Input CSV')
uploaded_file = st.file_uploader("Choose a file")

if uploaded_file is not None:
  df = pd.read_csv(uploaded_file)
  st.subheader('DataFrame')
  st.write(df)
  st.subheader('Descriptive Statistics')
  st.write(df.describe())
else:
  st.info('☝️ Upload a CSV file')
```

#### Explicación línea por línea
Lo primero que debe hacer al crear una aplicación Streamlit es comenzar importando la librería `streamlit` como `st` y otras de la siguiente manera:
```python
import streamlit as st
import pandas as pd
```

A esto le sigue la creación de un título para la aplicación:
```python
st.title('st.file_uploader')
```

A continuación, usaremos `st.file_uploader` para mostrar un componente de carga de archivos:
```python
st.subheader('Input CSV')
uploaded_file = st.file_uploader("Choose a file")
```

Finalmente, definimos la condición para mostrar inicialmente un mensaje de bienvenida invitando a los usuarios a cargar su archivo (como se implementa en la condición `else`). Al cargar el archivo, la condición `if` se activa y la biblioteca `pandas` lee el archivo CSV y lo muestra a través del comando `st.write`.
```python
if uploaded_file is not None:
  df = pd.read_csv(uploaded_file)
  st.subheader('DataFrame')
  st.write(df)
  st.subheader('Descriptive Statistics')
  st.write(df.describe())
else:
  st.info('☝️ Upload a CSV file')
```
