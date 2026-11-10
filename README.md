MiniStore — Práctica de LEFT, RIGHT y FULL OUTER JOIN

Justificaciones técnicas

1. ¿Por qué utilizamos LEFT JOIN y no INNER JOIN en la Consulta 1?

Utilizamos LEFT JOIN porque necesitábamos identificar los productos del catálogo que nunca fueron vendidos. Este tipo de unión permite conservar todos los productos, independientemente de si tienen ventas asociadas.

Si utilizáramos INNER JOIN, únicamente obtendríamos los productos que registraron ventas, perdiendo información importante para el análisis.

Por ejemplo, los productos 108 (Hub USB-C 7p) y 109 (Parlante Bluetooth) no registraron ventas. Gracias al LEFT JOIN, podemos identificarlos y analizar posibles acciones comerciales para impulsar su venta.

2. ¿Por qué utilizamos RIGHT JOIN en la Consulta 2? ¿Qué tabla está a la izquierda y cuál a la derecha?

Utilizamos RIGHT JOIN porque necesitábamos identificar ventas registradas cuyos productos no existen en el catálogo.

En nuestra consulta, la tabla productos está a la izquierda y la tabla ventas a la derecha. El RIGHT JOIN conserva todos los registros de ventas, aunque no encuentre coincidencias en productos.

Esto permitió detectar la venta 10, asociada al producto 999, que no existe en el catálogo. Este hallazgo podría indicar un error en la carga de datos que debería revisarse.

3. ¿Qué representan los valores NULL en cada resultado?

Los valores NULL indican que no se encontró un registro coincidente en la tabla relacionada.

En la Consulta 1, los productos 108 y 109 presentan venta_id = NULL porque no tienen ventas registradas.

En la Consulta 2, la venta 10 presenta p.producto_id = NULL porque el producto 999 no existe en el catálogo, aunque sí está registrado en la tabla de ventas.

En ambos casos, los valores NULL permiten identificar situaciones relevantes para el análisis y la calidad de los datos.

4. ¿Cuándo utilizaríamos FULL OUTER JOIN en un caso real de negocio?

Utilizaríamos FULL OUTER JOIN cuando necesitamos comparar dos tablas y conservar todos sus registros, independientemente de si existen coincidencias.

Por ejemplo, en MiniStore nos permitió realizar una auditoría completa del catálogo y las ventas, identificando:

9 ventas asociadas correctamente a productos del catálogo.

2 productos que nunca fueron vendidos.

1 venta asociada a un producto inexistente.

Este tipo de consulta resulta útil para detectar inconsistencias, controlar la calidad de los datos y mejorar la confiabilidad de los reportes comerciales.
