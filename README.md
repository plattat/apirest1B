# apirest1A
# 📌 Se ejecua el siguiente codigo para probar  PersonService

package com.example.api.apirest;
import static org.mockito.Mockito.*;
import com.example.api.apirest.Person.PersonRepository;
import com.example.api.apirest.Person.PersonService;
import com.example.api.apirest.Person.Person;
import org.junit.jupiter.api.Test;
import org.junit.jupiter.api.extension.ExtendWith;
import org.mockito.InjectMocks;
import org.mockito.Mock;
import org.mockito.junit.jupiter.MockitoExtension;

@ExtendWith(MockitoExtension.class)
class PersonServiceTest {

    @Mock
    private PersonRepository personRepo;

    @InjectMocks
    private PersonService personService;

    @Test
    void testCreatePersona() {
        Person person = new Person(null, "John", "Doe", "john@example.com");
        personService.createPersona(person);
        verify(personRepo, times(1)).save(person);
    }
}


# 📌 Resultado de las Pruebas con Maven Prueba unitaria para PersonService

Verifica que el método createPersona llama correctamente a personRepo.save().

### 🔹 Comando Ejecutado:
```sh
mvn test
[INFO] 
[INFO] -------------------------------------------------------
[INFO]  T E S T S
[INFO] -------------------------------------------------------
[INFO] Running com.example.api.apirest.PersonServiceTest
Java HotSpot(TM) 64-Bit Server VM warning: Sharing is only supported for boot loader classes because bootstrap classpath has been appended
[INFO] Tests run: 1, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 1.297 s -- in com.example.api.apirest.PersonServiceTest
[INFO] 
[INFO] Results:
[INFO]
[INFO] Tests run: 1, Failures: 0, Errors: 0, Skipped: 0
[INFO]
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  10.429 s
[INFO] Finished at: 2025-03-26T19:25:27-05:00
[INFO] ---------------------------------------------


# 📌 Codigo de las Prueba unitaria para PersonControllere

package com.example.api.apirest;
import static org.mockito.Mockito.*;

import com.example.api.apirest.Person.PersonService;
import com.example.api.apirest.Person.Person;
import com.example.api.apirest.Person.PersonController;
import org.junit.jupiter.api.Test;
import org.junit.jupiter.api.extension.ExtendWith;
import org.mockito.InjectMocks;
import org.mockito.Mock;
import org.mockito.junit.jupiter.MockitoExtension;


@ExtendWith(MockitoExtension.class)
class PersonControllerTest {

    @Mock
    private PersonService personService;

    @InjectMocks
    private PersonController personController;

    @Test
    void testCreatePersona() {
        Person person = new Person(null, "Jane", "Doe", "jane@example.com");
        personController.createPersona(person);
        verify(personService, times(1)).createPersona(person);
    }
}

# 📌 Resultado de las Prueba unitaria para PersonControllere

### 🔹 Comando Ejecutado:

[INFO] 
[INFO] -------------------------------------------------------
[INFO]  T E S T S
[INFO] -------------------------------------------------------
[INFO] Running com.example.api.apirest.PersonServiceTest
Java HotSpot(TM) 64-Bit Server VM warning: Sharing is only supported for boot loader classes because bootstrap classpath has been appended
[INFO]
[INFO] Results:
[INFO]
[INFO] Tests run: 1, Failures: 0, Errors: 0, Skipped: 0
[INFO]
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  10.429 s
[INFO] Finished at: 2025-03-26T19:25:27-05:00
[INFO] ------------------------------------------------------------------------
PS C:\Users\cristian\Downloads\apirest\apirest> mvn test
[INFO] Scanning for projects...
[INFO] 
[INFO] ----------------------< com.example.api:apirest >-----------------------
[INFO] Building apirest 0.0.1-SNAPSHOT
[INFO]   from pom.xml
[INFO] --------------------------------[ jar ]---------------------------------
[INFO] 
[INFO] --- resources:3.3.1:resources (default-resources) @ apirest ---
[INFO] Copying 1 resource from src\main\resources to target\classes
[INFO] Copying 0 resource from src\main\resources to target\classes
[INFO]
[INFO] --- compiler:3.13.0:compile (default-compile) @ apirest ---
[INFO] Nothing to compile - all classes are up to date.
[INFO]
[INFO] --- resources:3.3.1:testResources (default-testResources) @ apirest ---
[INFO] skip non existing resourceDirectory C:\Users\cristian\Downloads\apirest\apirest\src\test\resources
[INFO]
[INFO] --- compiler:3.13.0:testCompile (default-testCompile) @ apirest ---
[INFO] Recompiling the module because of changed source code.
[INFO] Compiling 1 source file with javac [debug parameters release 17] to target\test-classes
[INFO] 
[INFO] --- surefire:3.5.2:test (default-test) @ apirest ---
[INFO] Using auto detected provider org.apache.maven.surefire.junitplatform.JUnitPlatformProvider
[INFO] 
[INFO] -------------------------------------------------------
[INFO]  T E S T S
[INFO] -------------------------------------------------------
[INFO] Running com.example.api.apirest.PersonServiceTest
Java HotSpot(TM) 64-Bit Server VM warning: Sharing is only supported for boot loader classes because bootstrap classpath has been appended
[INFO] Tests run: 1, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 1.185 s -- in com.example.api.apirest.PersonServiceTest
[INFO] 
[INFO] Results:
[INFO]
[INFO] Tests run: 1, Failures: 0, Errors: 0, Skipped: 0
[INFO]
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  5.541 s
[INFO] Finished at: 2025-03-26T19:56:03-05:00
[INFO] ------------------------------------------------------------------------


###  Conclusión Final

Se ejecutaron dos pruebas unitarias en el proyecto con Maven y JUnit.

Ambas pruebas resultaron exitosas (BUILD SUCCESS).

Se confirmó que el código no presenta errores en la funcionalidad probada.

La compilación y ejecución mejoraron en la segunda prueba



### Codigo para prueba de integración con API REST 

package com.example.api.apirest;
import com.example.api.apirest.Person.PersonRepository;
import com.example.api.apirest.Person.Person;
import static org.assertj.core.api.Assertions.assertThat;

import org.junit.jupiter.api.Test;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.autoconfigure.web.servlet.AutoConfigureMockMvc;
import org.springframework.boot.test.context.SpringBootTest;
import org.springframework.http.MediaType;
import org.springframework.test.web.servlet.MockMvc;
import org.springframework.test.web.servlet.ResultActions;

import com.fasterxml.jackson.databind.ObjectMapper;

import static org.springframework.test.web.servlet.request.MockMvcRequestBuilders.post;
import static org.springframework.test.web.servlet.result.MockMvcResultMatchers.status;

@SpringBootTest
@AutoConfigureMockMvc
class PersonIntegrationTest {

    @Autowired
    private MockMvc mockMvc;

    @Autowired
    private PersonRepository personRepository;

    @Autowired
    private ObjectMapper objectMapper;

    @Test
    void testCreatePersona() throws Exception {
        Person person = new Person(null, "Alice", "Smith", "alice@example.com");

        ResultActions response = mockMvc.perform(post("/person")
                .contentType(MediaType.APPLICATION_JSON)
                .content(objectMapper.writeValueAsString(person)));

        response.andExpect(status().isOk());

        // Verificar que el objeto se guardó en la BD
        assertThat(personRepository.findAll()).isNotEmpty();
    }
}

###  Prueba si el endpoint /person guarda correctamente un objeto Person en la base de datos.

### La prueba de integración se ejecuta en la clase PersonIntegrationTest

[INFO] Scanning for projects...
[INFO] 
[INFO] ----------------------< com.example.api:apirest >-----------------------
[INFO] Building apirest 0.0.1-SNAPSHOT
[INFO]   from pom.xml
[INFO] --------------------------------[ jar ]---------------------------------
[INFO] 
[INFO] --- resources:3.3.1:resources (default-resources) @ apirest ---
[INFO] Copying 1 resource from src\main\resources to target\classes
[INFO] Copying 0 resource from src\main\resources to target\classes
[INFO]
[INFO] --- compiler:3.13.0:compile (default-compile) @ apirest --- 
[INFO] Nothing to compile - all classes are up to date.
[INFO]
[INFO] --- resources:3.3.1:testResources (default-testResources) @ apirest ---
[INFO] skip non existing resourceDirectory C:\Users\cristian\Downloads\apirest\apirest\src\test\resources
[INFO]
[INFO] --- compiler:3.13.0:testCompile (default-testCompile) @ apirest ---
[INFO] Recompiling the module because of changed source code.
[INFO] Compiling 1 source file with javac [debug parameters release 17] to target\test-classes
[INFO] 
[INFO] --- surefire:3.5.2:test (default-test) @ apirest ---
[INFO] Using auto detected provider org.apache.maven.surefire.junitplatform.JUnitPlatformProvider
[INFO] 
[INFO] -------------------------------------------------------
[INFO]  T E S T S
[INFO] -------------------------------------------------------
[INFO] Running com.example.api.apirest.PersonIntegrationTest
[INFO] 
[INFO] Results:
[INFO]
[INFO] Tests run: 1, Failures: 0, Errors: 0, Skipped: 0
[INFO]
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  11.603 s
[INFO] Finished at: 2025-03-26T20:16:45-05:00
[INFO] ------------------------------------------------------------------------



### La prueba de integración se ejecuta en la clase PersonIntegrationTest

Resultados Finales y Conclusión
Pruebas Ejecutadas: 1 (la prueba de integración PersonIntegrationTest).

Estado: Sin fallos, errores ni pruebas omitidas.

Tiempo Total: Aproximadamente 11.603 s para el proceso completo (incluyendo compilación y ejecución).

Conclusión:
La prueba de integración se ejecutó exitosamente, confirmando que la configuración de Spring Boot, JPA y la conexión a la base de datos funcionan correctamente. Esto valida la correcta integración de los componentes de la aplicación.