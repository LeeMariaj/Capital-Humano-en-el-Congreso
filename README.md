# Capital Humano en el Cogreso
María José Lee - 24 de noviembre, 2021

## Descripción y Motivación

## Metodos Usados
- **Scraping** 
  - La información de los congresistas se encuentra distribuida en la página del API de Congreso Visible a lo largo de 30 paginas, comenzando por la siguiente página: https://congresovisible.uniandes.edu.co/api/apis/congresistas/
    - Fue necesario usar esta API en la medida en que la página oficial de Congreso Visible solo permitía extraer información de 29 congresistas.
  - Para extarer la información se genero un codigo que modificaba el final del link anteriormente mencionado a traves de un loop, de manera que se pudiese descargar el texto de las 30 páginas y guardarlo todo en una misma variable.
  - Adicionalmente, entre la información dsiponible para cada congresista en la API de Congreso Visible, estaba el link de la página personal asociada a cada uno, de donde se recogieron pedazos de información adicional.
    - Para esto fue necesario usar un loop que guardase temporalmente el contendio de la página de cada congresista, extrajese los datos solicitados, y despues reescribiese esa variable con el contenido del siguiente congresista.
    - Esto fue necesario en la medida en que descargar y guardar la información de la página de cada congresista implicaba demasiado poder de procesamiento, sin mencionar el peso exagerado del documento final.

- **Extracción de la Información** <br>
  - Para el texto recogido de la API de Congreso Visible
    - Se comienza por reemplazar los codigos especiales que hay en las palabras con tildes, por la letra con tilde. Esto para facilitar no solo la extracción de los datos, sino tambien su manejo.
     - Posterior a modificar el codigo recogido, se procede a extraer por medio de listas, loops y regex la información concerniente al nombre de los congresistas, el apellido, si trabaja en el senado o como representante, el género y el partido político al que pertenece.

  - Para el texto de las páginas inidividuales de cada congresista 
    - jdjdd
## Resultados
