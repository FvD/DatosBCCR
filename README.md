# DatosBCCR
Funci�n para conectarse al API del BCCR y descargar las series directamente a R.
Requiere instalaci�n previa de los siguientes paquetes: RCurl, httr, dplyr y XML.
En caso de no estar instalados, los paquetes ser�n descargados autom�ticamente.
Para una descripci�n del API, ver: http://www.bccr.fi.cr/indicadores_economicos_/ServicioWeb.html.

##Instalaci�n

Para instalar el paquete se deben seguir dos pasos:

1. Instalar el paquete devtools (`install.packages("devtools"); library("devtools")`).
2. Utilizar el comando de instalaci�n desde github: `install_github("rafaelcb/DatosBCCR")`

## Uso

La funci�n de descarga es `DescargarDatosBCCR(indicador, inicio="11/02/1989", fin = "hoy", subniveles = "N", nombre= "me")`. La funci�n retorna un data.frame en formato largo, lo que facilita graficar los datos con ggplot.

### Par�metros
* El _indicador_ es el �nico par�metro obligatorio. Se trata de un n�mero de serie que puede ser obtenido del listado disponible a trav�s de `View(cods)`. Para varias series, se puede utilizar un vector num�rico (`DescargarDatosBCCR(c(1, 317))` retorna por ejemplo el tipo de cambio de compra diario y la cuenta corriente trimestral).

* Las fechas de _inicio_ y _fin_ son aquellas que se desean intentar descargar. Deben ser ingresadas como texto y en formato "dd/mm/aaaa".

* El par�metro _subniveles_ se refiere a la posibilidad de descargar ciertas variables relacionadas a la de inter�s. Por ejemplo, `DescargarDatosBCCR(1, subniveles = "S")` retorna 14 series con los distintos componentes de la cuenta corriente. Para determinar si existen subniveles, se debe realizar una inspecci�n visual de las series [en el sitio del BCCR](http://www.bccr.fi.cr/indicadores_economicos_/ServicioWeb.html), ya que la indentaci�n indica las relaciones entre variables.

* Por �ltimo, el par�metro _nombre_ se refiere a una cadena de texto que sirve como referencia para que el API tenga un control respecto a qui�n descarga los datos.



**Versi�n 0.3.0: Agosto 2016**




