
# Manejo de archivos en Java

En Java, puedes manejar archivos usando la clase File ubicada en el paquete java.io:
```java
import java.io.File;
```
Para empezar a manejar un archivo, especifica el nombre del archivo o la ruta para crear un objeto File:
```java
File dataFile = new File("data.txt");
```
En la lección anterior, vimos cómo crear un objeto File a partir de cualquier archivo. Ahora veamos algunas operaciones básicas:
```java
File dataFile = new File("data.txt");
System.out.println("Nombre del archivo: " + dataFile.getName());
System.out.println("Ruta absoluta: " + dataFile.getAbsolutePath());
System.out.println("Tamaño del archivo en bytes: " + dataFile.length());
```
El código anterior imprime el nombre, la ruta absoluta y el tamaño del archivo data.txt.

**Leer**

Una forma de leer el contenido de un archivo en Java es utilizando la clase Scanner, que también se usa para obtener entrada:
```java
try {
  File dataFile = new File("data.txt");
  Scanner scanner = new Scanner(dataFile);
  while (scanner.hasNextLine()) {
    String data = scanner.nextLine();
    System.out.println(data);
  }
  scanner.close();
} catch (FileNotFoundException e) {
  System.out.println("Ocurrió un error.");
  e.printStackTrace();
}
```
El código anterior lee e imprime cada línea del archivo "data.txt".
Ten en cuenta que debes envolver el código con try-catch y manejar la excepción `FileNotFoundException`.

**Escribir**

Para escribir en un archivo en Java, podemos usar la clase FileWriter:
```java
try {
  FileWriter writer = new FileWriter("data.txt");
  writer.write("¡Este es el nuevo contenido del archivo data.txt!");
  writer.close();
} catch (IOException e) {
  System.out.println("Ocurrió un error.");
  e.printStackTrace();
}
```
El código anterior escribe algún texto en el archivo "data.txt", nota que debes manejar la excepción IOException.

Por defecto, el texto sobrescribe cualquier texto existente, si deseas agregar el texto al contenido ya existente del archivo, usa esto:
```java
FileWriter writer = new FileWriter("data.txt", true);
```
Nota el true como el segundo argumento del constructor FileWriter.

**Crear**

Para crear un archivo en Java, usa el constructor de la clase File con el nombre de archivo deseado y luego ejecuta el método createNewFile(). El método devolverá true si el archivo se creó con éxito, o false si el archivo ya existe:
```java
try {
  File file = new File("data.txt");
  if (file.createNewFile()) {
    System.out.println("Archivo creado: " + file.getName());
  } else {
    System.out.println("El archivo ya existe.");
  }
} catch (IOException e) {
  System.out.println("Ocurrió un error.");
  e.printStackTrace();
}
```
El código anterior crea el archivo llamado "data.txt", nota que debes manejar la excepción IOException.

**Eliminar**

Por último, para eliminar un archivo en Java, usa el método delete() de la clase File. El método devolverá true si el archivo se eliminó con éxito, o false si falló:
```java
File file = new File("data.txt"); 
if (file.delete()) { 
    System.out.println("¡Archivo eliminado!");
} else {
    System.out.println("No se pudo eliminar el archivo.");
}
```
El código anterior intenta eliminar el archivo llamado "data.txt".
