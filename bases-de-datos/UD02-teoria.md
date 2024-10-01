---
layout: default
title: UD02. Diseño de Bases de Datos, el modelo conceptual.
permalink: /bases-de-datos/ud02/teoria/
author: Teo Rojas
date: Septiembre 2024
abstract: Sinopsis de la unidad 02
---

# Índice

# Índice
1. [Introducción](#1-introducción)
2. [Diseño de Bases de Datos](#2-diseño-de-bases-de-datos)
    1. [Fase de Análisis: Especificación de Requisitos Software (E.R.S.)](#21-fase-de-análisis-especificación-de-requisitos-software-ers)
    2. [Fase 1 del Diseño: Diseño Conceptual – Modelo Entidad/Relación (E/R)](#22-fase-1-del-diseño-diseño-conceptual--modelo-entidadrelación-er)
    3. [Fase 2 del Diseño: Diseño Lógico – Modelo Relacional](#23-fase-2-del-diseño-diseño-lógico--modelo-relacional)
    4. [Fase 3 del Diseño: Diseño Físico – Modelo Físico](#24-fase-3-del-diseño-diseño-físico--modelo-físico)
3. [Entidades](#3-entidades)
    1. [Tipos de Entidades](#tipos-de-entidades)
4. [Atributos](#4-atributos)
    1. [Atributos y su Significado](#41-atributos-y-su-significado)
    2. [Tipos de Atributos](#42-tipos-de-atributos)
        1. [Atributos Identificadores de Entidad (Clave Primaria o Clave Principal)](#421-atributos-identificadores-de-entidad-clave-primaria-o-clave-principal)
        2. [Atributos Descriptores de Entidad](#422-atributos-descriptores-de-entidad)
        3. [Atributos Opcionales](#423-atributos-opcionales)
        4. [Atributos Derivados](#424-atributos-derivados)
        5. [Atributos Multivaluados](#425-atributos-multivaluados)
        6. [Atributos Compuestos](#426-atributos-compuestos)
        7. [Atributos Discriminadores o Discriminantes](#427-atributos-discriminadores-o-discriminantes)
5. [Relaciones](#5-relaciones)
    1. [Representación Gráfica de Relaciones](#representación-gráfica-de-relaciones)


# 1. Introducción

El diseño de bases de datos es una disciplina fundamental en el desarrollo de sistemas de información, y uno de los pilares clave para asegurar que una base de datos sea eficiente, escalable y funcional. Antes de implementar una base de datos, es necesario crear un diseño conceptual que permita entender y estructurar la información que será gestionada. En este tema, nos adentraremos en el **modelo Entidad-Relación (E/R)**, una herramienta ampliamente utilizada para diseñar la estructura lógica de una base de datos.

El **modelo E/R** proporciona una representación visual y abstracta de los datos mediante entidades, atributos y relaciones, lo que facilita la comprensión de cómo se conectan y organizan los diferentes elementos dentro del sistema. A través de este modelo, se pueden identificar claramente las entidades principales de un dominio de información, sus propiedades (**atributos**) y cómo se interrelacionan entre sí mediante diferentes tipos de **relaciones**.

Este tema no solo cubrirá los conceptos básicos del modelo E/R, sino que también explorará con profundidad la naturaleza de las relaciones, desde su **grado** hasta su **cardinalidad**, y cómo se representan y gestionan las **relaciones no binarias**. Además, abordaremos los **atributos propios de las relaciones**, los conceptos de **dependencia** e **interrelación**, y la importancia de evitar la **redundancia** en los datos, un aspecto crucial para mantener la eficiencia y coherencia en el sistema.

A medida que avancemos, también exploraremos el **modelo E/R Extendido (EER)**, que añade nuevas capacidades al modelo básico, permitiendo representar estructuras más complejas y restricciones adicionales. Este modelo es especialmente útil cuando se trabaja con dominios más sofisticados que requieren mayor precisión y detalle en la estructura de la información.

Finalmente, el tema concluirá con una **guía práctica** para la construcción de diagramas E/R, una herramienta esencial para cualquier diseñador de bases de datos, y varios **ejercicios** que ayudarán a consolidar los conocimientos adquiridos. Con todo ello, los estudiantes estarán equipados para diseñar modelos conceptuales robustos y sólidos que sirvan como la base de futuras implementaciones en bases de datos relacionales.


# 2. Diseño de Bases de Datos

El diseño de una base de datos es un proceso fundamental para estructurar la información de manera eficiente y asegurar que responda a las necesidades de los usuarios. Este proceso implica identificar todos los datos importantes relacionados con un problema específico a través de un análisis exhaustivo que permita determinar qué datos son esenciales y cuáles no lo son. Una vez identificados los datos clave, se crea un **esquema** que describe con precisión toda la información necesaria, similar a un plano que se elabora antes de construir un edificio.

El diseño de una base de datos suele seguir un proceso estructurado que va desde una etapa conceptual, en la que se modela la información de forma abstracta, hasta una fase física, en la que el diseño se implementa utilizando un Sistema Gestor de Bases de Datos (SGBD). A lo largo de este capítulo, exploraremos estas fases, entendiendo cómo cada una contribuye a crear una base de datos eficiente, organizada y sin redundancias.

## 2.1. Fase de Análisis: Especificación de Requisitos Software (E.R.S.)

Antes de comenzar con el diseño de la base de datos, es crucial entender las **necesidades** y **requisitos** del sistema. En esta etapa, los informáticos se reúnen con los usuarios y otras partes interesadas para recopilar la información necesaria, lo que resulta en un documento clave conocido como **Especificación de Requisitos Software (E.R.S.)**. Este documento describe de manera detallada qué información debe gestionar el sistema, cómo debe interactuar con los usuarios y qué reglas deben seguirse para asegurar que los datos sean precisos y consistentes.

El E.R.S. es la base sobre la cual se desarrollará el diseño de la base de datos, ya que define los requisitos de alto nivel que deben cumplirse. Este paso es crítico porque cualquier error o malentendido en esta etapa puede llevar a problemas durante las fases de diseño e implementación. Es aquí donde se definen las **entidades**, los **atributos** y las **relaciones** clave que formarán el esqueleto del modelo conceptual.

## 2.2. Fase 1 del Diseño: Diseño Conceptual – Modelo Entidad/Relación (E/R)

El **diseño conceptual** es la primera fase del diseño de la base de datos y se centra en representar la información de una manera que sea comprensible para usuarios no técnicos. En esta etapa, el objetivo es crear un **modelo abstracto** de la base de datos, que refleje los datos y las relaciones entre ellos sin entrar en detalles técnicos.

Para ello, se utiliza el **Modelo Entidad/Relación (E/R)**, que permite representar las entidades (objetos o conceptos que queremos modelar), sus atributos (propiedades o características) y las relaciones entre ellas. Este modelo es una herramienta visual que facilita la comprensión y permite a los diseñadores y usuarios asegurarse de que todos los datos necesarios están correctamente representados.

El modelo E/R se presenta en forma de diagramas, donde las entidades se representan como rectángulos, los atributos como óvalos, y las relaciones como líneas que conectan las entidades. Esta fase es crucial porque una buena representación conceptual reduce los problemas en las fases posteriores.

## 2.3. Fase 2 del Diseño: Diseño Lógico – Modelo Relacional

El **diseño lógico** es la segunda fase del proceso y aquí se traduce el diseño conceptual en un formato más técnico y orientado a la implementación. En este curso, utilizaremos el **Modelo Relacional**, que organiza la información en **tablas** (relaciones), donde cada columna representa un atributo de los datos y cada fila un registro.

El modelo lógico es más técnico que el diseño conceptual y está diseñado para que pueda ser implementado en un Sistema Gestor de Bases de Datos (SGBD). A través de esta etapa, los datos representados en el modelo E/R se convierten en tablas que pueden ser gestionadas por el SGBD, asegurando que todas las **entidades**, **atributos** y **relaciones** definidas se preserven correctamente.

El modelo relacional también introduce el concepto de **normalización**, un proceso que elimina la redundancia de datos y asegura la integridad referencial entre las tablas. La normalización es esencial para garantizar que la base de datos funcione de manera eficiente y sin inconsistencias.

## 2.4. Fase 3 del Diseño: Diseño Físico – Modelo Físico

El **diseño físico** es la última fase del proceso de diseño de bases de datos, y aquí se traduce el diseño lógico en un formato que puede ser implementado directamente en un SGBD. Esto implica decidir cómo se almacenarán los datos en el hardware, optimizar el acceso a los datos y seleccionar las estructuras de almacenamiento más adecuadas.

El diseño físico se implementa generalmente utilizando lenguajes de programación de bases de datos, como **SQL (Structured Query Language)**, que permite definir las tablas, establecer relaciones entre ellas, y manipular los datos mediante consultas, inserciones y actualizaciones. En este curso, aprenderemos a convertir el **Modelo Relacional** en un **Modelo Físico** utilizando SQL, lo que permitirá gestionar y manipular los datos de manera eficiente.

# 3. Entidades

Una **entidad** es cualquier cosa sobre la cual queremos almacenar información en la base de datos. Las entidades pueden ser personas, objetos, eventos o cualquier elemento relevante para el sistema. En un **diagrama Entidad/Relación (E/R)**, las entidades se representan gráficamente como **rectángulos** con un nombre en su interior. Cada entidad debe nombrarse solo una vez en el esquema conceptual, asegurando que no haya duplicación ni ambigüedad en la definición.

## Tipos de Entidades

Existen dos tipos principales de entidades: **entidades fuertes** y **entidades débiles**. La distinción entre estos dos tipos es fundamental para el diseño de bases de datos.

- **Entidades fuertes**: Son aquellas cuya existencia es **independiente** de otras entidades. Se representan gráficamente con un **rectángulo de borde simple**. Estas entidades tienen un identificador único, lo que permite diferenciarlas de otras entidades sin la necesidad de apoyarse en ninguna otra entidad.
- **Entidades débiles**: Son aquellas cuya existencia depende de la existencia de otra entidad, conocida como la **entidad propietaria**. Se representan con un **rectángulo de doble borde**. Las entidades débiles no tienen un identificador propio único y necesitan de una entidad fuerte para poder ser identificadas de manera única.

![Entidades Fuertes y Débiles](/bases-de-datos/imgs/ud02/ud02_img01_fuertesDebiles.png)

## Ejemplo de Entidad Fuerte y Débil

Para ilustrar la diferencia entre entidades fuertes y débiles, consideremos un ejemplo en el contexto de un banco:

- **Entidad Fuerte (Cliente de Banco)**: Un **Cliente de Banco** es una entidad fuerte. Tiene una existencia independiente y puede ser identificado por sí mismo mediante atributos como el número de identificación, el nombre completo, o un número de cliente único. Cada cliente es una entidad autónoma dentro del sistema, sin depender de ninguna otra entidad para su existencia.
  
- **Entidad Débil (Cuenta Bancaria)**: Una **Cuenta Bancaria** es una entidad débil porque su existencia depende de un **Cliente de Banco**. No puede ser identificada de manera única sin hacer referencia al cliente que la posee. Es decir, una cuenta bancaria solo tiene sentido en el contexto de un cliente específico; sin un cliente asociado, no puede existir ni ser identificada.

Este tipo de relación entre una entidad fuerte y una débil es común en sistemas que modelan situaciones en las que ciertos elementos no pueden existir de forma aislada.

## Resumen

En resumen, la diferencia clave entre una entidad fuerte y una entidad débil es que una **entidad fuerte** tiene una existencia independiente y se puede identificar de forma autónoma. En cambio, una **entidad débil** depende de otra entidad (la **entidad propietaria**) para su existencia y solo se puede identificar en el contexto de esa entidad. Siguiendo el ejemplo, un **Cliente de Banco** es una entidad fuerte, mientras que una **Cuenta Bancaria** es una entidad débil, ya que su existencia depende del cliente al que pertenece.

# 4. Atributos

Los **atributos** son componentes fundamentales en un modelo Entidad-Relación (E/R) y desempeñan un papel esencial en la descripción de las entidades y sus características. Son las propiedades que describen y definen la información relacionada con una entidad dentro de una base de datos.

## 4.1. Atributos y su Significado

- Los atributos son **propiedades** o **características** que describen una entidad en una base de datos.
- Cada entidad tiene sus propios atributos, los cuales representan información específica sobre dicha entidad.

## 4.2. Tipos de Atributos

### 4.2.1. Atributos Identificadores de Entidad (Clave Primaria o Clave Principal)

Los **atributos identificadores** tienen la función de **identificar de manera única** cada instancia u ocurrencia de una entidad en la base de datos. Esto significa que no puede haber dos instancias de la misma entidad con el mismo valor en el atributo identificador. 

Esta clase de atributos se representan con una circunferencia rellena de negro, en el ejemplo a continuación el **atributo identificador** es el que corresponde a `DNI`.

![Atributos](/bases-de-datos/imgs/ud02/ud02_img02_atributos01.svg)

- En un modelo E/R, debe existir **al menos un atributo identificativo** en cada entidad. Esto garantiza que cada instancia de la entidad se pueda identificar de forma única en la base de datos.

### 4.2.2. Atributos Descriptores de Entidad

Los **atributos descriptores** son aquellos que representan características o propiedades de una entidad. Por ejemplo, en una base de datos de empleados:

- Atributos como **"nombre," "apellido," "edad," y "dirección"** son ejemplos de atributos descriptivos.

Aunque proporcionan información detallada sobre la entidad, no se utilizan para **identificar** de forma única las instancias de la entidad.

Esta clase de atributos se representan con una circunferencia transparente, en el ejemplo a continuación el **atributo descriptor** es el que corresponde a `Nombre`.

![Atributos](/bases-de-datos/imgs/ud02/ud02_img02_atributos01.svg)


### 4.2.3. Atributos Opcionales

Los **atributos opcionales** son aquellos cuyo valor no es necesario que esté presente para todas las instancias de una entidad. En otras palabras, no todas las ocurrencias de una entidad deben tener un valor para estos atributos. Se utilizan cuando la información es relevante solo en ciertos casos o situaciones.

- Por ejemplo, en una base de datos de empleados, el atributo **"número de teléfono secundario"** podría ser opcional si no todos los empleados tienen uno.
- Otro ejemplo sería un atributo **"segundo nombre"** para una entidad "Persona", ya que no todas las personas tienen un segundo nombre.

Los atributos opcionales se representan en los diagramas E/R mediante una circunferencia que está unido a la entidad con una **línea discontinua**, lo que indica que su valor no es obligatorio.

![Atributos](/bases-de-datos/imgs/ud02/ud02_img02_atributos02.svg)

### 4.2.4. Atributos Derivados

Los **atributos derivados** son aquellos cuyos valores se calculan a partir de otros atributos en la base de datos. Por ejemplo:
- El atributo **"edad"** de una persona podría calcularse automáticamente a partir de su **"fecha de nacimiento"**.
- El **"precio_total"** de un producto podría derivarse de la suma del **"precio"** y el **"impuesto (%IVA)"**.

Se representan con una **circunferencia discontínua transparente** y con una línea contínua. A continuación el atributo `Edad` sería un atributo derivado.

![Atributos](/bases-de-datos/imgs/ud02/ud02_img02_atributos03.svg)

### 4.2.5. Atributos Multivaluados

Estos atributos pueden contener múltiples valores dentro del mismo dominio. Imagina que estamos hablando de ti y queremos guardar información sobre ti en una base de datos.

Sabemos que tienes **un solo nombre**, **una sola fecha de cumpleaños**, y **una sola dirección**. Para estos datos, usamos lo que llamamos **atributos simples** porque solo tienen un valor. Por ejemplo:

- Nombre: Teo
- Fecha de cumpleaños: 23 de noviembre
- Dirección: Calle Sol, 15

Pero, ¿qué pasa si tienes **más de un número de teléfono**? Digamos que tienes tres números de teléfonos: el móvil, el fijo de casa y el móvil para hablar con tus ligues. Como tienes **varios valores** para "número de teléfono", usaríamos un **atributo multivaluado**. Esto es solo una manera elegante de decir que puedes tener **más de un valor** para ese dato.

Entonces, en lugar de guardar **un solo número de teléfono**, guardamos **varios**. El **atributo multivaluado** es simplemente una cajita en la que podemos meter **más de un valor** de algo. Así que, cuando tengas algo que pueda tener **varios** valores (como correos o teléfonos), usamos un atributo multivaluado.

El atributo multivaluado se representa con una circunferencia doble como se observa a continuación.

![Atributos](/bases-de-datos/imgs/ud02/ud02_img02_atributos04.svg)

### 4.2.6. Atributos Compuestos

Los **atributos compuestos** son aquellos que pueden descomponerse en sub-atributos que pertenecen a diferentes dominios. Un ejemplo clásico es el **"CCC" (Código Cuenta Corriente)**, que podría descomponerse en:
- **Número de Banco**: `n_banco`.
- **Número de Sucursal**: `n_sucurs`.
- **Número de Cuenta**: `n_cuenta`.

![Atributos](/bases-de-datos/imgs/ud02/ud02_img02_atributos05.svg)

Cada uno de estos sub-atributos pertenece a un dominio distinto y en conjunto forman el atributo compuesto.

### 4.2.7. Atributos Discriminadores o Discriminantes

Estos atributos se utilizan en el contexto de **entidades débiles**, que dependen de una entidad fuerte para su identificación. Los atributos discriminadores ayudan a **distinguir entre las diferentes ocurrencias** de la entidad débil dentro de la entidad fuerte. Se representan con un símbolo especial, como un círculo relleno. Un ejemplo en una base de datos bancaria sería:
- **"num_transacción"** como un atributo discriminatorio dentro de la entidad débil "Cuenta Corriente" (CCC), que depende de la entidad fuerte "Cliente".

*Ver más adelante el apartado 5.5. Dependencia e interrelaciones - Debilidad por dependencia en identificación*

## 4.2.8. Tipos de Atributos, resumen

En resumen, los atributos en una base de datos pueden clasificarse en diferentes tipos, según su función y características:

1. **Identificativos**: Identifican de forma única una instancia de una entidad.
3. **Descriptivos**: Proporcionan características o propiedades adicionales.
7. **Opcionales**: No todas las instancias de una entidad deben tener un valor para estos atributos.
4. **Derivados**: Su valor se calcula a partir de otros atributos.
5. **Multivaluados**: Pueden contener varios valores dentro del mismo dominio.
6. **Compuestos**: Se dividen en varios sub-atributos más pequeños.
2. **Discriminantes**: Distinguen entre instancias de entidades débiles.


Cada uno de estos tipos de atributos desempeña un papel esencial en la representación y organización de los datos, ayudando a asegurar la integridad y coherencia de la base de datos.

---

***Ejercicio 4.1:*** *Clasificación de Atributos.*

Dada la siguiente entidad "Empleado" con los siguientes atributos: *DNI*, *Nombre*, *Apellidos*, *Dirección*, *Teléfono*, *Edad*, *Años de Servicio* y *Email Alternativo*.

1. *Identifica qué tipo de atributo es cada uno (identificativo, descriptivo, opcional, derivado, multivaluado).*
2. *Justifica tu elección para cada atributo.*

***Ejercicio 4.2:*** *Atributos Derivados.*

En una base de datos de una tienda online, tienes la entidad "Pedido" con los siguientes atributos: *Fecha de Pedido*, *Precio Producto*, *Cantidad* y *Precio Total*.

1. *Identifica qué atributo es derivado y explica cómo se calcularía a partir de otros atributos.*
2. *¿Cómo representarías este atributo derivado en un diagrama E/R?*

***Ejercicio 4.3:*** *Atributos Multivaluados.*

Imagina que estás diseñando una base de datos para una escuela. La entidad "Estudiante" tiene los atributos *Nombre*, *Apellido*, *Teléfonos de Contacto* y *Asignaturas Matriculadas*.

1. *Explica por qué los atributos "Teléfonos de Contacto" y "Asignaturas Matriculadas" serían considerados multivaluados.*
2. *Dibuja cómo representarías estos atributos multivaluados en un diagrama E/R.*

***Ejercicio 4.4:*** *Atributos Opcionales.*

Supón que estás diseñando una base de datos para una clínica. La entidad "Paciente" tiene los atributos *Número de Seguro Social*, *Nombre*, *Dirección* y *Correo Electrónico Secundario*.

1. *¿Por qué "Correo Electrónico Secundario" sería un atributo opcional?*
2. *Modifica el diagrama E/R para incluir este atributo opcional.*

***Ejercicio 4.5:*** *Descomposición de Atributos Compuestos.*

En una base de datos bancaria, la entidad "Cuenta Bancaria" tiene el atributo compuesto *"CCC" (Código Cuenta Corriente)*, que se descompone en *Número de Banco*, *Número de Sucursal* y *Número de Cuenta*.

1. *Explica por qué "CCC" es un atributo compuesto.*
2. *Dibuja cómo representarías este atributo compuesto en un diagrama E/R, mostrando la descomposición en sub-atributos.*



# 5. Relaciones

Las **relaciones** son una parte fundamental en un modelo de base de datos, ya que representan las asociaciones entre dos o más entidades. Una relación es la **conexión** o **asociación** que existe entre dos o más entidades. Cada relación tiene un nombre que describe su función o propósito en el contexto de la base de datos.

## Representación Gráfica de Relaciones

En un **diagrama Entidad-Relación (E/R)**, las relaciones se representan mediante **rombos**. El nombre de la relación se coloca en el interior del rombo. 

Generalmente, el nombre de una relación se elige considerando la primera letra de cada entidad. Por ejemplo, si las entidades son **CLIENTE** y **COCHE**, podríamos nombrar la relación como **"C-CO"**. En este caso, como ambas entidades empiezan por “C”, se añaden algunas letras más para hacer referencia a **COCHE**.

![Atributos](/bases-de-datos/imgs/ud02/ud02_img03_clienteCoche01.svg)


También podríamos haber utilizado un nombre más descriptivo para la relación, como **"Compra"** (donde **CLIENTE** compra **COCHE**). Sin embargo, este tipo de nomenclatura puede conducir a confusión a la hora de determinar la **cardinalidad** de la relación cuando estamos aprendiendo.

![Atributos](/bases-de-datos/imgs/ud02/ud02_img03_clienteCoche02.svg)