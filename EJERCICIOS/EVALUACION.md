## Práctica 1.

1. Introducción a base de datos

Objetivo: Identificar el nivel de comprensión de los conceptos de base de datos,
mediante preguntas abiertas.
 
Preguntas:

1. ¿Cuáles son las cinco funciones principales del administrador de bases de datos?
(valor 1.5)

  Las funciones principales de un administrador de base de datos son: reteener la información de la base de datos, , asegurar el buen funcionamineto de la base de datos, evitar la perdida de datos, solicionar incidentes y dar seguridad a los datos.

2. Indíque cinco responsabilidades del sistema gestor de bases de datos (valor 1.5)

   Las funciones de un gestor de base de datos son: instalar configurar y gestionar la base de datos, dar soporte a los desarrolaldores y usuarios, dar disponibilidad de la base de datos

3. En una BD al usuario del sistema se le brindarán recursos para realizar diversas
operaciones sobre estos archivos, tales como: (valor 1.5)

normalmmente el usuario podrá crear o eliminar cuentas, almacenar datos, modificarlos, o trasnferirlos.

4. ¿Qué es un Sistema de Información? (valor 1.5)
 un sistema de información almacena, ordena los datos y los hace disponibles para utilizarlos.



## Práctica 2.

2. Diseño de un modelo relacional

Objetivo: Representar desde un modelo entidad relación un problema


Ejercicio:

Tenemos que diseñar una base de datos sobre proveedores y disponemos de la siguiente
información:

Realiza el modelo entidad relación. (valor 6)

Tenemos esta información sobre una cadena editorial:

● La editorial tiene varias sucursales, con su domicilio, teléfono y un código de
sucursal.

● Cada sucursal tiene varios empleados, de los cuales tendremos su nombre,
apellidos, NIF y teléfono. Un empleado trabaja en una única sucursal.

● En cada sucursal se publican varias revistas, de las que almacenaremos su título,
número de registro, periodicidad y tipo.

● Una revista puede ser publicada por varias sucursales.

● La editorial tiene periodistas (que no trabajan en las sucursales) que pueden
escribir artículos para varias revistas. Almacenaremos los mismos datos que para
los empleados, añadiendo su especialidad.

● También es necesario guardar las secciones fijas que tiene cada revista, que
constan de un título y una extensión.

● Para cada revista, almacenaremos información de cada ejemplar, que incluirá la
fecha, número de páginas y el número de ejemplares vendidos.

![BD_art_1](https://user-images.githubusercontent.com/19659201/170092272-d4216750-89ed-4635-8b8f-e1a8946728e1.jpg)


https://www.db-fiddle.com/f/4ySko9dvt3cHoPnHAhY1FJ/2

CREATE DATABASE editorial;
USE editorial;
 
CREATE TABLE sucursales(
  cod_sucursal INT UNSIGNED PRIMARY KEY,
  domicilio VARCHAR(100) NOT NULL,
  telefono char(10) NOT NULL  
);

CREATE TABLE revistas(
  num_registro INT UNSIGNED PRIMARY KEY,
  título varchar(50),
  periodicidad varchar(50),
  tipo varchar(50)
);
 
CREATE TABLE secciones(
  id_seccion INT UNSIGNED PRIMARY KEY,
  título varchar(50) NOT NULL,
  revista INT UNSIGNED,
  extensión varchar(30),
  FOREIGN KEY (revista) REFERENCES revistas(num_registro)  
);
 
CREATE TABLE ejemplares (
  num_ejemplar INT UNSIGNED PRIMARY KEY,
  fecha DATETIME,
  copias_vendidas INT UNSIGNED NOT NULL,
  num_paginas INT UNSIGNED NOT NULL,
  revista INT UNSIGNED,
  FOREIGN KEY(revista) REFERENCES revistas(num_registro)
);
 
CREATE TABLE empleados (
  CURP CHAR(18) NOT NULL PRIMARY KEY,
  nombre VARCHAR(50) NOT NULL,
  domicilio VARCHAR(100) NOT NULL,
  telefono char(10) NOT NULL,
  sucursal INT UNSIGNED NOT NULL,
  FOREIGN KEY(sucursal) REFERENCES sucursales(cod_sucursal)
);


CREATE TABLE periodistas (
  CURP CHAR(18) NOT NULL PRIMARY KEY,
  nombre VARCHAR(50) NOT NULL,
  domicilio VARCHAR(100) NOT NULL,
  telefono char(10) NOT NULL,
  especialidad VARCHAR(20) NOT NULL
 );
 
 CREATE TABLE publicaciones (
   cod_sucursal INT UNSIGNED NOT NULL,
   cod_revista INT UNSIGNED NOT NULL,
   FOREIGN KEY (cod_sucursal) REFERENCES sucursales(cod_sucursal),
   FOREIGN KEY (cod_revista) REFERENCES revistas(num_registro)   
 );

CREATE TABLE periodistas_revistas (
  CURP CHAR(18) NOT NULL,
  cod_revista INT UNSIGNED NOT NULL,
  FOREIGN KEY (CURP) REFERENCES periodistas(CURP),
  FOREIGN KEY (cod_revista) REFERENCES revistas(num_registro) 
);



