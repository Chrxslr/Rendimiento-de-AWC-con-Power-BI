# 📊 Proyecto Integrador – Visualizando el Rendimiento de AWC con Power BI  

**Autor:** Christian Daniel Lara Larios  
**Email:** larad8704@gmail.com  
**Cohorte:** DAFT-16  
**Fecha de entrega:** 17/07/2025  
**Institución:** Adventure Works BI  

---

## 📌 Introducción  
Este proyecto integrador tuvo como objetivo analizar el **rendimiento financiero de Adventure Works**, una empresa ficticia de retail.  

A partir de una base de datos estructurada, se diseñó un **dashboard interactivo en Power BI** con enfoque visual y funcional que permite:  
- Explorar **indicadores clave**.  
- Identificar **patrones de comportamiento**.  
- Facilitar la **toma de decisiones estratégicas**, especialmente en el mercado estadounidense.  

---

## 🛠️ Desarrollo del proyecto  

### 🔹 Carga y transformación de datos  
- Tablas principales: `FactInternetSales`, `DimDate`, `DimCustomer`, `DimProduct`, `DimSalesTerritory`.  
- Transformaciones en **Power Query**:  
  - Formateo y cambio de tipos de datos.  
  - Eliminación de columnas irrelevantes.  
  - Creación de columnas auxiliares para segmentación geográfica.  
  - Filtrado de fechas y regiones válidas.  

### 🔹 Modelado de datos  
- Relaciones entre tablas basadas en **foreign keys**.  
- Revisión de direcciones de filtro cruzado para asegurar coherencia en los análisis.  

### 🔹 Medidas DAX creadas  
**Tabla Financieras**:  
```DAX
TotalIngresos = SUM(FactInternetSales[SalesAmount])  
TotalCOGS = SUM(FactInternetSales[TotalProductCost])  
Margen_Profit = DIVIDE([TotalIngresos] - [TotalCOGS], [TotalIngresos], 0)  
Ingresos_YTD = TOTALYTD([TotalIngresos], DimDate[FullDateAlternateKey])  
