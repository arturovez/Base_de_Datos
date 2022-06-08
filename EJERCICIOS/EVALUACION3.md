
## Práctica 4
### Data warehouse

Objetivo: Demostrar la identificación de los elementos que componen data warehouse y
su esquema

Ejercicio:

1. ¿Qué es un DataWarehouse?(valor 2)

un data Warehouse, o almacen de datos, es un sistema que combina, almacena y ordena información de diferentes fuentes en un almacén ed datos único, con la infraestructura y disponibilidad adecuadas.

2. Realiza un diseño del modelo en estrella (valor 2)

![imagen](https://user-images.githubusercontent.com/19659201/171882931-3746eacf-0a0a-4d38-8601-b7a11ed1ae24.png)


3. Realiza un diseño del modelo copo de nieve (valor 2)

![imagen](https://user-images.githubusercontent.com/19659201/171883093-4440b10c-7865-4de2-9c71-cd1b0918dc60.png)



## Práctica 7
### Funciones en SQL
Objetivo: Demostrar el uso y aplicación en una base de datos para mejorar la gestión

Ejercicio:

https://www.db-fiddle.com/f/tPUBoGD2vdujf4Fwp79adG/1

1. Calcula el número total de productos que hay en la tabla productos. (valor 4.5)

SELECT COUNT(cod_prod) FROM tienda_informatica.productos;
![imagen](https://user-images.githubusercontent.com/19659201/171658644-eaef68f3-e667-4677-b4de-b2c2f8e42241.png)


2. Muestra el número total de productos que tiene cada uno de los fabricantes. El listado
también debe incluir los fabricantes que no tienen ningún producto. El resultado
mostrará dos columnas, una con el nombre del fabricante y otra con el número de
productos que tiene. Ordene el resultado descendentemente por el número de
productos. (valor 4.5)

SELECT nombre_fabricante, COUNT(nombre_prod) FROM fabricantes  LEFT JOIN productos ON productos.cod_fab1=fabricantes.cod_fab GROUP BY(cod_fab);

![imagen](https://user-images.githubusercontent.com/19659201/171666861-dc75f9a3-2f28-4450-be13-8382beb31f60.png)

3. Muestra el precio máximo, precio mínimo y precio medio de los productos de cada
uno de los fabricantes. El resultado mostrará el nombre del fabricante junto con los
datos que se solicitan. (valor 4.5)

SELECT nombre_fabricante, MAX(precio), MIN(precio), AVG(precio) FROM productos LEFT JOIN fabricantes on productos.cod_fab1=fabricantes.cod_fab GROUP BY(cod_fab1);

![imagen](https://user-images.githubusercontent.com/19659201/171667108-18c343a0-1ff5-4816-bb64-325e03cec7aa.png)

4. Muestra el nombre de cada fabricante, junto con el precio máximo, precio mínimo,
precio medio y el número total de productos de los fabricantes que tienen un precio
medio superior a 200€. Es necesario mostrar el nombre del fabricante. (valor 4.5)

SELECT nombre_fabricante, MAX(precio), MIN(precio), AVG(precio) AS Prom, COUNT(cod_prod) AS 'Mayor a 200' FROM productos LEFT JOIN fabricantes on productos.cod_fab1=fabricantes.cod_fab GROUP BY(cod_fab1) HAVING Prom > 200;

![imagen](https://user-images.githubusercontent.com/19659201/171668824-cbcd3f7d-c289-4a04-a275-3c674a66aff2.png)


## Práctica 8.
### Disparadores (Triggers)

EV 4 ------>
