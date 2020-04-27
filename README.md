# PIPENV+SPARK+JUPYTER+MACHING-LEARNING EN WINDOWS 10
Estructura para trabajo de Organizacion y Datos

## Paquetes añadidos:
jupyter = "*"
pandas = "*"
numpy = "*"
seaborn = "*"
matplotlib = "*"
bokeh = "*"
scipy = "*"
findspark = "*"
py4j = "*"
pyspark = "*"
scikit-learn = "*"
tensorflow = "*"
pyproj = "*"
geos = "*"
six = "*"
shapely = "*"

### *REQUERIMIENTOS:
	python_version = "3.7"
	java = 1.8
	
## *INSTALACIÓN DEL REPOSITORIO [PYTHON + SPARK + HERAMIENTAS]
	
	0° Instalar python , link: https://www.python.org/downloads/release/python-370/  //importante 3.7.0 o modificar el pipfile para otra versión.
	1° Instalar Java (1.8 recomendable)
	2° Instalar pipenv con pip:
			> pip install pipenv
	3° Instalar apache Spark
			3.1 - Descargar apache del siguiente link: https://spark.apache.org/downloads.html
			3.2 - EN mi caso (abril 2020 descargue:  spark-3.0.0-preview2-bin-hadoop2.7.tgz)
			3.3 - Extraer el contenido en C:\Spark
			3.4 - Setear variables de entorno:
						SPARK_HOME = C:\Spark\spark-3.0.0-preview2-bin-hadoop2.7
						PATH += C:\Spark\spark-3.0.0-preview2-bin-hadoop2.7\bin
			3.5 Instalar Winsutils:
					3.5.1 - Descargar winutils.exe desde: https://github.com/steveloughran/winutils
							Importante: Escoger la misma version para el spark que descargamos(en este caso hadoop 2.7.1)
					3.5.2 - Buscar winutils.exe dentro de la carpeta del repo de git de hadoop-X.X.X donde X.X.X es la version.
							Link directo a hadoop-2.7.1: https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe
					3.5.3 - Copiarlo en C:\Spark\spark-3.0.0-preview2-bin-hadoop2.7\bin
					3.5.4 - Setear variable de ambiente:
							HADOOP_HOME = C:\Spark\spark-3.0.0-preview2-bin-hadoop2.7
			
	4° Descargar Repositorio o clonarlo link: https://github.com/diegolanu89/python_spark.git
	6° Crear directorio con el ambiente en la ruta del repo:
		    EJ: >c:\el_repo		   //cualquier dirección donde este la carpeta raiz del repo
			 6.1  >pipenv shell    //crea un entorno virtual o lo inicia si ya esta creado.
			 6.2  >pipenv install  //actualizará y descargará todas las dependencias necesarias 
							       //que ya estan cargadas en el pipfile del repo (ej;pandas,numpy,jupyter...)
	7° Reiniciar la PC
	8° Al terminar el proceso podras ejecutar jupyter:
      8.1 - Repetir el paso 6.1 unicamente (para volver a iniciar el entorno virtual)
		  8.2 - Ejecutar:
                    > jupyter notebook

## *INICIOS POSIBLES PARA SPARK
	
		import findspark 
		findspark.init('C:\Spark\spark-3.0.0-preview2-bin-hadoop2.7')   //busca el entorno de Spark
		
		from pyspark import SparkContext
		try: 
			type(sc)
		except NameError:
			sc = pyspark.SparkContext('local[*]')
			
## *INSTALACIÓN DE PAQUETES ADICIONALES:
	Sempre luego de iniciar pipenv shell en la carpeta raiz del repo clonado:
		pipenv install 'nombre_del_paquete'
	Recomendación:instalar los paquetes en el entorno nuevo sin estar usando previamente ningun notebook abierto o script de python.
		
## *¿PORQUÉ USAR PIPENV (ENTORNO VIRTUAL)?:
	- Porque es más fácil ejecutarlo e instalarlo.
	- NO rompe nada del python instalado base en el sistema o corrompe paquetes previamente instalados.
	- Se puede dockerizar , empaquetar con yam, npm, versionar, etc.
	- Porque yo decido que versiones y cuando usarlas (modificando el pipfile o el package.json).
	- Porque es una buena práctica y punto (Salvo que lo uses unicamente en tu vida para cursar Datos).

### *EXTRAS:
###	VSCode
	Recomiendo en lugar de Jupyter o Jupyter Labs utilizar 'VS Code' para utilizar el entorno del repo. 
	El plugin permite elegir el entorno virtual que nosotros creamos como Kernel o cualquier otro.
	La interfaz es mucho mas dósil y NOS AHORRAMOS DE INICIAR POR CONSOLA SIEMPRE DESDE EL ENTORNO A JUPYTER.

### 	GEOS + basemap:
	1 - Instalar todos los paquetes con el ejecutable en la carpeta packs:  osgeo4w-setup-x86_64
	2 - Download basemap‑1.2.1‑cp37‑cp37m‑win_amd64.whl in https://www.lfd.uci.edu/~gohlke/pythonlibs/
	2 - En el directorio de la descarga : 
			pip install basemap‑1.2.1‑cp37‑cp37m‑win_amd64.whl

### Posible error de ambiente:
	1- setx /M PIPENV_VENV_IN_PROJECT 1 (con permisos de admin el cmd)
	2 - python -m venv .venv 
	3 - pipenv shell
	4 - pipenv install