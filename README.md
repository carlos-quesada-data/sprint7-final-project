# sprint7-final-project
Proyecto Sprint 7: Análisis ConnectaTel 

## Objetivo del proyecto

Este proyecto realiza un análisis exploratorio de datos sobre el comportamiento de uso de clientes de **ConnectaTel**, una empresa de telecomunicaciones. El objetivo es limpiar, transformar y segmentar la base de usuarios según su perfil demográfico y patrones de uso (llamadas, mensajes y minutos), con el fin de generar **insights accionables** que apoyen decisiones comerciales sobre la oferta de planes y oportunidades de negocio.

## Datasets utilizados

| `plans.csv` | Información sobre los planes disponibles (Básico, Premium, etc.) |

| `users_latam.csv` | Datos demográficos de los usuarios: edad, ciudad, fecha de registro (`reg_date`), plan contratado |

| `usage.csv` | Registro histórico de uso por usuario: tipo de evento (`type`: llamada/mensaje), duración (`duration`), fecha |

Todos los archivos se encuentran en la carpeta `/datasets`.

## Etapas del análisis

1. **Revisión y estandarización de fechas**
   Conversión de columnas de fecha a tipo `datetime` (a prueba de errores), conteo de frecuencia por año y detección de fechas imposibles (años futuros posteriores a 2024 o negativos).

2. **Limpieza de datos**
   Tratamiento de valores faltantes o mal codificados (ej. `"?"` en la columna `city`), y conversión de tipos de datos incorrectos (ej. columnas numéricas almacenadas como texto).

3. **Evaluación de valores nulos (MAR/MCAR)**
   Análisis de si los nulos en `duration` y `length` dependen de otra variable observada (`type`), mediante tablas de contingencia y prueba de chi-cuadrado, para decidir si se dejan como nulos o se imputan.

4. **Construcción del perfil de usuario (`user_profile`)**
   Agregación de la tabla `usage` por `user_id` (total de mensajes, llamadas y minutos de llamada) y combinación con la tabla `users` mediante `merge`.

5. **Estadísticas descriptivas**
   Resumen estadístico (`describe()`) de las variables clave del comportamiento de uso.

6. **Visualización de distribuciones**
   Histogramas de `age`, `cant_mensajes`, `cant_llamadas` y `cant_minutos_llamada`, segmentados por tipo de plan, para observar diferencias y forma de la distribución.

7. **Identificación de outliers**
   Boxplots por variable y cálculo de límites mediante el **método IQR**, para detectar valores extremos y decidir su tratamiento.

8. **Segmentación de clientes**
   - Por nivel de uso (`grupo_uso`): Bajo uso, Uso medio, Alto uso
   - Por edad (`grupo_edad`): Joven (<30), Adulto (30-59), Adulto Mayor (60+)

9. **Insight ejecutivo**
   Traducción de los hallazgos técnicos en conclusiones de negocio: calidad de los datos, comportamiento por segmento, segmentos más valiosos, implicaciones de los outliers y recomendaciones sobre la oferta de planes.

## ▶️ Cómo ejecutar el notebook

Abre el archivo S7 Version-Estudiante-Project-ConnectaTel.ipynb.
Asegúrate que los datasets corran.
Descarga las librerías necesarias pandas, seaborn, matplotlib.
Reproduce las celdas en orden.

## 📂 Estructura del repositorio

```
├── S7 Version-Estudiante-Project-ConnectaTel.ipynb
├── README.md
```
