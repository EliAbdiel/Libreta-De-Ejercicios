
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

