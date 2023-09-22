# Interacting with the Twitter API

Twitter se puede utilizar como fuente de datos para varios proyectos de ciencia de datos.

En este ejercicio, aprenderemos a interactuar con la API de Twitter. Practicaremos almacenar tweets en un marco de datos y guardarlos en un archivo csv.

Tweepy es una biblioteca de Python para acceder a la API de Twitter. Deberás configurar una aplicación de Twitter en dev.twitter.com para obtener un conjunto de claves de autenticación para usar con la API.

### Paso 1: crea una cuenta de desarrollador de Twitter

Crea una aplicación en la cuenta de desarrollador: https://developer.twitter.com/ . 
Asegúrate de obtener bearer_token, consumer_key, consumer_secret, access_token, access_token_secret y guárdalos en un lugar seguro.

Estos se pueden generar en tu portal de desarrollador, en la pestaña "Claves y tokens" de tu aplicación de desarrollador.

Orientación sobre cómo crear una aplicación de Twitter (pasos 1 y 2): https://developer.twitter.com/en/docs/tutorials/step-by-step-guide-to-making-your-first-request-to-the-twitter-api-v2

### Paso 2: Configuración inicial

- Crear un archivo app.py dentro de la carpeta `./src/`.
- Instalar Tweepy usando PIP.

### Paso 3: Variables de entorno

Debes proporcionar las claves y los tokens de Twitter para poder utilizar la API v2.

Para hacerlo de forma segura, debes almacenar los secretos en un archivo .env separado.
Un archivo dotenv contiene solo texto, donde tienes una asignación de variable de entorno por línea.
Crea un archivo .env en tu proyecto y agrega tus claves secretas o contraseñas:

```py
CONSUMER_KEY="insert your API key"
CONSUMER_SECRET="insert your API secret"
ACCESS_TOKEN="insert your access token"
ACCESS_TOKEN_SECRET="insert your access token secret"
BEARER_TOKEN="insert your bearer token"
```

> Importante: asegúrate de agregar el .env dentro de su archivo .gitignore, que no se guarda en el control de fuente, para que no estés poniendo en riesgo información potencialmente confidencial.
Ahora, debes instalar python-dotenvpackage. python-dotenv es un paquete de Python que permite que tu aplicación de Python lea un archivo .env. Este paquete buscará un .env y, si lo encuentra, expondrá las variables que contiene a la aplicación.

Ejemplo:

```py
from dotenv import load_dotenv   #para el método python-dotenv
load_dotenv()                    

import os 

consumer_key = os.environ.get('CONSUMER_KEY')
consumer_secret = os.environ.get('CONSUMER_SECRET')
access_token = os.environ.get('ACCESS_TOKEN')
access_token_secret = os.environ.get('ACCESS_TOKEN_SECRET')
bearer_token = os.environ.get('BEARER_TOKEN')

```

Para establecer una contraseña o claves secretas en la variable de entorno en Linux (y Mac) o Windows, consulta el siguiente enlace: https://dev.to/biplov/handling-passwords-and-secret-keys-using-environment-variables-2ei0

### Paso 4: Inicializar la biblioteca tweepy

- Importar Tweepy y [biblioteca de solicitudes](https://requests.readthedocs.io/en/latest/)
- Hacer una conexión con API v2. Usa las variables en la función `tweepy.Client()`.

> Utiliza la siguiente documentación como guía sobre los parámetros.: https://docs.tweepy.org/en/stable/client.html
### Paso 5: Comienza a realizar solicitudes a la API

- Haz una consulta: Busca tweets que tengan el hashtag #100daysofcode y la palabra python o pandas, de los últimos 7 días (search_recent_tweets).
- No incluyas retweets. Limita el resultado a un máximo de 100 Tweets.
- También incluye información adicional con tweet_fields (identificación del autor, cuándo se creó el tweet, el idioma del texto del tweet).

Puedes usar este enlace para obtener orientación sobre cómo crear la consulta: https://developer.twitter.com/en/docs/twitter-api/tweets/search/integrate/build-a-query


1. Definir consulta.
2. Obtener un máximo. 100 tweets (es el máximo permitido por la API de Twitter).


### Paso 6: Convertir a Pandas Dataframe

1. Importar pandas.
2. Guardar datos como diccionario.
3. Extraer el valor de "datos" del diccionario.
4. Transformar a pandas Dataframe
5. Echar un vistazo al Dataframe (marco de datos) para asegurarse de que sea correcto `df.head ()`.
6. Guardar los datos como un archivo CSV llamado coding-tweets.csv.

### Paso 7: Buscar las palabras

Ahora que has configurado tu DataFrame de tweets, vas a hacer un poco de análisis de texto para contar cuántos tweets contienen las palabras 'pandas' y 'python'. Define la siguiente función word_in_text(), que te indicará si el primer argumento (una palabra) aparece dentro del segundo argumento (un tweet).

> Asegúrate de convertir cualquier palabra o texto de tweet a minúsculas.
> Puedes usar la biblioteca re python (operaciones de expresiones regulares). Consulta la documentación para obtener orientación.: https://docs.python.org/3/library/re.html#


1. Importar la biblioteca `re` usando `import re`.
2. Definir tu función `word_in_text` e implemente el código.
### Paso 11:

Itera a través de las filas del DataFrame contando la cantidad de tweets en los que se mencionan pandas y python, usando tu función word_in_text().

1. Inicializar la lista para almacenar los recuentos de tweets.
2. Iterar a través de df, contando la cantidad de tweets en los que se menciona cada uno (pandas y python).

### Paso 12: Visualizar los datos

1. Importar paquetes.
2. Establecer estilo seaborn.
3. Crear una lista de etiquetas: cd.
4. Trazar el gráfico de barras.

Fuente: 

https://www.kirenz.com/post/2021-12-10-twitter-api-v2-tweepy-and-pandas-in-python/twitter-api-v2-tweepy-and-pandas-in-python/

https://developer.twitter.com/en/docs/twitter-api/tweets/search/integrate/build-a-query
