# Discovery Server - EcoHabitat Platform

El módulo **discovery-server** forma parte fundamental de la arquitectura de microservicios de la plataforma **EcoHabitat**. Su propósito es actuar como **servidor Eureka** para el registro y descubrimiento dinámico de microservicios dentro del ecosistema distribuido.

---

## Funcionalidad principal

- 📡 Registro automático de microservicios (`ecoaction-service`, `user-service`, `habitat-service`, etc.).
- 🔍 Descubrimiento de servicios mediante nombre lógico (`@FeignClient(name="...")`).
- 🧭 Facilita el balanceo de carga y el desacoplamiento entre componentes.
- 🛡️ Mejora la resiliencia del sistema al permitir la localización flexible de instancias activas.

---

## Configuración

**Archivo:** `application.properties`

```properties
spring.application.name=discovery-server
server.port=8081
```

---

## Clase principal

```java
@SpringBootApplication
@EnableEurekaServer
public class DiscoveryServerApplication {
    public static void main(String[] args) {
        SpringApplication.run(DiscoveryServerApplication.class, args);
    }
}
```

---

## Integración en EcoHabitat

Todos los microservicios del sistema EcoHabitat están configurados como **clientes Eureka**, lo que les permite:

- Registrarse automáticamente al iniciar.
- Descubrir las ubicaciones de otros servicios sin conocer su IP ni puerto.

Este módulo es **esencial** para que la arquitectura sea verdaderamente dinámica, escalable y orientada a servicios.

---

## URL por defecto

Una vez iniciado el servidor, la consola de Eureka estará disponible en:

```
http://localhost:8081
```

Desde allí se puede visualizar el estado del sistema y los microservicios registrados.

---

## Notas técnicas

- Basado en **Spring Cloud Netflix Eureka**.
- Compatible con Spring Boot.
- Utiliza `spring-cloud-starter-netflix-eureka-server` como dependencia principal.

---
