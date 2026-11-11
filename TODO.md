# TODO — Laboratorio 4: Actas municipales en un grafo (Neo4j)

> Guía oficial: [labs/lab4-neo4j/README.md](labs/lab4-neo4j/README.md) · notebook: [labs/lab4-neo4j/Lab4.ipynb](labs/lab4-neo4j/Lab4.ipynb)
> **Entrega:** miércoles 11 de noviembre de 2026, 11:00 pm. PDF (máximo **4 páginas**) en TEC Digital, con el
> enlace al repositorio donde está el notebook completado.

Reglas:

- El informe pega **salidas del notebook**; si no las trae, cada criterio que dependa de una cifra vale la mitad.
- Un TODO en `PENDIENTE` o `VERIFICACIÓN FALLÓ` no suma la parte de código de su criterio.
- Commits de los tres integrantes, repartidos en los días.

---

## Reparto del trabajo

Se reparte como la rúbrica: cada persona tiene sus TODO y las preguntas del informe que dependen de ellos.

| Persona | Nombre | TODO | Preguntas del informe | Puntos de la rúbrica | Además |
| --- | --- | --- | --- | --- | --- |
| **A** | Fabricio Mena | 1 y 2 (carga del grafo, paso 5) | 2 (captura del paso 6.3 y `cargo`) y 4 (`CREATE` contra `MERGE`) | 25 | repo, entorno, base del informe, ejecución final y PDF |
| **B** | Alisson Redondo | 3 y 4 (uno y dos saltos, paso 6) | 3 (consultas, SQL y `JOIN` del tercer salto) y 1 (delimitación) | 20 + 15 = 35 | — |
| **C** | Christopher Rodriguez | 5 (vector y camino, paso 7) | 5 (solo vector contra vector + acta, 128 tokens) y 6 (lectura crítica del paso 9) | 20 + 20 = 40 | — |

A tiene menos puntos de rúbrica, pero arma el repo, deja el grafo cargado para los demás y hace la
ejecución final y el PDF.

### Dependencias

| Necesita | Depende de |
| --- | --- |
| TODO 3 | TODO 2 (fragmentos) |
| TODO 4 | TODO 1 (personas) y TODO 2 |
| TODO 5 | TODO 2 (fragmentos con su vector) |
| Pasos 8.5 y 9 (pregunta 6) | TODO 5 |
| Pregunta 1 | nada: sale del paso 2, se puede hacer desde ya |

Por eso A hace primero los TODO 1 y 2 y los deja en `develop`; B y C parten de ahí.

### Calendario sugerido

| Fecha | Quién | Qué |
| --- | --- | --- |
| jue 5 – vie 6 nov | A | repo, TODO 1 y 2, base del informe, fusión en `develop` |
| vie 6 – dom 8 nov | B y C | sus TODO en su rama (B puede adelantar la pregunta 1 desde ya) |
| lun 9 nov | B y C | sus preguntas del informe y PR de su rama a `develop` |
| mar 10 nov | A | ejecución final del notebook, captura, PDF y lista de control |
| mié 11 nov, 11:00 pm | A | subir el PDF y el enlace al repo a TEC Digital |

### Flujo de ramas

- `main`: solo el entorno y este archivo; se fusiona `develop` al final.
- `develop`: integración. Cada quien abre un PR de su rama a `develop`.
- Ramas personales: `fabricio`, y B y C crean la suya **desde `develop`** después de que estén los TODO 1 y 2.
- En el notebook cada quien edita **solo las celdas de su TODO**.
- Antes de cada commit, limpie las salidas del notebook para no chocar al fusionar:
  `docker compose --profile lab4 exec -T lab4-notebook jupyter nbconvert --clear-output --inplace labs/lab4-neo4j/Lab4.ipynb`.
  La versión con salidas la deja A en la ejecución final.

---

## Checklist — Persona A

- [x] Crear el repo en GitHub con el entorno del curso, ramas `main`, `develop` y `fabricio`
- [x] Invitar a B y C como colaboradores
- [x] Hacer público el repo (se creó privado) o darle acceso al profesor antes de entregar
- [x] `make lab4-up` y correr el notebook hasta el paso 5
- [x] **TODO 1** (paso 5.3): `MERGE` de `Persona` y de `PARTICIPA_EN`, con `rol` y `cargo` en la relación → `OK`
- [x] **TODO 2** (paso 5.4): `MERGE` de `Fragmento`, sus propiedades y `CONTIENE` → `OK`
- [x] Base del informe `labs/lab4-neo4j/REPORTE.tex` con las secciones de las seis preguntas
- [x] Pregunta 4: qué pasa con `CREATE` en lugar de `MERGE` en el TODO 1
- [x] Pregunta 2: explicación de por qué `cargo` va en `PARTICIPA_EN`
- [x] Paso 6.3: captura del navegador de Neo4j para la pregunta 2
- [x] Fusionar `fabricio` en `develop`
- [x] Ejecución final del notebook completo con salidas, guardado en el repo
- [ ] Armar el PDF (máximo 4 páginas) y revisar la lista de control
- [ ] Fusionar `develop` en `main` y entregar en TEC Digital

## Checklist — Persona B

- [X] Crear la rama `alisson` desde `develop` (con los TODO 1 y 2 ya fusionados)
- [X] **TODO 3** (paso 6.1): un salto, fragmentos por acta con agregación → `OK`
- [X] **TODO 4** (paso 6.2): dos saltos `Persona → Acta → Fragmento` filtrado por palabra → `OK`
- [x] Pregunta 3: consultas de los TODO 3 y 4 con su resultado, SQL equivalente y cuántos `JOIN` necesitaría un tercer salto
- [x] Pregunta 1: cuántos documentos publica el índice, cuántas actas entraron al grafo y qué haríamos con un PDF escaneado (cifras de la salida del paso 2)
- [x] PR de `alisson` a `develop`

## Checklist — Persona C

- [x] Crear la rama `chris` desde `develop` (con los TODO 1 y 2 ya fusionados)
- [x] **TODO 5** (paso 7): recorrido de caminos después de la búsqueda vectorial (`OPTIONAL MATCH`, `collect`) → `OK`
- [x] Pregunta 5: «solo vector» contra «vector + acta» con la salida del TODO 5, y el papel de los 128 tokens (salida del paso 8.2)
- [x] Pregunta 6: para las tres preguntas del paso 9, si la respuesta es correcta según el contexto recuperado, con las alucinaciones señaladas
- [x] PR de `chris` a `develop`

---

## Lista de control final

- [x] Los cinco TODO en `OK` en el resumen final del notebook
- [x] El notebook del repo tiene las salidas de la ejecución final
- [ ] La captura del paso 6.3 está en el informe
- [ ] Las seis preguntas respondidas con salidas pegadas del notebook
- [ ] PDF de 4 páginas como máximo, con el enlace al repo
- [ ] Commits de los tres integrantes, repartidos en los días
