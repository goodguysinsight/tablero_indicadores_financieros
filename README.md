# Financiamiento y factoring empresarial

Tablero interactivo con dos pestañas: indicadores de inclusión financiera empresarial (2021-2026) y operaciones de factoring (enero 2019-agosto 2026), por tamaño empresarial, sector y departamento.

## Pestaña 1: Indicadores financieros

| Elemento | Contenido |
|---|---|
| Indicadores principales | Inclusión financiera, empresas con financiamiento, saldo, saldo promedio por empresa y empresas con financiamiento no registradas en SUNAT |
| Mapa departamental | Inclusión financiera, variación anual (pp) o saldo promedio; clic en un departamento filtra todo el tablero |
| Burbujas | Inclusión financiera (eje X) frente a saldo promedio (eje Y, logarítmico); tamaño = empresas con financiamiento |
| Líneas por tamaño | Evolución de la inclusión financiera de micro, pequeña, mediana y gran empresa |
| Matriz sector × tamaño | Inclusión financiera en cada cruce; clic en una celda filtra por ese sector y tamaño |
| Mapa de árbol | Saldo por subsector (área) coloreado por inclusión financiera |
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
| Mapa de árbol | Monto por subsector, coloreado por sector |
| Tabla | Detalle por departamento, ordenable y con búsqueda |

## Definiciones

- **Inclusión financiera** = empresas con financiamiento / total de empresas × 100 (el total suma el padrón SUNAT y las empresas con financiamiento no registradas en SUNAT), para el mismo año, tamaño, sector y departamento. Es la definición del tablero de PRODUCE.
- **Saldo promedio** = saldo / empresas con financiamiento.
- **MIPYME** = micro + pequeña + mediana empresa; **MYPE** = micro + pequeña; **PYME** = pequeña + mediana. El filtro de tamaño ofrece además cada tamaño por separado.
- Se presenta 2021-2026; 2026 corresponde a saldos a julio. El padrón de 2025 repite el de 2024.
- **Factoring**: 2026 cubre enero-agosto; sus variaciones se comparan con enero-agosto de 2025.
- Colores de variación: azul = aumento, rojo = disminución.

## Validación

Las cifras coinciden con el [tablero de PRODUCEmpresarial](https://www.producempresarial.pe/financiamiento-tablero-indicadores/): saldo e inclusión financiera por año y tamaño (por ejemplo, 2026: S/ 224,154 millones y 27.3%), saldo por sector y subsector, y monto y facturas de factoring por año, sector, subsector y departamento.

## Contenido

| Ruta | Descripción |
|---|---|
| `index.html` | Tablero (carga d3 desde CDN y los datos desde `data/datos.js`). |
| `data/datos.js` | Datos agregados (financiamiento, factoring y límites departamentales). |
| `data/limites.json` | Contornos simplificados de los 25 departamentos (INEI). |
| `scripts/agregar_datos.py` | Agrega los Excel fuente y regenera `data/datos.js`. |

## Actualizar los datos

```
pip install pandas openpyxl python-calamine
python scripts/agregar_datos.py "F:/2026/Pedro_2026/Tablero_indicadores_financieros"
```

El script lee `Indicadores_financiamiento.xlsx` (todas sus hojas) e `indicadores_factoring.xlsx` y reescribe `data/datos.js`. El tablero no recalcula los datos fuente: solo suma y divide los agregados.

## Publicar en GitHub Pages

1. Suba todos los archivos manteniendo las carpetas.
2. En **Settings → Pages**, elija la rama `main` y la carpeta `/ (root)`.

Fuentes: financiamiento, SUNAT, SBS y PRODUCE; factoring, SUNAT, CAVALI, SBS, SMV y PRODUCE. Elaboración: Good Guys Insight.
