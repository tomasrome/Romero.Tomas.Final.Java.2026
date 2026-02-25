# El Gato Tuerto — Sistema de Rental de Equipamiento Médico
<div align="center">
  <img src="RentalMedicoGatoTuerto\src\rentalmedicogatotuerto\images\logo.png" width="400" alt="Menu Principal">
</div>

---

##  Resumen

**El Gato Tuerto** es un sistema de gestión de alquiler de equipamiento médico desarrollado en Java con interfaz gráfica JavaFX.

La aplicación permite administrar tres tipos de equipos médicos: **Monitores**, **Respiradores** y **Camillas**, ofreciendo operaciones completas de alta, baja, modificación y consulta, junto con persistencia de datos en múltiples formatos.

### ¿Cómo se usa?

1. Completá los campos del formulario correspondiente al tipo de equipo (Monitor / Respirador / Camilla)
2. Hacé clic en **Agregar** para registrarlo en el sistema
3. Seleccioná un equipo de la tabla y usá **Actualizar** para editar sus datos directamente en el formulario
4. Usá los botones del sidebar para filtrar por categoría o gestionar la persistencia
5. Los botones de ordenamiento y **Aumentar 10%** operan sobre la lista completa visible


<div align="center">
  <img src="RentalMedicoGatoTuerto\src\rentalmedicogatotuerto\images\bienvenida.jpg" width="700" alt="Menu Principal">
  <img src="RentalMedicoGatoTuerto\src\rentalmedicogatotuerto\images\gestor.jpg" width="700" alt="Gameplay">
</div>

### Funcionalidades principales

| Funcionalidad | Descripción |
|---|---|
| CRUD completo | Agregar, listar, actualizar y eliminar equipos |
| Filtros | Por tipo: Monitores, Respiradores, Camillas |
| Ordenamiento | Por nombre (A-Z) y por precio |
| Modificación masiva | Aumentar precio un 10% con interfaz funcional |
| Validación de estado | Equipos electrónicos no pueden pasar de EN_MANTENIMIENTO a ALQUILADO directamente |
| Persistencia | Serialización `.dat`, CSV, JSON, exportación TXT |


---

## UML - Diagrama de Clases

<div align="center">
  <img src="RentalMedicoGatoTuerto\src\rentalmedicogatotuerto\images\uml.png" width="700" alt="Menu Principal">
</div>

## ⚙️ Requisitos técnicos implementados

| Requisito | Implementación |
|---|---|
| Clase abstracta base | `EquipoMedico` con 5 atributos y métodos comunes |
| 3 clases derivadas | `Monitor`, `Respirador`, `Camilla` |
| Constructores sobrecargados | 3 constructores por clase con `super()` individual |
| Interfaz con método abstracto | `IInspeccionable` → `validarCambioEstado()` |
| Enumerados | `EstadoEquipo`, `TipoMonitor`, `TipoRespirador`, `TipoCamilla` |
| CRUD con lista genérica | `GestorEquipos` con `List<EquipoMedico>` |
| Interfaz genérica CRUD | `IGestionable<T>` |
| Iterator personalizado | `EquipoIterator` implements `Iterator<EquipoMedico>` |
| Comparable | `EquipoMedico` implements `Comparable` → orden por nombre |
| Comparator x2 | `EquipoComparator.porPrecio()` y `porEstado()` |
| Wildcards `? extends` | `calcularPrecioPromedio(List<? extends EquipoMedico>)` |
| Wildcards `? super` | `exportarTXT(List<? super EquipoMedico>)` |
| Interfaces funcionales | `Consumer` en `modificarTodos()`, `Predicate` en `filtrar()` |
| Serialización `.dat` | `ObjectOutputStream` / `ObjectInputStream` |
| CSV | Escritura manual con `BufferedWriter` |
| JSON | Escritura manual con `BufferedWriter` |
| TXT | `BufferedWriter` con encabezado descriptivo |
| JavaFX | Interfaz completa con sidebar, tabla, formularios y filtros |
| Excepciones propias | `EquipoNoEncontradoException`, `EquipoNoDisponibleException` |
| Diagrama UML | Incluido en este README |

---
---

*UTN Avellaneda — Tecnicatura Universitaria en Programación — 2024*
