---
layout: post
title: "Inyección de dependencias manual en aplicaciones ASP.NET MVC"
date: 2016-05-11
tags: di aspnet mvc
published: false
---

# Inyección de dependencias manual en aplicaciones ASP.NET MVC

Mi primera publicación está dedicada al concepto de la inyección de dependencias y más concretamente en aplicaciones ASP.NET MVC hasta la versión 5. Es importante aclarar que no estamos hablando de la versión ASP.NET Core que usa otros mecanismos. 

**La Inversión de la dependencia o Inyección de dependencias** es un principio básico de la programación orientada a objetos [introducido por el gran Robert C. Martin](https://es.wikipedia.org/wiki/SOLID "Wikipedia"). De los cinco principios representados por el acrónimo SOLID es el último, pero desde mi punto de vista no el menos importante. No es el objetivo de este artículo explicar qué implica este patrón de diseño, sólo hay que navegar hasta este artículo de [Wikipedia](https://en.wikipedia.org/wiki/Dependency_injection "Dependency injection") y leer esta fantástica entrada.

En las últimas aplicaciones que he hecho con ASP.NET MVC siempre he usado la inyección de dependencias usando un Contenedor de Iversión de la depenendencia o IoC Container. Hay muchos de estos contenedores: [Unity](https://github.com/unitycontainer/unity), [AutoFac](http://autofac.org/), [Funq](https://funq.codeplex.com/), [Ninject](http://www.ninject.org/), [Spring.Net](http://www.springframework.net/), [Windsor](https://github.com/castleproject/Windsor), etc. Yo he usado preferentemente Ninject. Aunque los estos componentes son de código abierto y podemos ver su "magia", en algunos momentos siento que estoy _matando moscas a cañonazos_. Es por eso que en determinadas aplicacaciones pequeñas suelo usar la inyección de dependencias manual. Este método tiene sus ventajas y sus inconvenientes.

## Ventajas

1. Básicamente la principal ventaja es que nosotros tenemos el control y entendemos perfectamente lo que está sucediendo.
2. Es más rápido. Aunque no creo que este sea un factor determinante puesto que no estamos hablando de tiempos perceptibles por un usuario. El hecho de no tener tanta "fontanería" implica algo más de velocidad.

## Inconvenientes

1. Implica un mayor trabajo de programación. Dependiendo de las dependencias que tengamos que inyectar y dónde queramos hacerlo puede llegar a ser un trabajo muy complejo y tedioso.
2. Es más costoso decidir el ciclo de vida de las clases que inyectamos. Los Contenedores nos proporcionan métodos de configuración fáciles y descriptivos para establecer el ciclo de vida de la clase que se inyecta. El trabajo de hacerlo de forma manual es más complejo, dependiendo de dónde queramos llegar. 

## El Framework ASP.NET MVC y su extensibilidad

ASP.NET MVC ha sido diseñado con la perpectiva de la modulariadad como prioridad. Esto implica que podemos cambiar el comportamiento estándar con sólo sustituir un módulo por otro. Podemos intervenir en prácticamente todas las áreas que intervienen en el procesamiento de una petición, desde la creacción del controlador hasta el procesamiento de una vista. Es esta forma en que está construído el framework la que nos permite intervenir para inyectar las dependencias dónde sea necesario.

### Factoría de controladores

Aunque luego veremos cómo inyectar dependencias en otros componentes, dónde siempre tendremos que usar la inyección de dependencias es en los controladores. Aquí es dónde tenemos que pasar un contexto de base de datos, una servicio de registro de eventos, un repositorio o cualquier otra clase necesaria para que la acción concreta pueda realizar su trabajo.

#### El método por reflexión

Hay tres formas de inyectar las dependencias a una clase. Se pueden encontrar en el artículo de [Wikipedia](https://en.wikipedia.org/wiki/Dependency_injection "Dependency injection") anterior. Yo voy a usar el inyección por el constructor dado que en este contexto es la elección más lógica.

#### El método condicional


#### El método mixto


#### Los ciclos de vida de las clases


### Inyección de dependencias en las vistas


### Inyección de dependencias en los filtros


## Conclusiones