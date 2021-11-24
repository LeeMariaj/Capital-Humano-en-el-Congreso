# Capital Humano en el Cogreso
María José Lee - 24 de noviembre, 2021

## Descripción y Motivación
El Departamento de Ciencias Políticas de la Universidad de los Andes creo el programa de Congreso Visible en 1998 con la intención de generar una fuente de información sobre lo que estaba sucediendo en el Congreso, alternativa a los medios de comunicación tradicionales. Para este proyecto se analizo la información referente a todos los congresistas del periodo 2018-2022.

Este proyecto surge con la intención de generar un primer acercaminto a la dinámica y composición del Congreso, al tiempo que se respondían algunas preguntas puntuales:
- ¿Cual es la composición de género en el Congreso?
- ¿Cómo es la distribución de edades en el Congreso?
- ¿De que partes del país tienden a salir los congresistas?
- ¿Hay zonas sobre-representadas o sub-resentadas?
- ¿Qué tan bien preparados academicamente están los congresistas?, ¿De que manera afecta esto su desempeño en el Congreso?
- ¿Como votan los partidos al interior del congreso?
- ¿Hay una dominancia clara en la cantidad de votos y proyectos de ley por parte de los partidos afines al gobierno, o de otro tipos de actores?

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
    - Se utilizo un loop, que junto con regex y listas, guardaba el codigo en una variable, extraía la información que se quería del congresista, la guardaba, y despues sobreescribia el codigo del congresita con el del siguiente y volvía a repetir el ciclo.
    - Durante esta etapa se recogio información respecto al Nivel Educativo, el lugar de nacimiento, la fecha de nacimiento, número de proyectos de ley de los que ha sido autor, cantidad de veces que ha votado y su profesión.

- **Manejo, Almacenamiento y Limpieza** <br>
  - Se utilizaron listas, loops y regex para almacenar y limpiar la información recolectada, asi como para generar nuevas variables con base en ella (Nombre Completo, Departamento de Nacimiento, Edad y Años de Educación)
  - Se utilizo la librería pandas para generar un DataFrame en donde poder consolidar toda la información referente a cada congresista.
  - Posteriormente se separo este Dataframe en dos, dependiendo de si la persona era congresista o representante. Estos serían los dos databases que serían descargados.

- **Gráficas** <br>
  - Para gráficar los datos recolectados se utilizo el programa Tableau.
  - Aqui se hizo usa de las diferentes maneras en las que se podía organizar la información, asi como los toques extras que permite agregar.
  - Las gráficas realizadas terminaron dividiendose en tres grandes temas:
    - **Generales:** Aquellas que hablaban de la composición del Congreso en terminos generales.
    - **De Educación:** Aquellas que estuviesen relacionadas a la educación de los congresistas, y las diferencias dependiendo de las diferentes clasificaciones.
    - **Por Partido:** Aquellas que mostrasen el comportamiento que tenían los distintos partidos dentro del congreso.

## Resultados
Todas las gráficas fueron realizadas por medio de Tableau, y pueden ser consultadas en los documentos adjuntados.
- Cantidad de personas identificados como Representantes: 181
- Cantidad de personas identificados como Senadores: 118

### Generales
Con las que se pretende entender mejor las características de las personas que componen el Congreso.

- **Piramide Poblacional**

![Piramide Poblacional - Representantes](https://user-images.githubusercontent.com/92488913/143255104-0a8d80fb-63f5-47f1-ab66-ecab89cb44e3.png)
![Piramide Poblacional - Senadores](https://user-images.githubusercontent.com/92488913/143255113-ffea3570-fc74-44a6-8460-76c5bc4d4c14.png)

- **Distribución del Departamento de Nacimiento**

![image](https://user-images.githubusercontent.com/92488913/143316859-93fd9292-062a-4ad8-a233-8acdb4056273.png)![image](https://user-images.githubusercontent.com/92488913/143316877-06b017d4-ee62-4159-8096-edfb431c9002.png)


- **Distribución de Profesiones**

![Dist  Profesiones - Representantes](https://user-images.githubusercontent.com/92488913/143250183-4edb08a4-4a5e-4bc6-b137-b6e48f7bf76b.png)
![Dist  Profesiones - Senadores](https://user-images.githubusercontent.com/92488913/143250105-8e0cea5a-c357-45e0-b9da-278cce3a32d5.png)


### Por Partido

- **Autoría de Proyectos de Ley**
![image](https://user-images.githubusercontent.com/92488913/143278933-fd48ee37-f950-40c8-862d-d7bf1f6cb53c.png)
![image](https://user-images.githubusercontent.com/92488913/143278954-eec92fd2-dfa4-48fa-833a-d91bcc7e6882.png)

- **Votos por Proyectos de Ley**
![image](https://user-images.githubusercontent.com/92488913/143280193-3904225a-a509-4b77-921c-45cbbec6f363.png)
![image](https://user-images.githubusercontent.com/92488913/143280224-d2f0f1ae-7a1b-4440-bb7d-99e002b66e9b.png)


### Educación

- **Distribución del Nivel Educativo**
![Nivel Educativo General - Representantes](https://user-images.githubusercontent.com/92488913/143280871-067e9355-d60e-447b-872a-a8beaf5b7613.png)
![Nivel Educativo General - Senadores](https://user-images.githubusercontent.com/92488913/143280770-fe11e98e-d77f-4b15-a013-df5ed5fd3d27.png)

- **Contraste de Años de Educación Estimados entre Hombres y Mujeres**
![image](https://user-images.githubusercontent.com/92488913/143281473-a28bc08a-422a-4f1c-bef8-bfc0b1939069.png)
![image](https://user-images.githubusercontent.com/92488913/143281518-3e53a5c1-cf1b-4f5a-b61e-ff239a5ccea5.png)

- **Votos promedio por nivel educativo**
![image](https://user-images.githubusercontent.com/92488913/143313424-251a7c74-63a6-47ae-a8c2-c7f3df5583b1.png)
![image](https://user-images.githubusercontent.com/92488913/143313175-d4089b62-e4df-43a7-9d0d-7b4fe5873263.png)

## Posibles Continuaciones
- Entender porque ciertos niveles de estudios y partidos no aparece como que estén efectivamente votando.
- Entender porque las mujeres senadoras tienden a estar mejor preparadas acádmicamente que sus pares hombres, al tiempo que se tiene el efecto opuesto en la Camara de Representantes.
- Generar una red adentro de los partidos, y entender el impacto que tener mas conexiones en la manera y frecuencia de los votos de los congresistas.
- Entender porque hay tan baja representación de las regiones de Oniroquia y Amazonía entre los senadores.
