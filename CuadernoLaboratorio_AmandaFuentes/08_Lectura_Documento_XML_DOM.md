## Estructura del proyecto

![[Foto2_XML_DOM.png]]
## Código DOMLeerEjemplo

```java
import javax.xml.parsers.*;  
import org.w3c.dom.*;  
import java.io.File;  
  
public class DOMLeerEjemplo {  
    public static void main(String[] args) {  
        try {  
            File archivo = new File("datos/empleados.xml");  
            DocumentBuilderFactory dbf = DocumentBuilderFactory.newInstance();  
            DocumentBuilder db = dbf.newDocumentBuilder();  
            Document doc = db.parse(archivo);  
  
            NodeList lista = doc.getElementsByTagName("empleado");  
  
            for (int i = 0; i < lista.getLength(); i++) {  
                Element emp = (Element) lista.item(i);  
                String id = emp.getAttribute("id");  
                String nombre = emp.getElementsByTagName("nombre").item(0).getTextContent();  
                String puesto = emp.getElementsByTagName("puesto").item(0).getTextContent();  
                System.out.println("ID: " + id + " | Nombre: " + nombre + " | Puesto: " + puesto);  
            }  
  
        } catch (Exception e) {  
            System.out.println("Error al leer: " + e.getMessage());  
        }  
    }  
}
```

## Resultado en consola

![[Foto1_XML_DOM.png]]

## Código DOMEscribirEjemplo

```java
import javax.xml.parsers.*;  
import javax.xml.transform.*;  
import javax.xml.transform.dom.DOMSource;  
import javax.xml.transform.stream.StreamResult;  
import org.w3c.dom.*;  
import java.io.File;  
  
public class DOMEscribirEjemplo {  
    public static void main(String[] args) {  
        try {  
            DocumentBuilderFactory dbf = DocumentBuilderFactory.newInstance();  
            DocumentBuilder db = dbf.newDocumentBuilder();  
            Document doc = db.newDocument();  
  
            Element root = doc.createElement("empleados");  
            doc.appendChild(root);  
  
            Element emp = doc.createElement("empleado");  
            emp.setAttribute("id", "E001");  
  
            Element nombre = doc.createElement("nombre");  
            nombre.appendChild(doc.createTextNode("Ana Torres"));  
            emp.appendChild(nombre);  
  
            Element puesto = doc.createElement("puesto");  
            puesto.appendChild(doc.createTextNode("Desarrolladora"));  
            emp.appendChild(puesto);  
  
            root.appendChild(emp);  
  
            TransformerFactory tf = TransformerFactory.newInstance();  
            Transformer transformer = tf.newTransformer();  
            DOMSource source = new DOMSource(doc);  
            StreamResult result = new StreamResult(new File("datos/empleados_generado.xml"));  
            transformer.transform(source, result);  
  
            System.out.println("Archivo XML generado correctamente.");  
  
        } catch (Exception e) {  
            System.out.println("Error al escribir: " + e.getMessage());  
        }  
    }  
}
```

## Resultado en consola

![[Foto4_XML_DOM.png]]

Se genera un archivo xml solo:
![[Foto3_XML_DOM.png]]