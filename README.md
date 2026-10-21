# Financiamiento y factoring empresarial

Tablero interactivo con tres pestañas: indicadores de inclusión financiera empresarial (2021-2026), operaciones de factoring (enero 2019-agosto 2026) y un análisis con once indicadores complementarios, por tamaño empresarial, sector y departamento.

## Pestaña 1: Indicadores financieros

| Elemento | Contenido |
|---|---|
| Indicadores principales | Porcentaje de empresas con acceso al financiamiento (inclusión financiera), empresas con financiamiento, saldo, saldo promedio por empresa y empresas con financiamiento no registradas en SUNAT |
| Mapa departamental | Inclusión financiera, variación anual (pp) o saldo promedio; clic en un departamento filtra todo el tablero |
| Burbujas | Inclusión financiera (eje X) frente a saldo promedio (eje Y, logarítmico); tamaño = empresas con financiamiento |
| Líneas por tamaño | Evolución de la inclusión financiera de micro, pequeña, mediana y gran empresa |
| Matriz sector × tamaño | Inclusión financiera en cada cruce; clic en una celda filtra por ese sector y tamaño |
| Mapa de árbol | Saldo por subsector (área); un color por sector y tonos por subsector; entre paréntesis, porcentaje de empresas con acceso |
| Tabla | Detalle por departamento, ordenable y con búsqueda |

## Pestaña 2: Factoring

| Elemento | Contenido |
|---|---|
| Indicadores principales | Monto negociado, facturas, monto por factura, participación MIPYME y participación en el total nacional |
| Calendario | Mapa de calor año × mes (monto, facturas o monto por factura) |
| Serie mensual | Barras mensuales con promedio móvil de 12 meses |
| Composición | Participación de cada tamaño empresarial en el monto, por año |
| Mapa departamental | Monto, variación, monto por factura o participación MIPYME |
| Concentración | Curva de Pareto: cuántos departamentos explican el 80% del monto |
| Mapa de árbol | Monto por subsector; un color por sector y tonos por subsector; entre paréntesis, participación en el monto |
| Tabla | Detalle por departamento, ordenable y con búsqueda |

## Pestaña 3: Análisis

Filtros: año de análisis, año base, tamaño y departamento (clic en mapas, barras o cuadros).

| # | Elemento | Indicador |
|---|---|---|
| 1 | Margen extensivo e intensivo | ΔSaldo = (E₁ − E₀) × P₀ + E₁ × (P₁ − P₀): efecto del número de empresas y del saldo por empresa |
| 2 | Brecha | Empresas sin financiamiento = total de empresas − empresas con financiamiento (mapa y sectores) |
| 3 | Descomposición de la inclusión | ΔI = dentro de sector × tamaño + composición + interacción |
| 4 | Factoring respecto del crédito | Factoring de 12 meses / saldo de crédito × 100, por tamaño y departamento |
| 5 | Clústeres espaciales | I de Moran global y LISA de la inclusión (contigüidad reina, 999 permutaciones) |
| 6 | Convergencia | β (pendiente del cambio sobre el nivel inicial) y σ (dispersión entre departamentos) |
| 7 | Índice de acceso financiero | Promedio de cuatro dimensiones normalizadas 0-1 (método Sarma / IDH) |
| 8 | Concentración | HHI del crédito y del factoring, por departamento y por sector |
| 9 | Estacionalidad y proyección | Índice estacional mensual y proyección del año en curso con rango |
| 10 | Fichas | Mapa de cuadros con la evolución de la inclusión y ficha por departamento |
| 11 | Factoring como % del PBI | Factoring anual / valor agregado a precios corrientes del INEI, por departamento y actividad (2019-2025) |

## Definiciones

- **Inclusión financiera** = empresas con financiamiento / total de empresas × 100 (el total suma el padrón SUNAT y las empresas con financiamiento no registradas en SUNAT), para el mismo año, tamaño, sector y departamento. Es la definición del tablero de PRODUCE.
- **Saldo promedio** = saldo / empresas con financiamiento.
- **MIPYME** = micro + pequeña + mediana empresa; **MYPE** = micro + pequeña; **PYME** = pequeña + mediana. El filtro de tamaño ofrece además cada tamaño por separado.
- Se presenta 2021-2026; 2026 corresponde a saldos a julio. El padrón de 2025 repite el de 2024.
- **Factoring**: 2026 cubre enero-agosto; sus variaciones se comparan con enero-agosto de 2025.
- Colores de variación: azul = aumento, rojo = disminución.
- Lima comprende Lima Metropolitana y Lima Provincias: las bases no distinguen provincias.

## Validación

Las cifras coinciden con el [tablero de PRODUCEmpresarial](https://www.producempresarial.pe/financiamiento-tablero-indicadores/): saldo e inclusión financiera por año y tamaño (por ejemplo, 2026: S/ 224,154 millones y 27.3%), saldo por sector y subsector, y monto y facturas de factoring por año, sector, subsector y departamento.

## Contenido

| Ruta | Descripción |
|---|---|
| `index.html` | Tablero (carga d3 desde CDN y los datos desde `data/datos.js`). |
| `data/datos.js` | Datos agregados (financiamiento, factoring y límites departamentales). |
| `data/limites.json` | Contornos simplificados de los 25 departamentos (INEI). |
| `data/pbi.json` | VAB a precios corrientes por departamento y actividad, 2019-2025 (INEI, PBI departamental 2007-2025). |
| `scripts/pbi_extract.py` | Extrae `data/pbi.json` de `pbi_departamentos_2007_2025.xlsm`. |
| `data/vecinos.csv` | Pares de departamentos contiguos (contigüidad tipo reina) para el análisis espacial. |
| `scripts/agregar_datos.py` | Agrega los Excel fuente y regenera `data/datos.js`. |

## Actualizar los datos

```
pip install pandas openpyxl python-calamine
python scripts/agregar_datos.py "F:/2026/Pedro_2026/Tablero_indicadores_financieros"
```

El script lee `Indicadores_financiamiento.xlsx` (todas sus hojas), `indicadores_factoring.xlsx` y, si está en la misma carpeta, `pbi_departamentos_2007_2025.xlsm` del INEI; luego reescribe `data/datos.js`. El tablero no recalcula los datos fuente: solo suma y divide los agregados.

## Publicar en GitHub Pages

1. Suba todos los archivos manteniendo las carpetas.
2. En **Settings → Pages**, elija la rama `main` y la carpeta `/ (root)`.

Fuente: PRODUCE; PBI, INEI. Elaboración: **Good Guys Insight**.
