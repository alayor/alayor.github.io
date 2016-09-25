---
layout: post
title:  "Behaviour-Driven Development"
date:   2016-09-24 21:45:00 -0500
categories: post
---

"Esta funcionalidad esta erroneamente desarrollada. El calculo deberia
hacerse biweekly, es decir, dos veces por semana." - comento el analista
de negocios. "Esto esta completamente desviado de la funcionalidad que yo
habia solicitado".

Era la demostracion numero 2 que se le habia mostrado al analista de
negocios sobre esa nueva funcionalidad. Y esta era la sa vez que no se 
encontraba conforme con los resultados.

"Nosotros pensamos que biweekly significaba cada dos semanas" - 
respondio el programador. "Tratamos de seguir al pie de la letra los todos
requerimientos en la historia de usuario, pero al parecer existen
ambiguedades".
 
"Muy bien, tratare de redactarlo lo mas explicito posible" - Acordo el
analista de negocios".

Cual es el costo de estos malentendidos? Que se puede hacer para
evitarlos?

En la actualidad no se utilizan lenguajes como el ingles,
frances o espanol para codificar instrucciones y que un compilador o
interprete de software pueda procesar debido a que estos 
lenguajes se prestan a ambiguedades.

En este caso, la historia de usuario es redactada en idioma ingles, por
lo que al momento de se procesada por el interprete (en este caso el
programador) termina en un desarrollo incorrecto de la solucion.

BDD esta enfocado en solucionar este tipo de problemas proveendo un lenguaje
en comun que un analista de negocios y una computadora puedan entender.

Actualmente existen herramientas BDD como Cucumber que proporcionan
un lenguaje que es facilmente leible por personas no relacionadas
con la programacion.

Cucumber es un framework que permite crear archivos ".feature" donde los
analistas pueden redactar las reglas de negocio y definir el 
comportamiento de sistema.

Asi mismo, estos archivos pueden ser leidos por una computadora
de tal manera de que se puedan ejecutar pruebas automatizadas sobre
cada una de las instrucciones definidas por el analista de negocios.

El objetivo principal de BDD es resolver problemas de comunicacion dentro
de los equipos de software. Sin embargo, existe un uso muy interesante
que se le puede dar a esta herramienta si es que la definicion del
comportamiento se crea antes del desarrollo por parte del programador.

Al tener las deficiones previamente al desarrollo, se puede comprobar
en cualquier momento de la etapa de codificacion se se van cumpliendo
de manera satisfactoria con cada una de las reglas definidas. Asi como 
detectar si no se han afectado otras funcionalidades existentes.

Usando BDD, los equipos de desarrollo de software mantienen una sola
fuente de verdad donde se puede consultar la verdadera intencion
del software y donde se pueden evitar ambiguedades al momento de 
redaccion e interpretacion de las historias de usuario.