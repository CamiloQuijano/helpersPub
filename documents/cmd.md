﻿[`Volver`](../index.html)

# Windows

## windows+r 
###### Tags: `cmd` `comandos` `temp` `prefetch` `eventvwr` `limpieza`

```bash
	appwiz.cpl          Programas y características
	msconfig            Configuraciones del sistema
	regedit             Editor de registros
```

Limpieza de archivos temporales
```bash	
	%temp%      	Temporales
	TEMP        	Temporales
	prefetch    	Temporales
	eventvwr    	Visualizados de eventos
```


## CMD
###### Tags: `cmd` `cd` `ipconfig` `comandos`

Comandos básicos 

```bash
	d: (enter)                  	Cambiar de unidad de disco duro 
	cd ..                       	Volver nive anterior 
	cd folder1/folder2          	Moverse entre directorios
	cd ../../folder3            	Moverse entre directorios (Volver directorios)
	diskmgmt.msc                	Administrador de Discos
	ipconfig /flushdns          	Borrar cache DNS PC 
	gpupdate /force             	Actualizar Directivas
	wmic os get osarchitecture  	Versión de Windows,  Indica si el sistema es de 32 o 64 Bits 
	move C:\foldera C:\folderb  	Mover el contenido de una carpeta a otra 
	md data                     	Crear una carpeta en windows 
```

### Realizar busqueda por consola
```bash
	* /S (subniveles) 
	* /M (Muestra solo el nombre del archivo en donde se encuentra la coincidencia) 
	findstr /S /M "textoAConsultar" src/* 
```

### Mover archivos entre carpetas x consola
```bash
	robocopy /s /R:3 carpetaorigen carpetadestino
```

## netstat
###### Tags: `cmd` `netstat` `taskkill` `port`

```bash
	tasklist
	netstat -oan                    // Listado de servicios
    netstat -ano | findstr 80       // Consultar servicios con uso a un puesto especifico
	Taskkill /F /IM chrome.exe
	Taskkill /PID 364 /F
```

## Revisar nombre de un servidor en dominio
###### Tags: `cmd` `nslookup`

Condiciones:  
Se debe encontrar dentro del mismo dominio

```bash
	nslookup
	>> 192.168.100.31
	
	Name:    libra.dominio.local
	Address:  192.168.100.30
```

## Gulp inicio-singes
```bash
	node 8.9.3                  // Versión necesaria NODE
	npm install gulp-cli -g     // Instalar gulp CLI a nivel global
	npm install gulp            // Instalar gulp en proyecto
	npm install gulp-plumber    // Instalar dependencia gulp
	npm install gulp-sass       // Instalar dependencia gulp
	
	// Para Singes es necesario ubicarse en la carpeta resources
	gulp scripts                // Ejecutar scripts gulp
	gulp styles                 // Ejecutar estilos gulp
```

## Guardar listado de archivos de una carpeta a un archivo
```bash
	dir /b /o f:\Peliculas\Series > f:\series.txt
```
- /s -> Incluye ruta y nombre de archivos de subcarpetas
- /o -> Nombre de archivos de carpeta principal sin ruta 
- /b -> Sin b incluye fecha hora 


## FINDSTR 
- /S -> Recursivo, de la carpeta a todos los subniveles 
- /M -> Imprime nombre de archivo
- /N -> Imprime nombre de archivo y linea de coincidencia 
- /C:"búqueda hola" -> Búsqueda de una palabra exacta 
- "hola mundo" -> Búsqueda alternativa, o una o la otra palabra 