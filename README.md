# Pronóstico a 24 horas de la demanda eléctrica del SEIN (COES)

Proyecto final del curso **MIA-203 Redes Neuronales y Aprendizaje Profundo** · UNI FIIS · Equipo 6
Autores: Berthing Jhalin Gutierrez Brenis -  Glenn Luque Canaza

Pronóstico, a las 00:00 de Lima, de las 24 horas siguientes de la demanda eléctrica del Sistema Eléctrico Interconectado Nacional (SEIN), con datos públicos del COES (2008–2026). Se comparan Ridge, LightGBM y redes GRU, CNN y Transformer que corrigen el pronóstico del Ridge, con calendario peruano y una mezcla de modelos calibrada.

## Resultado principal
Prueba retrospectiva 2023–2026 (1 404 días), error absoluto medio (MAE) a 24 h:

| Modelo | MAE (MW) |
|---|---|
| Programación diaria del COES (referencia) | 104,1 |
| Ridge | 99,9 |
| Transformer sobre Ridge (3 semillas) | 90,0 ± 1,8 |
| **Mezcla calibrada (0,6 Transformer + 0,4 LightGBM)** | **81,3** |

## Contenido de este repositorio
| Carpeta | Qué hay |
|---|---|
| `informe/` | Artículo en formato IEEE (`Equipo6_Paper.pdf`, fuente `paper.tex` y `figs/`) y lista de referencias |
| `notebooks/` | Cuadernos de Google Colab ejecutados, con sus resultados a la vista |

### Cuadernos
- `Pronostico_Demanda_COES_B2_Colab.ipynb`: experimento principal (Ridge, LightGBM, ablación factorial, CNN y Transformer, mezcla calibrada).
- `Demo_Inferencia_COES_Colab.ipynb`: demostración de inferencia; pronostica las 24 horas de un día y lo compara con lo real y con el COES.
- `Pronostico_Demanda_COES_Colab.ipynb` y `Extender_Bloque1_60epocas_Colab.ipynb`: primera etapa (comparación de familias de redes, con entrenamiento extendido a 60 épocas).

Abrir un cuaderno en Colab: *Archivo → Abrir cuaderno → pestaña GitHub* y pegar la URL de este repositorio.

## Nota sobre la ejecución y los datos
- Los cuadernos usan el código fuente, los pesos entrenados y los datos que el equipo guarda en su Google Drive; en este repositorio se publican como evidencia de los experimentos y sus resultados.
- Los datos del COES **no se redistribuyen**: sus términos y condiciones (apartado V) permiten descargar «únicamente para fines informativos o personales» y exigen autorización escrita para distribuir su contenido. La fuente es el portal «Demanda» del COES: https://www.coes.org.pe/Portal/portalinformacion/demanda
