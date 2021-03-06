[`Volver`](../index.html)

# PHP

Descargar versiones de PHP  
https://windows.php.net/download/#php-5.4

## Configuaciones - Php.ini 

```php
upload_max_filesize 		 Peso máximo de archivos a subir
post_max_size				Peso máximo de archivos a subir por POST 
```

## Establecer Configuraciones tiempo ejecución memoria limite
```php
	ini_set("max_execution_time", 8500); 						// Mas tiempo para ejecución
	ini_set("memory_limit", "6048M"); 							// Mas memoria
	ini_set('pdo_sqlsrv.client_buffer_max_kb_size','1024288');  // Buffer (pdo_sqlsrv): En Bytes 1024288 == 1GB
	ini_set('sqlsrv.ClientBufferMaxKBSize','1024288');          // Buffer (sqlsrv): En Bytes 1024288 == 1GB
```

## Imprimir variables - arreglos - json
```php
	log_message('error', "response ::: ".json_encode($_POST));  	    // Log de array 
	var_export($array)  												// Imprimir array	
```

## Tipo de peticion get post put
```php
	$_SERVER['REQUEST_METHOD']
	// GET POST PUT 
```

## Acceder a data asignada en ROW
###### Tags: `php` `addi` `input` `post` `data`

Forma de acceder a información por row (caso ADDI)
```php
	$formdata = (array) json_decode(file_get_contents('php://input'), TRUE); 
```

## Redireccionar
```php
	header('Location: index.php');
    die();
```

## Sesion - iniciar - asignar - eliminar 
```php
	session_start(); 
	$_SESSION['accessAuthorization'] = 1; 		// Asignar valor
	echo  $_SESSION['accessAuthorization']; 	// Consultar valor	
	unset($_SESSION['logged_in_user_id']);		// Eliminar sesión
```


### Buscar key en arreglo 
###### Tags: `php` `array` `array_search` `array_column`

Busca un valor determinado en un array y devuelve la primera clave correspondiente en caso de éxito  
A partir de la versión 5.3.0, devuelve **null** si se le pasan parámetros inválidos.

Para búsqueda key en array **uni-dimencional**
```php
	$array = array(0 => 'azul', 1 => 'rojo', 2 => 'verde', 3 => 'rojo');
	$clave = array_search('verde', $array); // $clave = 2;
	$clave = array_search('rojo', $array);  // $clave = 1;
	$clave = array_search('cafe', $array);  // $clave = null;
```

Para búsqueda key en array **by-dimencional**
```php
	
	$userdb = [
		0 => ['uid' => '100', 'name' => 'Sandra Shush',     'url' => 'urlof100' ],
		1 => ['uid' => '101', 'name' => 'Stefanie Mcmohn',  'url' => 'urlof101' ],
		2 => ['uid' => '102', 'name' => 'Camilo Test',  	'url' => 'urlof102' ]
	];
	$key = array_search(101, array_column($userdb, 'uid'));	// $clave = 1;
	$key = array_search(102, array_column($userdb, 'uid'));	// $clave = 2;
```	


### Quitar elementos vacios de un arreglo
###### Tags: `php` `array` `array_filter` 

Eliminará del arreglo null, ceros, string vacios.  
```php
    $flowers = array("Rose", 0, "Hibiscus", "", "Tulip", null, "Sun Flower");
	$salida = array_filter($array);

    // Arreglo filtro aplicado
    array([0] => "Rose", [2] => "Hibiscus", [4] => "Tulip", [6] => "Sun Flower" )
```


### Cantidad de caracteres variable string
###### Tags: `php` `strlen` `longitud` 
```php
	strlen('abcdef');       // 6
```	


### Recortar palabras
###### Tags: `php` `substr` 

```php
	echo substr('abcdef', 1, 3); // bcd 							// Recortar palabras - bcd
	echo substr('abcdef', 0, 4); // abcd							// Recortar palabras - abcd
	echo substr('abcdef', -1, 1); // f  							// Recortar palabras - f
	echo substr("abcdef", 0, -1); // "abcde"						// Recortar palabras - abcde
	echo substr("abcdef", 2, -1); // "cde"  						// Recortar palabras - cde
	echo substr($_SERVER['SERVER_NAME'], 0, 20);					// Recortar palabras - IP hasta 20 caractéres
```	


### Buscar palabra o caracter en variable de texto 
###### Tags: `php` `strpos` 
```php
	echo strpos("I love php, I love php too!","X");		// FALSE
	echo strpos("I love php, I love php too!","php");	// 7
	echo strpos("I love php, I love php too!","I");		// 0
```


### Buscar texto despues de un caractes especifico
###### Tags: `php` `strstr` 
```php
    $email = 'name@example.com';

    // Consultar texto despues de un caracter
    $domain = strstr($email, '@');
    echo $domain; // mostrará @example.com

    // Consultar texto antes de un caracter
    $user = strstr($email, '@', true); // Desde PHP 5.3.0
    echo $user; // mostrará name
```	

### Remplazar texto
###### Tags: `php` `replace` `str_replace`

```php
	$bodytag = str_replace("%body%", "black", "<body text='%body%'>");
	// Produce: <body text='black'>

	$vowels = array("a", "e", "i", "o", "u", "A", "E", "I", "O", "U");
	$onlyconsonants = str_replace($vowels, "", "Hello World of PHP");
	// Produce: Hll Wrld f PHP

	$phrase  = "You should eat fruits, vegetables, and fiber every day.";
	$healthy = array("fruits", "vegetables", "fiber");
	$yummy   = array("pizza", "beer", "ice cream");
	$newphrase = str_replace($healthy, $yummy, $phrase);
	// Produce: You should eat pizza, beer, and ice cream every day
```

## Rellenar palabra con caracteres a la derecha-izquierda str_pad
```php
	$input = "Alien";
	echo str_pad($input, 10);                      // produces "Alien     "
	echo str_pad($input, 10, "-=", STR_PAD_LEFT);  // produces "-=-=-Alien"
	echo str_pad($input, 10, "_", STR_PAD_BOTH);   // produces "__Alien___"
	echo str_pad($input,  6, "___");               // produces "Alien_"
	echo str_pad($input,  3, "*");                 // produces "Alien"
```

## Validar variable boleana
###### Tags: `php` `filter_var` `FILTER_VALIDATE_BOOLEAN`

Validar variable boleana, asi venga en texto true false

```php
	filter_var('on', FILTER_VALIDATE_BOOLEAN);		// true
	filter_var('true', FILTER_VALIDATE_BOOLEAN);  	// true
	filter_var('1', FILTER_VALIDATE_BOOLEAN); 		// true
	filter_var(1, FILTER_VALIDATE_BOOLEAN);   		// true
	filter_var('yes', FILTER_VALIDATE_BOOLEAN);   	// true
	filter_var('off', FILTER_VALIDATE_BOOLEAN);   	// false
	filter_var('false', FILTER_VALIDATE_BOOLEAN); 	// false
	filter_var('0', FILTER_VALIDATE_BOOLEAN); 		// false
	filter_var(0, FILTER_VALIDATE_BOOLEAN);   		// false
```


## Setear variable string a entero 
###### Tags: `php` `intval`

Devuelve el valor integer de una var, con la especificada base para la conversión (por defecto es base 10). 
No debería ser usado en objetos, si es usado emitirá un error de nivel E_NOTICE y devolverá 1.

```php
	echo intval(42);                      // 42
	echo intval(4.2);                     // 4
	echo intval('42');                    // 42
	echo intval('+42');                   // 42
	echo intval('-42');                   // -42
	echo intval(042);                     // 34
	echo intval('042');                   // 42
	echo intval(1e10);                    // 1410065408
	echo intval('1e10');                  // 1
	echo intval(0x1A);                    // 26
	echo intval(42000000);                // 42000000
	echo intval(420000000000000000000);   // 0
	echo intval('420000000000000000000'); // 2147483647
	echo intval(42, 8);                   // 42
	echo intval('42', 8);                 // 34
	echo intval(array());                 // 0
	echo intval(array('foo', 'bar'));     // 1
```


## Setear variable string a decimal
###### Tags: `php` `floatval`

Pasar valor a float, entero en caso de no tener decimales
```php
    floatval("1234.56789");          // 1234.56789
    floatval("1234.56789Hello");     // 1234.56789
    floatval("Hello1234.56789");     // 0
```


## Validar si una variable es decimal
###### Tags: `php` `is_float`
```php
    is_float(27.25)     // True
    is_float(23.5)      // True
    is_float(1e7)       // True - Notación Científica
    is_float('abc')     // False
    is_float(23)        // False
    is_float(true)      // False
```


## Validar si una variable es numerica
###### Tags: `php` `is_numeric`
```php
	is_numeric(32) 			// True
	is_numeric('32')   		// True
	is_numeric(0)  			// True
	is_numeric(32.5)   		// True
	is_numeric(true)   		// False
	is_numeric(null)   		// False
	is_numeric('abc')  		// False
```


## Redondear un numero
###### Tags: `php` `round` `PHP_ROUND_HALF_UP` `PHP_ROUND_HALF_DOWN` `PHP_ROUND_HALF_EVEN` `PHP_ROUND_HALF_ODD`

Documentación: https://www.php.net/manual/es/function.round.php  

**PHP_ROUND_HALF_UP**: Redondea val hacia arriba a precision lugares decimales alejándose de cero, cuando está a medio camino. Hace que 1.5 sea 2, y -1.5 sea -2.  
**PHP_ROUND_HALF_DOWN**:	Redondea val hacia abajo a precision lugares decimales hacia cero, cuando está a medio camino. Hace que 1.5 sea 1, y -1.5 sea -1.  
**PHP_ROUND_HALF_EVEN**:	Redondea val a precision lugares decimales hacia el siguiente valor par.  
**PHP_ROUND_HALF_ODD**:	Redondea val a precision lugares decimales hacia el siguiente valor impar.  


```php
	// Ejemplo #1 Ejemplos de round()
	echo round(3.4);         // 3
	echo round(3.5);         // 4
	echo round(3.6);         // 4
	echo round(3.6, 0);      // 4
	echo round(1.95583, 2);  // 1.96
	echo round(1241757, -3); // 1242000
	echo round(5.045, 2);    // 5.05
	echo round(5.055, 2);    // 5.06
	
	// Ejemplo #2 Ejemplos de mode  
	echo round(9.5, 0, PHP_ROUND_HALF_UP);   // 10
	echo round(9.5, 0, PHP_ROUND_HALF_DOWN); // 9
	echo round(9.5, 0, PHP_ROUND_HALF_EVEN); // 10
	echo round(9.5, 0, PHP_ROUND_HALF_ODD);  // 9
	echo round(8.5, 0, PHP_ROUND_HALF_UP);   // 9
	echo round(8.5, 0, PHP_ROUND_HALF_DOWN); // 8
	echo round(8.5, 0, PHP_ROUND_HALF_EVEN); // 8
	echo round(8.5, 0, PHP_ROUND_HALF_ODD);  // 9
	
	// Usar PHP_ROUND_HALF_UP com precisión de 1 dígito decimal
	echo round( 1.55, 1, PHP_ROUND_HALF_UP);   //  1.6
	echo round( 1.54, 1, PHP_ROUND_HALF_UP);   //  1.5
	echo round(-1.55, 1, PHP_ROUND_HALF_UP);   // -1.6
	echo round(-1.54, 1, PHP_ROUND_HALF_UP);   // -1.5

	// Usar PHP_ROUND_HALF_DOWN com precisión de 1 dígito decimal
	echo round( 1.55, 1, PHP_ROUND_HALF_DOWN); //  1.5
	echo round( 1.54, 1, PHP_ROUND_HALF_DOWN); //  1.5
	echo round(-1.55, 1, PHP_ROUND_HALF_DOWN); // -1.5
	echo round(-1.54, 1, PHP_ROUND_HALF_DOWN); // -1.5

	// Usar PHP_ROUND_HALF_EVEN com precisión de 1 dígito decimal
	echo round( 1.55, 1, PHP_ROUND_HALF_EVEN); //  1.6
	echo round( 1.54, 1, PHP_ROUND_HALF_EVEN); //  1.5
	echo round(-1.55, 1, PHP_ROUND_HALF_EVEN); // -1.6
	echo round(-1.54, 1, PHP_ROUND_HALF_EVEN); // -1.5

	// Usar PHP_ROUND_HALF_ODD com precisión de 1 dígito decimal
	echo round( 1.55, 1, PHP_ROUND_HALF_ODD);  //  1.5
	echo round( 1.54, 1, PHP_ROUND_HALF_ODD);  //  1.5
	echo round(-1.55, 1, PHP_ROUND_HALF_ODD);  // -1.5
	echo round(-1.54, 1, PHP_ROUND_HALF_ODD);  // -1.5
```


## switch case break

```php
	$favcolor = "red";
	switch ($favcolor) {
	  case "red":
		echo "Your favorite color is red!";
		break;
	  case "blue":
		echo "Your favorite color is blue!";
		break;
	  default:
		echo "Your favorite color is neither red, blue, nor green!";
	}
```

## Iteracion
###### Tags: `php` `for` 
```php
    for ($i = 1; $i <= 5; $i++) {
        echo $i;
    }
    // Salida 1, 2, 3, 4, 5
```

## Funciones

### Sumar valores de una columna especifica
###### Tags: `php` `array_reduce` 
```php		
	$umbralProductsUnits = array_reduce($umbralDb, function($v1, $v2){ return $v1+$v2['unitsWeek']; }, 0 );
```

### Fechas
###### Tags: `php` `date` 

Documentación:  
https://www.php.net/manual/es/function.date.php  

```php		
	date('d/m/Y');  						// 02/11/2021
	date("F j, Y, g:i a");                  // March 10, 2001, 5:16 pm
	date("m.d.y");                          // 03.10.01
	date("j, n, Y");                        // 10, 3, 2001
	date("Ymd");                            // 20010310
	date('h-i-s, j-m-y, it is w Day');      // 05-16-18, 10-03-01, 1631 1618 6 Satpm01
	date('\i\t \i\s \t\h\e jS \d\a\y.');    // it is the 10th day.
	date("D M j G:i:s T Y");                // Sat Mar 10 17:16:18 MST 2001
	date('H:m:s \m \i\s\ \m\o\n\t\h');      // 17:03:18 m is month
	date("H:i:s");                          // 17:16:18
	date("Y-m-d H:i:s");                    // 2001-03-10 17:16:18 (el formato DATETIME de MySQL)
```

### Fecha y Hora - modificar horas
###### Tags: `php` `datetime` `modify`
```php		
	$dateDocument = new DateTime($docHead['fecCrea']);		// 2022-01-12 05:45:39.064809
	$dateDocument->modify("2 hour");						// 2022-01-12 07:45:39.064809
```

### Crear fecha a partir de formato 
###### Tags: `php` `datetime` `createFromFormat`

Documentación:  
https://www.php.net/manual/es/datetime.createfromformat.php  

```php
	// Fecha formato 16/09/2021
	$dateInitdt = DateTime::createFromFormat('d/m/Y', $dateInitFormat);
	
	// Fecha formato 16/09/20 ([y] minúscula)
	$datetimeInit = DateTime::createFromFormat('d/m/y', $dateInit);
	
	// Fecha Formato 21/01/2021 15:20 (Horas y minutos) H=Formato 24horas
	$dateInitdt = DateTime::createFromFormat('d/m/Y H:i', $dateInit);
```

### Diferencia entre fechas
###### Tags: `php` `datetime` `createFromFormat` `diff`

```php
	$dateInitdt = DateTime::createFromFormat('d/m/Y', $dateInitFormat);
	$dateEnddt = DateTime::createFromFormat('d/m/Y', $dateEndFormat);
	if(!$dateInitdt) { throw new Exception("Histórico Grupo: Error formato fecha Inicial"); }
	if(!$dateInitdt) { throw new Exception("Histórico Grupo: Error formato fecha Final"); }
	$dateDiff = $dateInitdt->diff($dateEnddt);
    $numDays = $dateDiff->days;
	
	// Fecha formato 16/09/20 ([y] minúscula)
	$datetimeInit = DateTime::createFromFormat('d/m/y', $dateInit);
	
	// Fecha Formato 21/01/2021 15:20 (Horas y minutos) H=Formato 24horas
	$dateInitdt = DateTime::createFromFormat('d/m/Y H:i', $dateInit);
	
```

### string to xml
```php
	$resultTrans = new SimpleXMLElement($responseClaro);
```

## throw new Exception - Excepciones  
```php
	throw new Exception("Histórico Grupo: Error formato fecha Final"); 
```

## Texto en mayuscula con caracteres especiales
###### Tags: `php` `mb_strtoupper`
```php
	$str = "Mary Had A Little Lamb and She LOVED It So";
	$str = mb_strtoupper($str);
	echo $str; // Imprime MARY HAD A LITTLE LAMB AND SHE LOVED IT SO
```

## Texto en minuscula con caracteres especiales
###### Tags: `php` `mb_strtolower`
```php
	$str = "Ejemplo ñ test á";
	$str = mb_strtolower($str);
	echo $str; // ejemplo ñ test á
```


## implode Unir elementos de un arreglo
```php
$arr = array('Hello','World!','Beautiful','Day!');
echo implode("-",$arr);					// Hello-World-Beautiful-Day!
```

## explode convertir  variable string en array
```php
$str = "Hello world. Beautiful day.";
print_r (explode(" ",$str));			// Array ( [0] => Hello [1] => world. [2] => Beautiful [3] => day.)
```

### strip_tags Eliminar contenido html-php en variables
Esta función intenta devolver una cadena con todos los bytes NULL, etiquetas HTML y PHP despojadas de un determinado str. Utiliza la misma máquina de estado de eliminación de etiquetas que la función fgetss () .

```php
$text = '<p>Test paragraph.</p><!-- Comment --> <a href="#fragment">Other text</a>';
echo strip_tags($text);
// Retornará "Párrafo de prueba. Otro texto"

// Allow <p> and <a>
echo strip_tags($text, '<p><a>');
echo strip_tags($text, ['p', 'a']);		// PHP 7.4.0
// Retornará "<p> Párrafo de prueba. </p> <a href="#fragment"> Otro texto </a>"
```

### Crear archivo JSON partiendo de array php

```php
	$file = fopen("../_file.json", "w") or die("Error opening output file");

	// Formato amigable
	$json = json_encode ( $structure, JSON_PRETTY_PRINT );
	fwrite($file, $json);

	// Json en una sola línea
	$json = json_encode($structure,JSON_UNESCAPED_UNICODE)
	fwrite($file, $json);

	// Json con KEYS y formato amigable
	$json = json_encode ( $structure, JSON_FORCE_OBJECT|JSON_PRETTY_PRINT );
	fwrite($file, $json);

	// Json con KEYS
	fwrite($file, json_encode($structure,JSON_FORCE_OBJECT ));
	fclose($file);
```

### Crear archivo PLANO txt - csv fputcsv

Parámetros de función fputcsv
1. nombreArchivo
2. arrayConLineaAIncluir
3. delimitador

```php
	// Listado de ejemplo
	$lista = array (
		array('aaa', 'bbb', 'ccc', 'dddd'),
		array('123', '456', '789'),
		array('"aaa"', '"bbb"')
	);

	// Abrir archivo / Iterar registros / Cerrar archivo
	$fp = fopen('fichero.csv', 'w');
	foreach ($lista as $campos) {
		fputcsv($fp, $campos);
	}
	fclose($fp);
	
	// En caso de generar descarga a traves de codeigniter 
	force_download('fichero.csv', NULL); 
	
	/*
	// Salida en CSV
	aaa,bbb,ccc,dddd
	123,456,789
	"""aaa""","""bbb"""
	*/
```


## PHP Excel

```php		
	// PHPEXCEL - Recorrer abecedario 
	foreach(range('A',$lastCol) as $columnID) {
		$PhpExcel->getActiveSheet()->getColumnDimension($columnID)->setAutoSize(true);
	}

	// PHPEXCEL - Formato con DOS Decimales 
	$Sheet->getStyle($lastCol.'2:'.$lastCol.($row-1))->getNumberFormat()->setFormatCode('0.00'); 
```

### Exportar excel cvs con numeros grandes formato texto

Al exportar a excel sea por csv o directamente de la librería, para números grandes y evitar que el formato se dañe al abrir el archivo

```php
	'Serial' => $valor['serie']."\t",
```