# Colab CheatSheet

## GOOGLE DRIVE

	from google.colab import drive
	drive.mount('/content/drive') 
	
## LINK DIRECTORY
	ln -s "/content/drive/My Drive/colab_shared/"  "/content/DIRECTORYNAME"
	
## GIT & BITBUCKET 

	git clone https://username:pwd@bitbucket.org/REPOADDRESS

	git switch -t "remotes/origin/BRANCHNAME"

## ZIP & UNZIP

	!unzip "/content/drive/FILEPATH"
	!zip "ZIP_FILEPATH"	"ZIPPING_FILEPATH1" "ZIPPING_FILEPATH2" ...
	
## FILE
	!cp SOURCE_FILEPATH DESTINATION_FILEPATH

## TEXT 

	!head FILEPATH
	!tail FILEPATH
	!wc -l FILEPATH
	
# SQL SERVER
	def  import_sql_lib():

		!curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
		!curl "https://packages.microsoft.com/config/ubuntu/18.04/prod.list" > "/etc/apt/sources.list.d/mssql-release.list"
		!apt update
		!ACCEPT_EULA=Y apt-get install msodbcsql17
		path="/etc/odbc.ini"
		!>$path
		!echo -e "[sqlTest]\nDriver = ODBC Driver 17 for SQL Server\n" >>$path
		#!apt-get install unixodbc-dev
		!pip install pyodbc
		con_str="""DSN=sqlTest;Server=IPADDRESS,PORT;
		Database=DBNAME;UID=DB_USER;
		PWD=DB_PWD;
		Trusted_Connection=no;"""
		#TEST 
		#!isql IPADDRESS,PORT DB_USER DB_PWD
		import pyodbc
	def connectionTest():
		con_str="""DSN=sqlTest;Server=IPADDRESS,PORT;
		Database=DBNAME;UID=DB_USER;
		PWD=DB_PWD;
		Trusted_Connection=no;"""
		conn = pyodbc.connect(con_str)
	
