## Using MSSQL

* Requires third party libraries<!-- .element: class="fragment" -->
  - "EFDException: [FireDAC][Phys][ODBC]-314. Cannot load vendor library [libodbc.so]. Hint: check it is in the PATH or application EXE directories, and has x64 bitness."<!-- .element: class="fragment" -->
* Out of date documentation<!-- .element: class="fragment" -->
  - https://docwiki.embarcadero.com/RADStudio/Athens/en/Connect_to_Microsoft_SQL_Server_(FireDAC)<!-- .element: class="fragment" -->
  - https://docwiki.embarcadero.com/RADStudio/Athens/en/UnixODBC_(FireDAC)<!-- .element: class="fragment" -->
* More libraries needed than documentation claims "EMSSQLNativeException: [FireDAC][Phys][ODBC][unixODBC][Driver Manager]Can't open lib 'libtdsodbc.so' : file not found"<!-- .element: class="fragment" -->
* Microsoft documentation is better, but not enough to make it work<!-- .element: class="fragment" -->
  - https://learn.microsoft.com/en-us/sql/connect/odbc/download-odbc-driver-for-sql-server?view=sql-server-ver16<!-- .element: class="fragment" -->
* Full story: MSSQL ODBC + unixODBC + FreeTDS + tdsodbc + ini file<!-- .element: class="fragment" -->
  - https://github.com/partouf/DS24-Linux-Delphi-Resources/blob/main/container-app-docker/Dockerfile<!-- .element: class="fragment" -->
