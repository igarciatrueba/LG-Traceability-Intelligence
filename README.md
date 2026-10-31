<p align="center">
  <img src="assets/banner.svg" alt="LGTI · LG Traceability Intelligence" width="100%">
</p>

# LGTI · LG Traceability Intelligence

Proyecto universitario (ADE + Business Analytics) de una plataforma de trazabilidad, calidad y valoración económica del riesgo para baterías de vehículos eléctricos. El caso de referencia son las retiradas del Chevrolet Bolt.

> **Aviso.** LGTI es una empresa hipotética, sin ninguna relación real con LG. Los datos sintéticos son de elaboración propia y no son datos internos ni históricos de LG Energy Solution (LGES). El proyecto demuestra un método; no afirma que exista un defecto real.

## Qué hace el proyecto
Cuando un vehículo se retira, las unidades sin evidencia de su origen se retiran por prudencia. LGTI registra la cadena proveedor → lote → celda → módulo → pack → vehículo para poder excluir de forma segura las unidades que no están afectadas. Regla: **sin evidencia de genealogía completa, la unidad no se excluye.**

## Contenido del repositorio
| Carpeta | Qué contiene |
|---|---|
| `front/` | `index.html`: front web (HTML + Three.js) con las páginas Inicio, Seguimiento, Calidad e Impacto económico |
| `datos/` | Base maestra (`LGTI_master_db.xlsx`), datos del front (`dataset_sintetico.json`) y tablas de cifras del dossier |
| `sas/` | Programas SAS de carga, CSV de las tablas, guía de edición del informe y capturas de Visual Analytics |
| `dossier/` | Documentación del proyecto (PDF) |
| `docs/` | Contexto y tabla maestra de cifras (fuente única de coherencia) |
| `assets/` | Banner del README |

## Cómo abrir el front
Abre `front/index.html` en el navegador. Si el navegador bloquea la carga de archivos locales, sirve la carpeta con un servidor sencillo:

```
cd front
python3 -m http.server 8000
```

y entra en `http://localhost:8000`.

## Datos
- **Datos públicos reales (NHTSA):** retiradas, reclamaciones e informes trimestrales. Por tamaño no se incluyen los ficheros originales. Se descargan de la página de conjuntos de datos de NHTSA (https://www.nhtsa.gov/nhtsa-datasets-and-apis): `FLAT_RCL_POST_2010`, `FLAT_RCL_Qrtly_Rpts`, los ficheros `COMPLAINTS_RECEIVED_*` y los archivos de diseño `RCL.txt`, `RCL_Qtrly_Rpts.txt` y `CMPL.txt`.
- **Costes públicos:** retiradas del Bolt y del Kona EV (tabla `Costs` de la base maestra).
- **Capa sintética (elaboración propia, datos sintéticos):** 1.800 registros y 605.250 unidades para demostrar la genealogía y la predicción.
- La base maestra es un conjunto relacional de tablas más una tabla analítica por campaña. Cada cifra distingue entre dato público observado, cálculo derivado, supuesto académico y objetivo de diseño.

## SAS Visual Analytics
El informe "LGES Traceability Intelligence" está en un servidor de SAS y no se puede incluir como archivo. En `sas/` están los programas de carga (`cargar_masterdb.sas`, `cargar_coherencia.sas`), los CSV que leen, la guía manual de edición y las capturas de las páginas.

## Cifras clave (dossier)
- Caso Bolt: 142.000 vehículos, 2.000 M USD de cargo, 14.085 USD por vehículo (dato público y cálculo derivado).
- Genealogía completa (capa sintética): 87,6 % de las unidades.
- Escenario base (supuestos académicos): coste evitado de 1.300 M USD y beneficio neto del cliente de 68,43 M USD al año.

La lista completa está en [`docs/CONTEXTO_COHERENCIA_DOSSIER_FRONTS.md`](docs/CONTEXTO_COHERENCIA_DOSSIER_FRONTS.md).

## Estado
Trabajo en curso. Pendientes: revisión final de dos páginas del informe de SAS, precio del software (hipótesis) y redacción de los últimos apartados del dossier.

## Uso
Material académico. No usar como fuente de datos internos de ninguna empresa.
