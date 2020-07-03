
**Antes de crear el mapa**
Antes de crear el mapa tenemos que importar el .js del api.

    <script src="https://maps.googleapis.com/maps/api/js?key=LLAVE_API_AQUI&callback=funcionMapa"></script>
El script solicita que llenemos el "key" con nuestra llave del gmaps. Y a su vez también tenemos que llenar el callback. El callback llamará a esa función para inicializar el mapa cuando el script haya cargado.

El primer paso para crear un mapa con el API de GMaps, es el de crear una instancia de la clase “[google.maps.Map](https://developers.google.com/maps/documentation/javascript/reference/map#Map)”. Esta clase tiene un constructor que se ve de la siguiente forma:


**Código JavaScript Para Crear el Mapa**

    <script> Map(mapDiv[, opts]) </script>

 - mapDiv: Este será el div dentro del cual se encontrará el mapa.
   
  - opts: Son la opciones que podemos configurar para el mapa. Entre las
   más utilizadas están: 
   - [MapTypeId](https://developers.google.com/maps/documentation/javascript/reference/map#MapTypeId)
 - [Zoom](https://developers.google.com/maps/documentation/javascript/reference/map#MapOptions.zoom)    
  - [Scrollwheel](https://developers.google.com/maps/documentation/javascript/reference/map#MapOptions.scrollwheel)
  - [Center](https://developers.google.com/maps/documentation/javascript/reference/map#Map.setCenter)

	    <script>
	        var mapProp= {
		        mapTypeId:ROADMAP,
		        center:new google.maps.LatLng(51.508742,-0.120850),
		        zoom:5,
		        scrollwheel: true,
        };
        var map = new google.maps.Map(document.getElementById("googleMap"),mapProp);
        } 
    </script>

**Crear Marcador Dentro del Mapa**

Para la creación del marcador dentro del mapa tenemos que utilizar el constructor [google.maps.Marker](https://developers.google.com/maps/documentation/javascript/reference/marker#Marker.constructor) Marker([opts]);
  - opts: Son la opciones que podemos configurar para el marcador. Entre las
   más utilizadas se encuentran: 
	- [clickable](https://developers.google.com/maps/documentation/javascript/reference/marker#MarkerOptions.clickable)

	- [draggable](https://developers.google.com/maps/documentation/javascript/reference/marker#MarkerOptions.draggable)

	- [icon](https://developers.google.com/maps/documentation/javascript/reference/marker#MarkerOptions.icon)

	- [label](https://developers.google.com/maps/documentation/javascript/reference/marker#MarkerOptions.label)

	- [map](https://developers.google.com/maps/documentation/javascript/reference/marker#MarkerOptions.map)

	- [position](https://developers.google.com/maps/documentation/javascript/reference/marker#MarkerOptions.position)

	- [shape](https://developers.google.com/maps/documentation/javascript/reference/marker#MarkerOptions.shape)

	- [title](https://developers.google.com/maps/documentation/javascript/reference/marker#MarkerOptions.title)

	- [visible](https://developers.google.com/maps/documentation/javascript/reference/marker#MarkerOptions.visible)

   **Código para generar marcador**
   
    <script>
    var marker = new google.maps.Marker({position: map.getCenter(), map: map});
	/* El map hace referencia a la variable creada anteriormente */
    </script>

Ejemplo para crear un circulo con un radio de 1km:

    <script>
    var circulo = new google.maps.Circle({
	  center:new google.maps.LatLng(51.508742,-0.120850),
	  radius:1000, /*Radio es en metros*/
	  fillColor:"#FF0000", /*Color rojo*/
	  fillOpacity:0.4,
	  map: map
	});
    </script>
Podemos crear una "InfoWindow" para un marcador. Una InfoWindow es una ventana que se abre para un marcador. Esta puede contener html.
Ej:

	<script>
    var infowindow = new google.maps.InfoWindow({
	  content:"Contenido de la infowindow"
	});
	infowindow.open(map,marker);
	//El código anterior abrirá la infowindow sin acción previa.
    </script>

   **Eventos**
   GMaps ofrece eventos o también llamados "triggers/listeners" para realizar ciertos eventos cuando queremos.

Por ejemplo, el evento de cuando se presiona sobre un marcador. Con este evento podemos hacer que el infowindow creado anterior se abra cada vez que el usuario presiona sobre el marcador.

    <script>
    google.maps.event.addListener(marker, 'click', function() {
      infowindow.open(map,marker);
    });
    </script>

