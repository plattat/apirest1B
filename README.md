pruebas unitarias usando Mockito

Se ha creado la clase PersonServiceTest.java para la ejecución de las pruebas unitarias.
Creamos el método testCreatePersona, para validar que la persona sea creada correctamente en la base de datos.
 








Con el siguiente método testGetAllPerson, validamos que en la base de datos tenga las dos personas en la listas, John y Jane.
 

Con el método testDeletePerson validamos que la persona sea eliminada de la base de datos.
 
Resultados de las pruebas se confirma que fue obtuvieron un resultado exitoso.
 

Se procedió a ejecutar las pruebas en postman



Base de datos:
 


Se crea una persona 
  

Se confirma que crea a Andres

 

Ahora con Postman validamos que podamos ver la información de los usuarios:
 






Se procede a validar la eliminación de un usuario:
Seleccionamos el ID de Andres 
 

Se confirma en la base de datos que fue eliminada.

 



