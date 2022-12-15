# HTML

HTML es un lenguaje de etiquetas usado para construir la estructura de un documento web. Su nombre significa HyperText Markup Language. Ahora veremos algunos conceptos en los que quisiera ahondar un poco.

**HTML Doctype**
La declaración doctype nos dice que version de HTML vamos a ejecutar en el browser, las mas reciente es HTML5

**WHATWG** es un grupo de trabajo que define los estándares de HTML para mejorar ante las necesidades del usuario.


## Custom Data Attributes

Son atributos de HTML que son declarados como `data-*` y sirven para guardar cierta información en los tags. Se debe tener en cuenta que en estos no se debe guardar información sensible ya que estos pueden ser modificados fácilmente. Los CDA deben ser siempre de tipo string, y su nombre no debe llevar mayúsculas, un ejemplo de estos puede ser:

```html
<span class="message" data-message-id="3" data-message-type="info" />
```

Para acceder a estos se puede hacer por estos medios:

- Con CSS: Se puede acceder por medio de los selectores de atributos, asi: 
  ```css
  span.message[data-message-type='info'] {
    background-color: blue;
  }
  ```

- Con Javascript: Se pueden acceder de dos formas diferentes, la primera es a traves de la función getAttribute, así:
  ```js
  const message = document.querySelector(".message")
  const messageId = message.getAttribute("data-message-id")
  ```
  Y la segunda es por medio de la propiedad dataset de javascript. Al utilizar esta propiedad, se debe tomar en cuenta que se elimina el `data-*` y la propiedad se convierte a camelCase, veámoslo:
  ```js
  const message = document.querySelector(".message")
  
  message.dataset.messageId
  message.dataset.messageType
  ```

## Accesibilidad

La accesibilidad significa que cualquier usuario puede usar una página web, sin importar que este tenga algo tipo de discapacidad física, mental o cognitiva. También se extiende a otros grupos de usuarios, por ejemplo aquellos que navegan desde dispositivos móviles o que tienen una conexión a internet lenta. Cuando se mejora la accesibilidad, se mejoran también otras cosas como lo puede ser el SEO, la legibilidad del código, se hace fácil de mantener y de entender, y si usamos bien los elementos que nos provee HTML nuestro código ya va a tener buena accesibilidad.

Una de las cosas que se debe de tener en cuenta para mantener la accesibilidad es escribir código HTML semánticamente correcto, esto significa que se deben usar los tags adecuados para lo que están hechos. Por ejemplo, usar los tags de estructura como lo son `<header>`, `<section>`, `<article>`, `<summary>`, `<footer>` y entre otros. Igualmente con los tags de acciones, por ejemplo botones, campos de formularios, deben er bien utilizados para que las herramientas de accesibilidad puedan leerlos e interpretarlos. 

Además de esto, es muy importante darle significado a los labels que usamos, por ejemplo: Para el label de un link, un texto “haz clic aquí” no es significativo, en cambio “Haz clic aquí para saber mas sobre accesibilidad”, tiene significado y le va a ayudar a un usuario a saber que funcionalidad tiene ese botón. Igualmente, el tag `<label>` es super importante para los formularios, ya que este le dan contexto de la info que tiene que llenar en el campo.

Para las tablas, tenemos tags que nos sirven para diferenciar entre las columnas “titulo” (`<th>`), las columnas “body” (`<tr>`) y el caption (`<caption>`).

### Texto alternativo
Para los archivos multimedia, la accesibilidad puede ser un poco más complicada, pero existen alternativas que nos pueden ayudar. Por ejemplo, para una imagen, podemos usar el atributo `alt` para añadir un texto alternativo, la propiedad `title` para añadir un titulo (se puede ver pasando haciendo hover), y la propiedad `aria-labelledby` para enlazarlo a un texto mostrado que tenga una descripción de la imagen, tal cual como este [ejemplo de la MDN](https://mdn.github.io/learning-area/accessibility/html/accessible-image.html). Si tenemos una imagen que es meramente decorativa y no queremos que el lector lea la URL completa, debemos agregar el atributo alt vacío o utilizar el atributo `role=“presentation”`.

La MDN también nos provee este [recurso para practicar accesibilidad](https://developer.mozilla.org/en-US/docs/Learn/Accessibility/Test_your_skills:_HTML_accessibility).

  
## Meta Tags

Sus atributos son:
- name
- charset
- content
- http-equiv
- viewport: Es lo que permite controlar cómo se va a mostrar la pagina, y entre otras cosas controlar los factores de esto, como zoom y width.

## Tipos de storage
**Local storage:** La data queda guardada en el browser aunque se cierre, esto significa que para ser eliminada tiene que ser de forma manual.

**Session storage:** Los datos guardados en el session storage son almacenados hasta que el browser es cerrado, en ese momento se borran automáticamente.

## Que es server-sent events
Es una conexión monodireccional que se establece entre el browser y el servidor, para que el browser pueda recibir updates del servidor sin pedirlo explícitamente

**La diferencia entre SSE y WebSockets** es que el SSE es monodireccional y los WebSockets son bidireccionales.

## Quirks mode and standards mode
La declaración DOCTYPE es lo que define en qué modo se va a tratar la página, este siempre DEBE de ir al principio del documento.

**Quirks mode:** Es una estrategia usada por los navegadores para preservar la compatibilidad con las paginas anteriores al estándar W3C.

**Almost Standard Mode:** Este modo renderiza la aplicación como en “full standard” con la única diferencia que las cell-tables las renderiza en modo quirk.

**Full Standard Mode:** En este modo se renderiza el documento con todos los estándares definidos por la W3C. Casi todos los browsers modernos usan este modo, es muy importante usar la declaración DOCTYPE de HTML5 para que el browser pueda interpretar bien el documento.
