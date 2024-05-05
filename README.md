# Hackathon ```<code/>```
## Enunciado
El Ministerio de Agricultura y Ganadería en conjunto con la Dirección de meteorología e hidrología del Paraguay están trabajando para encontrar una solución a las perdidas de cultivos ocasionadas por el cambio abrupto del clima de la región. Es por esto, que se pone en contacto con ustedes para desarrollar una página que permita alertar a los productores sobre posibles fenómenos meteorológico que perjudique la producción. 

## Requerimientos funcionales
**Descripción General:** Desarrollar y diseñar una página web que permita mostrar a los productores el pronostico extendido de los departamentos estudiados en el país (Central, Boquerón, Caaguazú). La 

## Set de datos
Se provee un API REST público donde se detalla el pronostico extendido de los próximos 3 días, incluyendo además, el día que se tomó la medición, correspondiente a cada departamento estudiado (Central, Caaguazú, Boquerón) bajo la URL https://xxxx.xxxx/xxx. 
Cada equipo deberá consumir estos datos y utilizarlo dentro de la aplicación.

### Ejemplo de respuesta de API en formato JSON
```
{
    "cod": "200",
    "message": 0,
    "departamento_list": [
        {
            "id": 11,
            "nombre": "Central",
            "población": 1866562,
            "coord": {
                "lat": -25.380646,
                "lon": -57.602323
            },
            "pronostico_extendido_list": [
                {
                    "fecha_hora_txt": "2024-05-11 06:00:00",
                    "dia_text": "hoy",
                    "main": {
                        "temp": 21.34,
                        "temp_min": 21.34,
                        "temp_max": 30.24,
                        "humedad": 100
                    },
                    "clima": [
                        {
                            "id": 1,
                            "tipo": "lluvia",
                            "description": "lluvia"
                        }
                    ],
                    "viento": {
                        "velocidad": 40.05,
                        "direccion": 66
                    },
                    "visibilidad": 5000,
                    "probabilidad_precipitacion": 0.99,
                    "lluvia": {
                        "volumen_1h": 0.4
                    }
                },
		{
			...
		}
            ]
        },
        {
            "id": 12,
            "nombre": "Boqueron",
            "población": 68595,
            "coord": {
                "lat": -22.125705,
                "lon": -60.737641
            },
            "pronostico_extendido_list": [
                {
			...
		}
	    ]
        },
        {
            "id": 13,
            "nombre": "Caaguazú",
            "población": 131143,
            "coord": {
                "lat": -25.460147,
                "lon": -56.026884
            },
            "pronostico_extendido_list": [
                {
			...
		}
	    ]
        }
    ]
}
```

### Campos de respuesta API en formato JSON

 - `cod` Parámetro interno
 - `message`Parámetro interno
 - `departamento_list`
	 - `id`Identificador del departamento
	 - `nombre`Nombre del departamento
	 - `poblacion`Población del departamento
	 - `coord`
		 - `lat`Ubicación geográfica, latitud
		 - `lon`Ubicación geográfica, longitud
	 - `pronostico_extendido_list`
		 - `fecha_hora_txt`fecha y hora del momento que se tomó las medidas en formato texto
		 - `dia_text`el día en formato texto. Puede tener como valor **hoy** que hace relación al día de la medición
	         - `main`
		 	- `temp`Temperatura. Unidad predeterminada, medidas en grados celsius
		 	- `temp_min`Temperatura mínima en el momento del cálculo, medidas en grados celsius
		 	- `temp_max`Temperatura máxima en el momento del cálculo, medidas en grados celsius
		 	- `humedad`Medidas en porcentaje (%)
	     	 - `clima`
		 	- `id`Identificador del clima
		 	- `tipo` Posibles valores (nublado_total, soleado, lluvia, tormenta_electrica, nublado_parcialemente, nieve)
		 	- `descripcion` Descripción del tipo de clima
	         - `viento`
		 	- `velocidad` Velocidad del viento. Medidos en kilometros/hora
		 	- `direccion` Dirección del viento. Medidos en grados
	       	 - `visibilidad` Visibilidad media. Medidos en metros.
	       	 - `probabilidad_precipitacion` Los valores del parámetro varían entre 0 y 1, donde 0 es igual al 0%, 1 es igual al 100%
	       	 - `lluvia`
		 	- `volumen_1h` Volumen de lluvia de la última hora, medida en milimetros
