# Grep para Hackers


El comando `grep` es una herramienta de búsqueda de texto que se utiliza en sistemas operativos Unix, Linux y macOS.
Su nombre proviene de "Global Regular Expression Print" ("Impresión global de expresiones regulares", en español).

La función principal de `grep` es buscar patrones de texto dentro de uno o varios archivos. Los patrones se definen
mediante expresiones regulares, que son secuencias de caracteres que describen un conjunto de cadenas de texto.

`grep` recorre línea por línea los archivos especificados y devuelve las líneas que contienen el patrón buscado.
También puede mostrar la línea anterior o posterior a la que contiene el patrón, contar el número de líneas que 
contienen el patrón, entre otras funciones.

Acontinuacion vamos a ver con distintos ejemplos como puedes emplear grep en tu diario dia a dia como Hacker.

### Obteniendo urls que comienzen con https:// http://

``` grep -o 'http[s]\?://[a-zA-Z0-9\-\.]\+\.[a-zA-Z]\{2,\}\(:[0-9]\+\)\?[^[:space:]]\+'  ``` 

### Obteniendo urls que comienzen con www. y no con http:/https:

``` grep -o 'www\.[a-zA-Z0-9\-\.]\+\.[a-zA-Z]\{2,\}\(:[0-9]\+\)\?[^[:space:]]\+' ```


### Obteniendo IPs (IPv4) 

```grep -oE "\b([0-9]{1,3}\.){3}[0-9]{1,3}\b" ```


### Obteniendo IPs IPv6

```grep -oE "([0-9a-fA-F]{1,4}:){7}[0-9a-fA-F]{1,4}"```


### Obteniendo direcciones que tengan el formato "usuario@gmail.com"

```grep -oE ':alnum:]_]+@[[:alnum:]_]+\.[[:alpha:{2,4}' ```

### Obteniendo direcciones que incluyan subdominios y tengan un fomato mas complejo

```grep -oE ':alnum:]_]+@[[:alnum:]_]+\.[[:alpha:{2,4}(\.:alpha:{2,4})+'```


### Buscando buscando palabras claves dentro de directorios de manera recursiva

```grep -r "password" /ruta/al/directorio```


### Buscando palabra clave dentro de un fichero individual

```grep -i "password" index.php```


# Ejemplos de uso


### Puedes usarlo para obtener todas las URLs de un sitio Web

```curl -s https://target.com | grep -o 'http[s]\?://[a-zA-Z0-9\-\.]\+\.[a-zA-Z]\{2,\}\(:[0-9]\+\)\?[^[:space:]]\+' | cut -d '/' -f 3 | tr -d '">' | uniq -u```

### Puedes obtener urls de ficheros binarios

```string <fichero binario> | grep 'http[s]\?://[a-zA-Z0-9\-\.]\+\.[a-zA-Z]\{2,\}\(:[0-9]\+\)\?[^[:space:]]\+' ``` 

### Puedes usar grep para la recoleccion Emails de un fichero sql u otros ficheros.

``` cat db.sql | grep -oE ':alnum:]_]+@[[:alnum:]_]+\.[[:alpha:{2,4}(\.:alpha:{2,4})+' | uniq -u```


