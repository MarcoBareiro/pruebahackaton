# Ejemplo de respuesta de API en formato JSON
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
                    "fecha_hora_txt": "2022-08-30 16:00:00",
                    "dia_text": "hoy",
                    "main": {
                        "temp": 296.34,
                        "temp_min": 296.34,
                        "temp_max": 298.24,
                        "humedad": 50
                    },
                    "clima": [
                        {
                            "id": 1,
                            "tipo": "Rain",
                            "description": "light rain"
                        }
                    ],
                    "viento": {
                        "velocidad": 1.06,
                        "direccion": 66
                    },
                    "visibilidad": 10000,
                    "probabilidad_precipitacion": 0.32,
                    "lluvia": {
                        "volumen_1h": 0.13
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

# Campos de respuesta API en formato JSON

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
         - `velocidad` Velocidad del viento. Medidos en metros/seg
         - `direccion` Dirección del viento. Medidos en grados
       - `visibilidad` Visibilidad media. Medidos en metros.
       - `probabilidad_precipitacion` Los valores del parámetro varían entre 0 y 1, donde 0 es igual al 0%, 1 es igual al 100%
       - `lluvia`
         - `volumen_1h` Volumen de lluvia de la última hora, medida en milimetros
