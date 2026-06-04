[`Volver`](../index.html)

# Excel

## Cambiar formato texto
###### Tags: `excel` `mayusc` `minusc` `nompopio`

```js
	=MAYUSC(Celda)      	// Pasar a mayúscula.            	Salida: gOOgle - GOOGLE 
	=MINUSC(Celda)      	// Pasar a minúscula.            	Salida: gOOgle - google
	=NOMPROPIO(Celda)   	// Pasar formato nombre Propio   	Salida: gOOgle - Google
```

## Cambiar formato fechas - pasar a texto
###### Tags: `excel` `texto`

```js
	FECHA = '1/01/2023';
	=TEXTO(FECHA;"yyyy")            	// Año              	Salida: 2022
	=TEXTO(FECHA;"mm")              	// Periodo          	Salida: 01
	=TEXTO(FECHA;"mmmm")            	// Mes              	Salida: enero
	=TEXTO(FECHA;"aaaa")            	// Día              	Salida: viernes
	=TEXTO(FECHA;"dd/mm/yyyy")      	// Formato fecha    	Salida: 01/01/2022
	=TEXTO(FECHA;"yyyy-mm-dd")      	// Formato fecha    	Salida: 2022-08-12
	=TEXTO(FECHA;"yy-mm-dd")        	// Formato fecha    	Salida: 22-08-12
	=TEXTO(FECHA;"dd/mm/yyyy HH:MM")	// Formato fecha    	Salida: 22/08/12 05:10
	=HOY()                          	// Fecha actual     	Salida: 2/01/2022
```


## Sumarle meses a una fecha
###### Tags: `excel` `FECHA.MES`

```js
	FECHA = '15/05/2025';
	=FECHA.MES(FECHA;3)				    // 15/08/2025
	=FECHA.MES(FECHA;12)			    // 15/05/2026
```


## Buscar caracter en especifico
###### Tags: `excel` `ENCONTRAR`

```js
	=ENCONTRAR(VALOR_A_BUSCAR;CELDA_A_VALIDAR;INICIAR_DESDE_POSICION) 

	B366 = 'HOLA MUNDO DOS'
	=ENCONTRAR(" ";B366)	       // SALIDA 5
	=ENCONTRAR(" ";B366;6)	       // SALIDA 11
```


## Concatenar textos
###### Tags: `excel` `CONCATENAR`

```js
	=CONCATENAR('TEXTO1'; ' | '; 'TEXTO2')    	// TEXTO1 | TEXTO 2
	=CONCATENAR('A'; 'B'; 'C')                	// TEXTO1 | TEXTO 2
```


## Recortar palabras
###### Tags: `excel` `EXTRAE` `substring`

```js
	TEXTO = 'Audifonos Gw 3 Monster'
	=EXTRAE(TEXTO;POSICION_INICIAL;POSICION_FINAL)      // Parametros
	=EXTRAE('Audifonos Gw';1;5)                         // Salida: Audif
	=EXTRAE('Audifonos Gw';1;9)                         // Salida: Audifonos
	=EXTRAE('CALLE 12 NO. 5-20 OF. 111';1;10)           // Salida: CALLE 12 N
```

## Contar condicional
###### Tags: `excel` `CONTAR.SI`

```js
	=CONTAR.SI(F1:F100;">0")
	// Salida: Cuenta solo las celdas que su valor sea mayor a 0
```


## Longitud palabras
###### Tags: `excel` `largo` `length` `tamaño`

```js
	=LARGO('Accesorios')    // Salida: 10
	=LARGO('Igoma')         // Salida: 5
```


## Contar Espacios en celda
###### Tags: `excel` `LARGO` `SUSTITUIR`

```js
	=LARGO(A1)-LARGO(SUSTITUIR(A1;" ";"")) 
	A1 = 'Juan David'                // Salida: 1
	A1 = 'Juan David Perez'          // Salida: 2
```

## Macros

### Macro con validacion de estado

- [`SCRIPT`](excel/Macroconvalidaciondeestado.txt)  


### Envio de mensajes whatsapp masivo
###### Tags: `excel` `whatsapp`

Ejemplo envio mensaje (Directo)
- [`SCRIPT`](excel/direct-EnviarWhatsappMsm.txt) | [`EXCEL`](excel/WhatsappTexto-Directo.xlsm)

Ejemplo envio imagen (Directo)
- [`SCRIPT`](excel/direct-EnviarWhatsImage.txt) | [`EXCEL`](excel/WhatsappImagen-Directo.xlsm)

Ejemplo envio mensaje (Navegacion)
- [`SCRIPT`](excel/navegacion-EnviarWhatsapp.txt) | [`EXCEL`](excel/WhatsappTexto-Navagacion.xlsm)

Ejemplo envio mensaje (Navegacion)
- [`SCRIPT`](excel/navegacion-EnviarWhatsappImg.txt) | [`EXCEL`](excel/WhatsappImagen-Navegacion.xlsm)

Pruebas  
- [`EXCEL`](excel/Pruebas.xlsm)
