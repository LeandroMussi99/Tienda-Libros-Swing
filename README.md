# 📚 Tienda de Libros — Aplicación de Escritorio con Swing y Spring Boot

Aplicación de escritorio construida con **Spring Boot 3**, **Swing** y **Spring Data JPA** para administrar el catálogo de una **tienda de libros**.  
Permite crear, modificar, eliminar y listar libros mediante una interfaz gráfica amigable conectada a una base de datos MySQL.

---

## 🖼️ Vista del sistema

> Interfaz principal de la aplicación, donde se gestionan los libros con operaciones CRUD.

<img width="881" height="688" alt="tienda libros" src="https://github.com/user-attachments/assets/7eeae245-c30d-44b9-91ab-e1cda0eac2d7" />

---

## ✨ Características principales

- 🧾 **Gestión completa de libros:** alta, baja, modificación y listado.  
- 🪄 **Interfaz Swing:** formulario con `JTable` para visualizar los registros en tiempo real.  
- 🧱 **Arquitectura MVC + Spring Boot:** componentes desacoplados (vista, servicio y repositorio).  
- ⚙️ **Persistencia con JPA y MySQL:** integración con Hibernate y manejo automático de entidades.  
- 🧩 **Uso de Lombok:** para reducir el código repetitivo en la entidad `Libro`.  
- 💡 **Inicialización de interfaz como bean:** el arranque usa `headless(false)` para habilitar la GUI.  

---

## 🧰 Requisitos previos

- ☕ **Java 21**  
- 🧱 **Maven 3.9+**  
- 🗄️ **MySQL 8** (o versión compatible)

---

## ⚙️ Configuración

1. Editá el archivo `src/main/resources/application.properties` con tus credenciales:

   ```properties
   spring.datasource.url=jdbc:mysql://localhost:3306/tienda_libros_db?createDatabaseIfNotExist=true&useSSL=false&serverTimezone=UTC
   spring.datasource.username=tu_usuario
   spring.datasource.password=tu_password
   spring.jpa.hibernate.ddl-auto=update
   spring.jpa.show-sql=true
   ```
2.Asegurate de que MySQL esté corriendo.
3.(Opcional) Podés modificar los logs en logback-spring.xml.

##🚀 Ejecución

Compilá y ejecutá el proyecto con Maven: mvn spring-boot:run
El sistema inicializa el contexto de Spring y abre automáticamente el formulario Swing.
Desde allí podrás agregar, modificar o eliminar libros, y los cambios se reflejarán directamente en la base de datos.


##🧩 Estructura del proyecto

```text
src/
 ├─ main/
 │   ├─ java/gm/tienda_libros/
 │   │   ├─ modelo/Libro.java                  # Entidad JPA
 │   │   ├─ repositorio/LibroRepositorio.java  # Capa de acceso a datos
 │   │   ├─ servicio/                         # Interfaces y clases de servicio
 │   │   ├─ vista/LibroForm.java              # Formulario principal (Swing)
 │   │   └─ TiendaLibrosApplication.java      # Clase principal con headless(false)
 │   └─ resources/
 │       ├─ application.properties
 │       └─ logback-spring.xml
 └─ test/
     └─ java/gm/tienda_libros/TiendaLibrosApplicationTests.java
```

## 🧠 Funcionamiento interno

- La interfaz Swing utiliza un DefaultTableModel para mostrar los libros.
- Cada acción (Agregar, Modificar, Eliminar) se conecta a métodos del LibroServicio.
- El método listarLibros() refresca los datos en la tabla después de cada operación.
- El formulario restringe la selección a una fila por vez (ListSelectionModel.SINGLE_SELECTION).

