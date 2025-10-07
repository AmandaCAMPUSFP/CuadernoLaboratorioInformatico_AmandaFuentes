# Objetivo
Practicar la lectura y escritura de ficheros de texto utilizando FileWriter , BufferedWriter ,
FileReader y BufferedReader .
Escribir líneas en un archivo de texto.
Leer el contenido de ese archivo línea por línea.
Visualizar la salida por consola.

# Instrucciones
1. Crea una carpeta llamada datos en la raíz del proyecto.
2. Crea una clase Java llamada GestorFicheroTexto .
3. Implementa los siguientes pasos en el método main :
Escribe 3 líneas de texto en un archivo llamado datos/registro.txt . Lee el contenido de ese
archivo y muéstralo por consola.
Usa BufferedWriter y BufferedReader .

# Código de ejemplo para completar 

``` java
import java.io.*;

public class GestorFicheroTexto {
public static void main(String[] args) {
try {
// Escritura
FileWriter fw = new FileWriter("datos/registro.txt"); BufferedWriter bw = new
BufferedWriter(fw);
bw.write("Registro 1");
bw.newLine();
bw.write("Registro 2");
bw.newLine();
bw.write("Registro 3");
bw.newLine();
bw.flush();
bw.close();
System.out.println("Archivo escrito con éxito.");
// Lectura
FileReader fr = new FileReader("datos/registro.txt"); BufferedReader br = new
BufferedReader(fr);
String linea;
System.out.println("Contenido del archivo:"); while ((linea = br.readLine())
!= null) { System.out.println("> " + linea);
}
br.close();
} catch (IOException e) {
System.out.println("Error: " + e.getMessage()); }
}
}
```


# Código completado

``` java
import java.io.*;
public class GestorFicheroTexto {
public static void main(String[] args) {
try {
// ==== ESCRITURA ====
// Creamos un FileWriter para escribir en datos/registro.txt
// Si la carpeta datos no existe, hay que crearla antes
File carpeta = new File("datos");
if (!carpeta.exists()) {
carpeta.mkdirs();
}
FileWriter fw = new FileWriter("datos/registro.txt");
BufferedWriter bw = new BufferedWriter(fw);
// Escribimos 3 líneas en el archivo
bw.write("Registro 1");
bw.newLine(); // Salto de línea
bw.write("Registro 2");

bw.newLine();
bw.write("Registro 3");
bw.newLine();
// Guardamos los datos en disco y cerramos
bw.flush();
bw.close();
System.out.println("Archivo escrito con éxito.");
// ==== LECTURA ====
// Ahora leemos el archivo línea a línea
FileReader fr = new FileReader("datos/registro.txt");
BufferedReader br = new BufferedReader(fr);
String linea;
System.out.println("Contenido del archivo:");
while ((linea = br.readLine()) != null) {
System.out.println("> " + linea);
}
br.close();
} catch (IOException e) {
System.out.println("Error: " + e.getMessage());
}
}
}
```

