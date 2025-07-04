[`Volver`](../index.html)

# Python

- [`EJERCICIOS`](https://dailypythonprojects.substack.com/)
- [`DESCARGAR`](https://www.python.org/downloads/)


## Instalar

Seguir los siguientes pasos dependiendo el sistema operativo
- [`WINDOWS`](python/pythonInstalarWindows.pdf)
- [`LINUX`](python/pythonInstalarWindows.pdf)
- [`MAC`](python/pythonInstalarMac.pdf)


## Consola

```bash
	py -3                   # Testear pyton x consola - apertura inicio consola  
	py -3 nombreArchivo     # Ejecutar un archivo ptyhon (formato py)  
	cls                     # Limpiar consola  
	exit()                  # Comando para salir de consola  
```

Puedes ver el listado de atributos del tipo de dato usando:  
```bash
	dir(int)                # Atributos de un tipo de variable - entero
	dir(float)              # Atributos de un tipo de variable - decimal
	dir(str)                # Atributos de un tipo de variable - texto
	dir(list)               # Atributos de un tipo de variable - lista
	dir(dict)               # Atributos de un tipo de variable - diccionario
	dir(__builtins__)       # Listado de todas las funciones de tipo variable
	
	help(str)
	help(str.upper)			# Explicación de una función de un tipo de variable (String)
	help(str.replace)		# Explicación de una función de un tipo de variable (String)
	help(dict.values)		# Explicación de una función de un tipo de variable (dict - objecto)
```

## Comentarios 

Se debe usar la almuadilla (#)

```bash
	# Ejemplo de operación
	print(3+4)
```


## Operadores matematicos

```bash
	print(3 + 4)       # Salida 7 (Addition)
	print(3 - 4)       # Salida -1 (Subtraction)
	print(3 * 4)       # Salida 12 (Multiplication)
	print(3 / 4)       # Salida 0.75 (Division)
	print(9 // 2)      # Salida 4 (Floor Division)
	print(9 % 2)       # Salida 1 (Modulus)
	print(3 ** 4)      # Salida 81 (Exponentiation - (3 * 3 * 3 * 3))
```

## Tipos de variables  
###### Tags: `integers` `floats` `strings` `lists` `dictionaries` `tuples`

Integers:  
```bash
	rank = 10
	eggs = 12
	people = 3
```

Floats:  
```bash
	temperature = 10.2
	rainfall = 5.98
	elevation = 1031.88
```

Strings:  
```bash
	message = "Welcome to our online shop!"
	name = "John"
	serial = "R001991981SW"
```

Lists: (Pueden modificarse)  
```bash
	members = ["Sim Soony", "Marry Roundknee", "Jack Corridor"]
	pixel_values = [252, 251, 251, 253, 250, 248, 247]
```

Dictionaries: (Con key => Valor)  
```bash
	phone_numbers = {"John Smith": "+37682929928", "Marry Simpons": "+423998200919"}
	volcano_elevations = {"Glacier Peak": 3213.9, "Rainer": 4392.1}
	
	Keys of a dictionary can be extracted with:
	phone_numbers.keys()
	
	Values of a dictionary can be extracted with:
	phone_numbers.values()
```

Tuples: represent arrays of values that are not to be changed during the course of the program:  
```bash
	vowels = ('a', 'e', 'i', 'o', 'u')
	one_digits = (0, 1, 2, 3, 4, 5, 6, 7, 8, 9)
```



## Uso variables 
###### Tags: `print` `string` `type` `list` `range`

Ejemplo con definicion de variables

```bash
	# Definicion de variables
	items = 3
	price = 4
	total = items *  price
	print(total)
	// Salida 12

	# Imprimir multiples variables
	print(total, items, price)
	// Salida 12 3 4 
```

Ejemplo con definicion de variables tipo texto

```bash
	# No es posible operar matematicamente variables tipo string
	x = 10    # int
	y = "10"  # string
	z = 10.1  # float
	
	total = x + x
	total2 = y + y
	print(total, total2)	             # Salida 20 1010
	print(type(x), type(y), type(z))     # Salida <class 'int'> <class 'str'> <class 'float'>	
```

Ejemplo listas

```bash
	notes = [5, 4, 3.1, 3]
	print(type(notes))                    # Salida <class 'list'>
	print(notes)                          # Salida [5, 4, 3.1, 3]
	print(notes * 3)                      # Salida [5, 4, 3.1, 3, 5, 4, 3.1, 3, 5, 4, 3.1, 3]
	print(notes + notes)                  # Salida [5, 4, 3.1, 3, 5, 4, 3.1, 3]
```

Ejemplo rangos

Paremetros: 
1. inicio
2. termina (antes de este)
3. step o saltos entre valores

```bash
	notes = list{range(1,6)}               # Salida [1,2,3,4,5]
	notes2 = list(range(1,6, 2))           # Salida [1,3,5]
```

Ejemplo Tuplas - Son iguales a las listas, pero con parentesis ()  
- La diferencia radica en que a este tipo de variable no se le pueden adicionar más valores  

```bash
	notes3 = (9.1, 8.8, 7.5)
	sum(notes3)             
```


## Funciones de tipos de variables 
###### Tags: `upper` `title` `lower` `sum` `len` `max` `count` `values` `keys` `append` `remove` `clear` `index` 

Uso de funciones en tipos de variables

```bash
	# Ejemplo tipo texto
	text = 'Hello'
	text.upper()                          # Salida HELLO
	text.title()                          # Salida Hello
	text.lower()                          # Salida hello
	text.replace('e', 'i')                # Salida hillo
	
	# Indexacion textos
	text = 'Hello'
	text[1]                                # Salida: e
	text[-1]                               # Salida: o
	text[:3]                               # Salida: hel
	
	# Ejemplo listas
	notes3 = [9.1, 8.8, 7.5]
	sum(notes3)                          # Salida 25.4 (suma los valores)
	len(notes3)                          # Salida 3    (cuenta la cantidad de elementos)
	max(notes3)                          # Salida 9.1  (Valor mayor)
	
	# Cuenta cantidad de coincidencias
	student_grades = [9.1, 8.8, 10.0, 7.7, 6.8, 8.0, 10.0, 8.1, 10.0, 9.9]
	student_grades.count(10)	        # Salida 3 
	
	# Funciones generales de lista (Agregar | Eliminar | Acceder)  
	temperatures = [5,6,7,8]
	temperatures.append(9)              # Salida: [5,6,7,8,9]
	temperatures.remove(6)              # Salida: [5,7,8,9]
	temperatures.clear()                # Salida: []
	temperatures.index(6)               # Salida: 1
	temperatures.__getitem__(1)         # Salida: 6
	temperatures[0]                     # Salida: 5
	temperatures[1]                     # Salida: 6
	
	# Segmentar Lista
	temperatures[1:3]                   # Salida: [6,7]
	temperatures[:3]                    # Salida: [5,6,7]
	temperatures[0:3]                   # Salida: [5,6,7]
	temperatures[2:]                    # Salida: [7,8]
	
	# Segmentar Lista: Index Negativo (se cuenta del ultimo elemento al primero (-1, -2))
	temperatures[-1]                    # Salida: 8
	temperatures[-2]                    # Salida: 7
	temperatures[-2:]                   # Salida: [7,8]
	temperatures[-3:-1]                 # Salida: [6,7,8]
```

Ejemplo de variable tipo diccionatio (dict) - Objecto

```bash
	student_grades = { "Juan": 9.1, "Luis": 8.8, "Pedro": 7.5 }
	student_grades.values()                     # Salida: dict_values([9.1, 8.8, 7.5])
	student_grades.keys()                       # Salida: dict_keys(['Juan', 'Luis', 'Pedro'])
	mysum = sum(student_grades.values);         # Salida: 25.4
	student_grades['Juan']                      # Salida: 9.1
```


## Convertir tipos de datos
###### Tags: `list` `tuple` `str` `join`

De tuple a list:  
```bash
	cool_tuple = (1, 2, 3)
	cool_list = list(cool_tuple)
	cool_list
	Salida: [1, 2, 3]
```

De list a tuple:  
```bash
	cool_list = [1, 2, 3]
	cool_tuple = tuple(cool_list)
	cool_tuple
	Salida: (1, 2, 3)
```

De string a list:  
```bash
	cool_string = "Hello"
	cool_list = list(cool_string)
	cool_list
	Salida: ['H', 'e', 'l', 'l', 'o']
```

De list a string:
```bash
	cool_list = ['H', 'e', 'l', 'l', 'o']
	cool_string = str.join("", cool_list)
	cool_string
	Salida: 'Hello'
```

## Indexacion de tipos de variables 
###### Tags: `list` `tuple`

Lists, strings, and tuples have a positive index system:
```bash
	["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"]
	   0      1      2      3      4      5      6
```

And they have a negative index system as well:
```bash
	["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"]
	  -7     -6     -5     -4     -3     -2     -1
```


In a list, the 2nd, 3rd, and 4th items can be accessed with:
```bash
	days = ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"]
	days[1:4]
	Output: ['Tue', 'Wed', 'Thu']
```

First three items of a list:
```bash
	days = ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"]
	days[:3]
	Output:['Mon', 'Tue', 'Wed'] 
```

Last three items of a list:
```bash
	days = ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"]
	days[-3:]
	Output: ['Fri', 'Sat', 'Sun']
```

Everything but the last:
```bash
	days = ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"]
	days[:-1] 
	Output: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat'] 
```

Everything but the last two:
```bash
	days = ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"]
	days[:-2] 
	Output: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri'] 
```

A dictionary value can be accessed using its corresponding dictionary key:
```bash
	phone_numbers = {"John":"+37682929928","Marry":"+423998200919"}
	phone_numbers["Marry"]
	Output: '+423998200919'
```
