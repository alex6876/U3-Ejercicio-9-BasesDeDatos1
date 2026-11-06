# Modelo Relacional de Bases de Datos 9



## Descripción



Este documento detalla el esquema y la estructura del modelo relacional de bases de datos para una plataforma de educación o cursos online, enfocado en el control de instructores, cursos, módulos, lecciones, estudiantes, inscripciones, evaluaciones, preguntas e intentos de exámenes.

---

## Estructura de Tablas y Atributos



### 1. Instructor



* **PK (Clave Primaria):** `id_Instructor`


* **Atributos:**
* `nombre`


* `biografia`


* `especialidad`


* `contacto`





### 2. Curso



* **PK (Clave Primaria):** `id_Codigo_Curso`


* **Atributos:**
* `titulo`


* `precio`


* `descripción`


* `nivel_Dificultad`




* **FK (Claves Foráneas):**
* `id_Instructor` (asociado a la tabla Instructor)





### 3. Modulo



* **PK (Clave Primaria):** `id_Modulo`


* **Atributos:**
* `nombre`


* `descripción`


* `orden_Secuencial`




* **FK (Claves Foráneas):**
* `id_Codigo_Curso` (asociado a la tabla Curso)





### 4. Lección



* **PK (Clave Primaria):** `id_Lección`


* **Atributos:**
* `titulo`


* `tipo`


* `duracion_estimada`


* `enlace_contenido`




* **FK (Claves Foráneas):**
* `id_Modulo` (asociado a la tabla Modulo)





### 5. Estudiantes



* **PK (Clave Primaria):** `id_Estudiante`


* **Atributos:**
* `nombre`


* `apellido`


* `Fecha_registro`


* `Email`





### 6. Inscripción



* **PK (Clave Primaria):** `id_inscripcion`


* **Atributos:**
* `Porcentaje_avance`


* `fecha_Alta`


* `Estado_finalización`




* **FK (Claves Foráneas):**
* `id_Estudiante` (asociado a la tabla Estudiantes)


* `id_Codigo_Curso` (asociado a la tabla Curso)





### 7. Evaluaciones



* **PK (Clave Primaria):** `id_Evaluación`


* **Atributos:**
* `titulo`


* `tipo`


* `fecha_creación`




* **FK (Claves Foráneas):**
* `id_Codigo_Curso` (asociado a la tabla Curso)





### 8. Pregunta



* **PK (Clave Primaria):** `id_Pregunta`


* **Atributos:**
* `Enunciado`


* `Opcion_A`


* `Opcion_B`


* `Opcion_C`


* `Opcion_correcta`




* **FK (Claves Foráneas):**
* `id_Evaluación` (asociado a la tabla Evaluaciones)





### 9. Intentos



* **PK (Clave Primaria):** `id_Intento`


* **Atributos:**
* `Fecha_Intento`


* `Calificación`


* `Estado`




* **FK (Claves Foráneas):**
* `id_Estudiante` (asociado a la tabla Estudiantes)


* `id_Evaluación` (asociado a la tabla Evaluaciones)





---

## Relaciones Principales



* **Instructor y Curso:** Un instructor imparte o crea múltiples cursos vinculados mediante su identificador `id_Instructor`.


* **Curso, Modulo y Lección:** Un curso se divide en varios módulos (`id_Codigo_Curso`), y cada módulo contiene diversas lecciones (`id_Modulo`).


* **Estudiantes y Curso (Inscripción):** La relación entre estudiantes y los cursos a los que acceden se gestiona a través de la tabla intermedia `Inscripción` utilizando `id_Estudiante` e `id_Codigo_Curso`.


* **Curso y Evaluaciones:** Los cursos pueden incluir evaluaciones asociadas mediante `id_Codigo_Curso`.


* **Evaluaciones y Pregunta:** Cada evaluación está compuesta por múltiples preguntas relacionadas mediante `id_Evaluación`.


* **Estudiantes y Evaluaciones (Intentos):** Los intentos realizados por los estudiantes en las evaluaciones se registran en la tabla `Intentos`, vinculando `id_Estudiante` e `id_Evaluación`.
