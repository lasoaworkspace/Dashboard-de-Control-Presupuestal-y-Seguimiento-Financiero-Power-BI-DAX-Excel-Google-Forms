# Dashboard de Control Presupuestal y Seguimiento Financiero | Power BI, DAX, Excel, Google Forms

Un repositorio para ver la guía de como se elaboro un archivo '.pbix' con fines educativos, sobre los datos estadísticos de un presupuesto para algún objetivo, que en el ejemplo fue para una moto 'Pulsar NS125'.
#  Análisis de Presupuesto (Power BI)

Este proyecto es un tablero interactivo diseñado para analizar desviaciones presupuestales y cumplimiento de objetivos financieros.

## 📷 Vista Previa del Tablero
<img width="2671" height="1495" alt="image" src="https://github.com/user-attachments/assets/04be0772-3ae4-4b08-8f53-7a9da1572203" />

## 🛠 Herramientas Utilizadas
- **Power BI Desktop:** Modelado de datos y visualización.
- **Excel:** Limpieza y estructuración de la fuente de datos (ETL).
- **DAX:** Creación de medidas calculadas para indicadores de cumplimiento.

## 📂 Cómo ver el proyecto completo
El archivo fuente `.pbix` está disponible en este repositorio. Puedes descargarlo para explorar las fórmulas y el modelo de datos.

## Previo a la elaboración
Debemos tener en cuenta que es lo que utilizaremos para crear esta tabla interactiva de presupuestos, necesitaremos un lugar por donde introducir los datos, un lugar donde almacenarlo, y un lugar donde mostrarlo, por ello utilizaremos Google Forms (Para la introducción de datos), el Excel predeterminado del Google Forms(Para el almacenamiento de nuestra base de datos) y Power Bi (Para mostrar las estadísticas de nuestro progreso), 

## Elaboramos un Google Forms
Elaboraremos 2 Formularios, uno para los ingresos y el segundo para los gastos.

Ganancias: 
<img width="1489" height="834" alt="image" src="https://github.com/user-attachments/assets/34d32387-9bd0-44c6-93b5-d88183e61fec" />

https://docs.google.com/forms/d/e/1FAIpQLSeE3a5VRLVgSeJLckOQor6E0jPTbLPx6BOWD2_KaCbxUd7Nvw/viewform?usp=dialog

Gastos:

<img width="530" height="1423" alt="image" src="https://github.com/user-attachments/assets/7c5d30ec-dcf0-4242-9d15-b15cfabb6fc6" />

https://docs.google.com/forms/d/e/1FAIpQLScseajcaVefzoQ6J9-1O-cJqCLGNcDLx1tQ9UKyzwW9cnJtZQ/viewform?usp=sharing&ouid=117298393876020992922

### 📝 Estructura de los Formularios 

Para asegurar que el análisis en Power BI sea detallado, diseñé los formularios con campos específicos que permiten segmentar la información. A continuación, detallo la configuración de preguntas y opciones:

#### 1. Formulario de Gastos
Este formulario registra cada salida de dinero. La estructura de preguntas y alternativas es la siguiente:

* **Fecha:** *Obligatorio*. (Para análisis temporal y líneas de tendencia).
* **Cuenta (Tipo de Gasto):**
    * *Gastos Fijos:* (Alquiler, luz, agua, internet).
    * *Gastos Variables:* (Comida, salidas, antojos).
    * *Educación/Salud:* (Inversión personal).
* **Medio de Pago:** (Crucial para conciliar con cuentas bancarias).
    * *Opciones:* Efectivo, Yape, Plin, Tarjeta de Débito, Tarjeta de Crédito.
* **Categoría:** (El nivel más granular para los gráficos de torta/pie charts).
    * *Opciones:* Transporte, Alimentación, Ocio, Servicios, Suscripciones, Mantenimiento, Ropa, Otros.
* **Importe:** *Número*. (El monto exacto de la transacción).
* **Descripción:** *Texto breve*. (Detalle opcional para recordar el gasto específico).

#### 2. Formulario de Ingresos (Ganancias)
Diseñado para ser rápido y registrar el flujo de caja positivo.

* **Fecha:** *Obligatorio*.
* **Fuente de Ingreso:** (Para diferenciar de dónde viene el dinero).
    * *Opciones:* Sueldo, Freelance/Cachuelos, Regalos, Inversiones.
* **Monto:** *Número*.

### 🔗 Integración: Conectando Google Sheets con Power BI

El corazón del proyecto es la automatización. Para evitar descargar archivos Excel manualmente cada vez que registro un gasto, establecí una conexión directa entre la nube (Google Sheets) y la herramienta de visualización (Power BI).

#### El Flujo de Datos (Pipeline):
1. **Origen:** Las respuestas de los formularios se guardan automáticamente en un Google Sheet en la nube.

<img width="2671" height="1848" alt="image" src="https://github.com/user-attachments/assets/33aabd93-3c23-4d0e-8db6-c0e96355c11b" />

2. **Conexión:**
   - En Power BI, utilicé la opción **"Obtener Datos" > "Web"** (o conector de Google Sheets).
   - Ingresé el enlace de la hoja de cálculo para crear un túnel de datos directo.
     
<img width="2819" height="1981" alt="image" src="https://github.com/user-attachments/assets/9957f9c9-eb0c-4c9c-acf2-cecf83e924c5" />

3. **Transformación (ETL básico):**
   Antes de visualizar, los datos pasan por **Power Query** para:
   - Definir correctamente los tipos de datos (Moneda, Fecha, Texto).
   - Limpiar columnas vacías o innecesarias.
   - Estandarizar los nombres de las categorías.

<img width="3552" height="432" alt="image" src="https://github.com/user-attachments/assets/acb7a13c-5e06-4738-b802-db39242a72d9" />

### 🎨 Diseño del Fondo (Wallpaper) y Layout

Para lograr una interfaz limpia y profesional, no utilicé los fondos predeterminados de Power BI. En su lugar, diseñé un "Wallpaper" personalizado que define visualmente las áreas para cada gráfico.

#### Paso 1: Definir la Estructura (Wireframing)
Antes de crear la imagen, es crucial decidir qué gráficos vas a mostrar, ya que el fondo debe tener los "espacios" o contenedores exactos para ellos.

* **Mi caso:** Yo necesitaba espacios para:
    * Categorías (Barra lateral izquierda).
    * Meta vs Actual (Indicador central).
    * Ingresos vs Gastos (Tarjetas grandes).
    * Histórico diario (Gráfico de área inferior).

> **💡 Tip de Personalización:**
> Si deseas replicar este proyecto pero con otros gráficos (ej. un mapa o una tabla grande), te recomiendo abrir **PowerPoint** o **Figma**, dibujar rectángulos grises simulando tus gráficos y usar eso como plantilla para saber dónde deben quedar los espacios vacíos en tu fondo final.

#### Paso 2: Generación del Fondo con IA
Utilicé Inteligencia Artificial para generar la estética "Tech/Futurista". Si quieres un resultado similar, puedes usar este **Prompt** en herramientas como Midjourney, Dall-E 3 o Adobe Firefly:

**Prompt Sugerido:**
> "Futuristic HUD dashboard interface background, dark blue and neon cyan color palette, modular layout with empty rectangular glass panels for data charts, high tech financial tracking concept, clean minimalist UI, cyber security aesthetic, 8k resolution --ar 16:9"
> Este prompt lo puede utilizar mediante la inteligencia artifical de Nano Banana por recomendación propia recomiendo adecuar el prompt acorde tus necesidades, lo que te doy yo es la referencia de mi proyecto.

#### Paso 3: Montaje en Power BI
Una vez tienes tu imagen (editada con los espacios que necesitas):
1. Ve a la pestaña **Visualizaciones** > **Formato de página de informe**.
2. En **Fondo de lienzo (Canvas Background)**, selecciona tu imagen.
3. **Importante:** Ajusta la **Transparencia al 0%** y el Ajuste de imagen a **"Ajustar" (Fit)**.

### 🧠 Modelado de Datos y Lógica (DAX)

Una vez cargados los datos, es necesario estructurarlos para que los gráficos funcionen correctamente. Este paso se divide en dos: **Relaciones** y **Medidas**.

#### 1. Relaciones entre Tablas (Star Schema)
Como tengo dos tablas de hechos separadas (`Gastos` e `Ingresos`), necesitaba una forma de ver ambas en una misma línea de tiempo. Para ello:

* **Tabla Calendario (Master Date):** Creé una tabla auxiliar de fechas única.
* **La Relación:** Conecté:
    * `Gastos[Fecha]` ➡️ `Calendario[Date]` (Relación de uno a muchos).
    * `Ingresos[Fecha]` ➡️ `Calendario[Date]` (Relación de uno a muchos).

> **¿Por qué hacer esto?** Sin esta relación, no podría filtrar el mes de "Noviembre" y ver tanto mis ingresos como mis gastos en la misma pantalla. La tabla Calendario actúa como el puente temporal entre ambas.

#### 2. Creación de Medidas (DAX)
Para los indicadores numéricos (KPIs) como el "Saldo Actual" o el "Progreso de la Meta", no usé las columnas directas, sino que creé **Medidas Calculadas** para asegurar que los números sean dinámicos:

* **Total Ingresos**
Calcula la suma total de todas las entradas de dinero registradas.

Total Ingresos = SUM('Ingresos'[Monto])
  
Total Gastos Suma acumulada de todas las salidas de dinero:

Total Gastos = SUM('Gastos'[Importe])

Saldo Actual (Dinero disponible para la Moto): Esta es la medida clave para el gráfico de medidor.

Saldo Actual = [Total Ingresos] - [Total Gastos]

Porcentaje de Meta: Utilizado para visualizar cuánto falta para llegar al precio de la Pulsar NS125. 
Usé la función DIVIDE para evitar errores si el denominador fuera cero.

% Meta = DIVIDE([Saldo Actual], 7000, 0)

<img width="488" height="1276" alt="image" src="https://github.com/user-attachments/assets/f6ac3ae6-ce13-47f9-a36c-d57e1d64c3d1" />

### 🖥️ Montaje Final y Validación

Con el fondo (Wallpaper) ya configurado y las medidas DAX listas, procedí a colocar los objetos visuales exactamente sobre los espacios diseñados.

#### 1. Distribución de Visualizaciones (Layout)
Para que los datos cuenten una historia coherente, organicé los gráficos de la siguiente manera:

* **Tarjetas (KPIs):** Ubicadas en la zona central para lectura rápida ("Saldo Actual", "Ingresos Totales").
* **Gráfico de Medidor (Gauge):** Configurado con un valor máximo de 7,000 (Precio de la moto) para visualizar visualmente cuánto falta para la meta.
* **Gráfico de Barras:** A la izquierda, desglosando los gastos por "Categoría" para identificar fugas de dinero.
* **Gráfico de Área:** En la parte inferior, mostrando el flujo de ingresos diario para detectar patrones temporales.

> **🎨 Detalle de Diseño:** Ajusté los títulos y quité los fondos de cada gráfico (Background = Off) para que parezcan integrados nativamente en la interfaz futurista.

#### 2. La Prueba de Fuego (Testing)
Para validar que la automatización funciona correctamente, realicé el siguiente flujo de prueba:

1. **Entrada:** Abrí el enlace del Google Form desde mi celular y registré un gasto de prueba (Ej: "Compra de prueba - 50 soles").
2. **Verificación en Nube:** Confirmé que el Google Sheet recibió la nueva fila instantáneamente.
3. **Actualización:** En Power BI Desktop, hice clic en el botón **"Actualizar" (Refresh)**.
4. **Resultado:** Los indicadores del tablero cambiaron automáticamente, restando los 50 soles del "Saldo Actual" y ajustando la barra de progreso de la meta.

---
### 🏁 Conclusión
Este proyecto demuestra cómo integrar herramientas gratuitas y accesibles (Google Forms + Sheets) con potencia de análisis empresarial (Power BI) para resolver un problema personal real: la gestión financiera para alcanzar un objetivo de ahorro.
