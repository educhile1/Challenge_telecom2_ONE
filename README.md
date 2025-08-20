
## Modelo Base:

Este proceso cuenta con la generación de un modelo base o "base line" para tener de referencia para los futuros modelos.

- **Definiendo una baseline:** Creación del modelo base.
  - 'RMSE': 0.4391
  - 'MAE': 0.3887
  - 'R2': -0.0002

## Modelo 1: Árboles de Decisión

El proceso se divide en varios análisis y tratamiento de datos ,

- **Creando el Modelo:** Creación del modelo a desarrollar basado en un Data Frame llama "datos_org_limpios", el cual había sido tratado previamente. Lo resultados obtenidos en este punto son:
  
  -  La exactitud del modelo con el conjunto de entrenamiento es: **0.8832702160837603**
  -  La exactitud del modelo con el conjunto de validación es: **0.758183032732131**
    
- **Evaluando el Modelo:** La matriz de confusión obtenida es:

  <img width="777" height="535" alt="image" src="https://github.com/user-attachments/assets/b368448b-8216-4610-82ab-e54002d2b525" />

- **Exactitud, precisión y recall (sensibilidad):** El análisis obtenido sugiere que el modelo tiene dificultades para identificar correctamente los resultados positivos. Sin embargo, la exactitud es más alta (75.8%), esto indica que, en general, el modelo clasifica correctamente una buena proporción de las instancias, aunque el balance entre precisión y recall es deficiente, como lo refleja el F1-score de 53.4%:
  
  - La precisión del modelo es: **0.5461741424802111**
  - La sensibilidad (recall) del modelo es: **0.5214105793450882**
  - La exactitud (accuracy) del modelo es: **0.758183032732131**
  - La F1-score del modelo es: **0.5335051546391752**
    
- **Curva ROC:** Este análisis indica que el modelo tiene un AUC de 0.68 lo cual significa que tiene un rendimiento moderado en la clasificación binaria, sugiriendo una capacidad razonable para discriminar entre las clases. Sin embargo, se considera que hay margen para mejorar, ya que un AUC por debajo de 0.70 se considera débil.

  <img width="657" height="550" alt="image" src="https://github.com/user-attachments/assets/abe73079-d6a0-42de-95cb-e1d10198de18" />

- **Curva de precisión x sensibilidad:** Este análisis nos entrega un AP de 0.41, esto indica un rendimiento moderado del modelo en la identificación de instancias positivas, sugiriendo que hay margen para mejorar su capacidad de clasificación. Un valor más alto es deseable para un mejor equilibrio entre precisión y sensibilidad.

  <img width="621" height="547" alt="image" src="https://github.com/user-attachments/assets/a30863b2-1715-4b5f-bc87-13fc73603266" />

- **Informe de métricas:** Las métricas obtenidas en este punto fueron:

  <img width="543" height="177" alt="image" src="https://github.com/user-attachments/assets/e263ab59-6d3b-4927-ab00-65514b5452ab" />

- **Validación cruzada:** Se realizaron 2 validaciones basadas en Kfold, una sin sensibilidad y una con sensibilidad:
  - Kfold:
    - El promedio de exactitud es de: 0.7534211153928225
    - El desvio típico es de: 0.011673206081966817
    - El Intervalo de confianza es: [(np.float64(0.7300747032288889), np.float64(0.7767675275567562))]
  - Validación cruzada con sensibilidad nos otorgó los siguientes valores. En caso de desear ver valores más concretos pueden ingresar al archivo y revisarlos en la sección correspondiente:
    - recall
    - precision
    - f1
- **Estratificando los datos:** Este análisis nos entregó los siguientes resultados:
  - El Intervalo de confianza es: [(np.float64(0.43343153622613145), np.float64(0.5496289958850524))]
- **Balanceo de los datos**: Esté tratamiento de datos contó con los siguientes análisis:
  - Oversampling: Los resutados obtenidos fueron:
    - El Intervalo de confianza es: [(np.float64(0.7992951961574655), np.float64(0.8668228098410864))]
  - Pipeline para validación: Los resutados obtenidos fueron:
    - El Intervalo de confianza es: [(np.float64(0.5924626525437608), np.float64(0.7492868464939948))]
  - Undersampling: Los resutados obtenidos fueron:
    - El Intervalo de confianza es: [(np.float64(0.4989950848330098), np.float64(0.6691020522421645))]
  - SMOTEENN: Los resutados obtenidos fueron:
    - El Intervalo de confianza es: [(np.float64(0.7071487055294401), np.float64(0.7856037100013815))]
    - 
- **Probando el modelo:** Al probar el modelo con un balanceo de tipo SMOTEENN se obtuvieron los siguientes resultados:

  <img width="706" height="708" alt="image" src="https://github.com/user-attachments/assets/67a5be70-9006-44c7-833c-61b380209663" />

- **Features Importances - Arboles De Decisión:** En este punto se procedió a mejorar el modelo evaluando la importancia de cada columna al momento de generar el modelo. Luego del tratamiento de los datos se obtuvo una reducción de 42 columnas a solo 10 columnas para este modelo, estas fueron:
  -  onehotencoder__Contract_Month-to-month
  -  tenure
  -  Charges.Monthly
  -  onehotencoder__OnlineSecurity_No
  -  PaperlessBilling
  -  onehotencoder__InternetService_Fiber optic
  -  onehotencoder__PaymentMethod_Electronic check
  -  onehotencoder__StreamingMovies_No
  -  Dependents
  -  gender
    
-  **Optimización de Hiperparámetros - Arboles de Decisión:** Finalmente se procedió con una Optimización de Hiperparámetros, obteniendo los siguientes resultados finales para el modelo de Árbol de Decisión:

  <img width="877" height="725" alt="image" src="https://github.com/user-attachments/assets/e5ae2cfd-f2ac-4b48-a5a5-043c9735019d" />

## Modelo 2: Bosques Aleatorios

El proceso se divide en varios análisis y tratamiento de datos los cuales se encuentran detallados y en profundidad dentro del archivo [TelecomX_Parte2_Bosques_Aleatorios.ipynb](https://github.com/Antonio-B85/challenge-Parte-2--TelecomX/blob/main/TelecomX_Parte2_Bosques_Aleatorios.ipynb). Los análisis y tratamientos realizados fueron:

- **Creando el Modelo**
- **Evaluando el Modelo:** La matriz de confusión obtenida es:

  <img width="797" height="543" alt="image" src="https://github.com/user-attachments/assets/af7c6ae3-41b7-45bf-abb1-6cc9b628d110" />

- **Exactitud, precisión y recall (sensibilidad):** El análisis obtenido sugiere que el modelo tiene dificultades para identificar correctamente los resultados positivos. Sin embargo, la exactitud es más alta (75.8%), esto indica que, en general, el modelo clasifica correctamente una buena proporción de las instancias, aunque el balance entre precisión y recall es deficiente, como lo refleja el F1-score de 53.4%:

  - La precisión del modelo es: **0.8170347003154574**
  - La sensibilidad (recall) del modelo es: **0.6523929471032746**
  - La exactitud (accuracy) del modelo es: **0.8690714762859052**
  - La F1-score del modelo es: **0.7254901960784313**
    
- **Curva ROC:** Esta curva nos indica que el modelo tiene una buena capacidad para discriminar entre las clases positivas y negativas, lo que sugiere que es clínicamente útil. Este valor implica que, en promedio, el modelo clasifica correctamente el 80% de los casos en comparación con los controles.

  <img width="646" height="553" alt="image" src="https://github.com/user-attachments/assets/9cf46781-853b-44d6-81ef-a065f2977e3b" />

- **Curva de precisión x sensibilidad:** Esto nos indica un rendimiento moderado del modelo en equilibrar precisión y sensibilidad, sugiriendo que identifica razonablemente bien las instancias relevantes. Sin embargo, hay margen para mejorar en la reducción de falsos positivos y en la recuperación de más instancias positivas.

  <img width="647" height="546" alt="image" src="https://github.com/user-attachments/assets/bb196b78-671b-4452-a0bb-74ef5dcd9596" />

- **Informe de métricas:** Las métricas obtenidas en este punto fueron:

  <img width="540" height="176" alt="image" src="https://github.com/user-attachments/assets/5410f40c-fe32-420e-bab1-5da8f8cf2159" />
  

- **Balanceo de datos, Análisis de Hiperparámetros y Features Importances**: Estos análisis fueron realizados primero por separados y luego en conjunto. En este documento detallaremos solo los análisis realizados de manera conjunta con los valores obtenidos y las matrices de confusión respectivas:

  - **Oversampling**
    - Features Importances: Este análisis redujo las columnas importantes a solo 10, estas son:
      
      - onehotencoder__Contract_Month-to-month
      - tenure
      - Charges.Monthly
      - onehotencoder__OnlineSecurity_No
      - onehotencoder__TechSupport_No
      - onehotencoder__Contract_Two year
      - onehotencoder__PaymentMethod_Electronic check
      - onehotencoder__InternetService_Fiber optic
      - onehotencoder__Contract_One year
      - PaperlessBilling
     
    - Optimización de Hiperparámetros:

      <img width="870" height="720" alt="image" src="https://github.com/user-attachments/assets/44780a51-143d-4373-9c2a-d6b4c15ecb11" />

  - **Undersampling**
    - Features Importances: Este análisis redujo las columnas importantes a solo 7, estas son:
      
      - onehotencoder__Contract_Month-to-month
      - tenure
      - Charges.Monthly
      - onehotencoder__OnlineSecurity_No
      - onehotencoder__TechSupport_No
      - onehotencoder__Contract_Two year
      - onehotencoder__PaymentMethod_Electronic
     
    - Optimización de Hiperparámetros:

      <img width="853" height="712" alt="image" src="https://github.com/user-attachments/assets/cfc489ff-dba7-49d7-88bc-80d4d9faf7b5" />

  - **SMOTEENN**
    - Features Importances: Este análisis redujo las columnas importantes a solo 30, estas son:
      
      - onehotencoder__Contract_Month-to-month
      - tenure
      - Charges.Monthly
      - onehotencoder__OnlineSecurity_No
      - onehotencoder__TechSupport_No
      - onehotencoder__Contract_Two year
      - onehotencoder__PaymentMethod_Electronic check
      - onehotencoder__InternetService_Fiber optic
      - onehotencoder__Contract_One year
      - PaperlessBilling
      - Partner
      - Dependents
      - onehotencoder__DeviceProtection_No
      - gender
      - onehotencoder__OnlineSecurity_Yes
      - onehotencoder__OnlineBackup_No
      - SeniorCitizen
      - onehotencoder__MultipleLines_No
      - onehotencoder__TechSupport_Yes
      - onehotencoder__InternetService_DSL
      - onehotencoder__PaymentMethod_Credit card (automatic)
      - onehotencoder__StreamingMovies_Yes
      - onehotencoder__StreamingTV_Yes
      - onehotencoder__OnlineBackup_Yes
      - onehotencoder__PaymentMethod_Bank transfer (automatic)
      - onehotencoder__DeviceProtection_Yes
      - onehotencoder__StreamingMovies_No
      - onehotencoder__StreamingTV_No
      - onehotencoder__PaymentMethod_Mailed check
      - onehotencoder__InternetService_No  
     
    - Optimización de Hiperparámetros:

      <img width="827" height="712" alt="image" src="https://github.com/user-attachments/assets/14e74b9d-7e5d-4fa7-9b55-e20cb21170a1" />

## Selección de Modelo

En base a los estudios detallados anteriormente se ha establecido que el modelo "Campeón" es el **"Modelo 2: Bosques Aleatorios + Oversampling e Hiperparámetros"**. Los motivos son:

1. Tiene el menor **RMSE** y **MAE**, lo que indica un mejor ajuste del modelo.
   
2. Presenta un **R²** positivo, lo que sugiere que el modelo explica una parte de la variabilidad de los datos.
   
3. El **f1-score** para la clase positiva (1.0) es el más alto entre todos los modelos, lo que indica una mejor capacidad para identificar correctamente las instancias positivas.

<img width="870" height="720" alt="image" src="https://github.com/user-attachments/assets/44780a51-143d-4373-9c2a-d6b4c15ecb11" />

## Principales Factores de Cancelación

- onehotencoder__Contract_Month-to-month
- tenure
- Charges.Monthly
- onehotencoder__OnlineSecurity_No
- onehotencoder__TechSupport_No
- onehotencoder__Contract_Two year
- onehotencoder__PaymentMethod_Electronic check
- onehotencoder__InternetService_Fiber optic
- onehotencoder__Contract_One year
- PaperlessBilling

## Sugerencias

En base a los resultados obtenidos, se indican las siguientes sugerencias para poder mejorar la fidelidad de los clientes con la empresa:

1. **Convertir contratos mes-a-mes a plazos largo**

    - Oferta "Recompensa por Compromiso": Descuento del 15-20% al cambiar a contratos anuales/bianuales.
    - Beneficio escalonado: Mayor descuento en el segundo año de permanencia (ej: 10% año 1 → 20% año 2).
    - Penalización mes-a-mes: Incremento moderado (5-8%) en tarifas para este plan.
    
3. **Reducción de fricción en pagos electrónicos**

    - Incentivo por autogestión: 3-5% de descuento por usar tarjeta/autorización automática vs. cheque electrónico.
    - Alertas proactivas: Notificaciones SMS/email 72h antes del cargo para evitar rechazos.
    - Programa "Pagos Perfectos": Bonificación por 12 pagos puntuales consecutivos (ej: mes gratis).
      
5. **Paquetes de valor agregado para Fiber Optic**

    - Bundle "Tranquilidad Fiber": Incluir seguridad + soporte técnico gratis 6 meses al contratar fibra.
    - Garantía de velocidad: Reembolso proactivo si la velocidad cae bajo umbral pactado.
    - Upgrade gratis: Migrar gradualmente clientes de cobre a fibra con prueba gratuita.
      
7. **Programa de lealtad por antigüedad**

    - Beneficios por hitos: Al cumplir X meses, ofrecer:
      - 6 meses: Servicio premium temporal (ej: cloud storage).
      - 12 meses: Reducción permanente del 5% en factura.
    - "Tarifa Congelada": Bloquear aumento de precio por 24 meses para clientes >1 año de antigüedad.
      
9. **Transformar papelera en ventaja digital**

    - Ecosistema digital: App exclusiva con:
      - Alertas personalizadas de uso.
      - Autodiagnóstico de fallas.
      - Sistema de recompensas (puntos por reportar averías, referidos, etc.).
    - Beneficio ecológico: Donación a causa ambiental por cada año sin factura física.
      
11. **Segmentación crítica para alto riesgo**

    - Equipo "Guardianes": Unidad especializada para contacto proactivo bimestral con:
      - Análisis gratuito de necesidades.
      - Ofertas personalizadas en tiempo real.
      - Acceso directo a soporte premium (max 5 min de espera).

## Requisitos

- Python 3.x  
- pandas  
- matplotlib (para visualización de datos)


