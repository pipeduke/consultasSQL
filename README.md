# consultasSQL
Prueba técnica SQL

# Escribir un query para consultar cada uno de los siguientes requerimientos:

_**1.1 Aportes diarios en metros cúbicos de los rios de la región de Antioquia**_
```
SELECT DATE_TRUNC('day',fechacarga) AS Dia,  SUM(aportesmm3) AS Aporte_M3
FROM public.aportesproduccion
WHERE regionhidrologica = 'ANTIOQUIA'
GROUP BY DATE_TRUNC('day',fechacarga)
ORDER BY 1 DESC;
```

_**1.2 Aportes totales del sistema durante el ultimo año**_
región de Antioquia**_
```
SELECT SUM(aportesenergia) AS AportesEnergia
FROM public.aportesproduccion
WHERE fechacarga >= (now() - '365 day'::INTERVAL);
```

_**2. Reservas del SIN en porcentaje durante el último año.**_

Estuve investigando que era SIN, parece ser Sistema Interconectado Nacional, pero no encontré alguna tabla con información al respecto

_**3. Máximo diario del precio de bolsa de los últimos tres meses.**_
```
SELECT DATE_TRUNC('day',fechaoperacion) AS Dia,  MAX(vctb) AS max_dia
FROM public.afac
WHERE fechaoperacion >= (now() - '90 day'::INTERVAL)
GROUP BY DATE_TRUNC('day',fechaoperacion);
```

_**4. Está repetido, debe ser "Minimo" diario del precio de bolsa de los últimos tres meses.**_
```
SELECT DATE_TRUNC('day',fechaoperacion) AS Dia,  MIN(vctb) AS min_dia
FROM public.afac
WHERE fechaoperacion >= (now() - '90 day'::INTERVAL)
GROUP BY DATE_TRUNC('day',fechaoperacion);
```

_**5. Promedio diario del precio de bolsa de los últimos tres meses.**_
```
SELECT DATE_TRUNC('day',fechaoperacion) AS Dia,  AVG(vctb) AS avg_dia
FROM public.afac
WHERE fechaoperacion >= (now() - '90 day'::INTERVAL)
GROUP BY DATE_TRUNC('day',fechaoperacion);
```

_**6. Demanda mensual del SIN durante los últimos tres años.**_

Estuve investigando que era SIN, parece ser Sistema Interconectado Nacional, pero no encontré alguna tabla con información al respecto

_**7. Precios de oferta promedio por tecnología de generación durante el último año.**_

-En esta consulta no encontré una tabla que se relacione con "public.capains", debe ser una consulta de dos tablas ya que esta no tiene columna de precio-

```
SELECT tecnologia, null oferta_promedio
FROM public.capains
WHERE fechaoperacion >= (now() - '365 day'::INTERVAL)
GROUP BY tecnologia;
```

_**8. Compras y ventas en bolsa por agente durante el último mes.**_
```
SELECT agente, SUM(vctb) AS comprasEnBolsa, SUM(vvtb) AS ventasEnBolsa
FROM public.afac
WHERE fechaoperacion >= (now() - '30 day'::INTERVAL) --Modificar a 60 días o más para que traiga información
GROUP BY agente;
```

_**9. Demanda de la última semana y de la misma semana del año anterior.**_

Pienso que la consulta está muy general, no encontré una tabla acorde para hacer este query.

*_______________________________*
* **✒️ Presentado por:** 

**Felipe Duque**

📧 [felipeduque9@gmail.com](mailto:felipeduque9@gmail.com)

📲 [310 3846185](tel://+573103846185)
