# 狂音流 - Mecánica de Daño por Suerte  

---

## 1. Conceptos Fundamentales

### 1.1 Definiciones Básicas
Se presentan tres variables principales para modelar el daño basado en Suerte:

- **幸运概率 (LuckRate)**  
  Probabilidad efectiva de activar un golpe de suerte.

- **幸运倍率 (LuckyMultiplier)**  
  Factor que describe la magnitud del daño cuando ocurre un golpe de suerte.

- **幸运增效 (LuckyAmplify)**  
  Aumento adicional aplicado al daño resultante del Lucky Hit.

La clase **狂音流** posee modificadores exclusivos que incrementan estos factores.

---

## 2. Fórmulas Fundamentales

### 2.1 Fórmula de 幸运倍率 (LuckyMultiplier)
La relación definida es:

```
LuckyMultiplier = 0.4 + 0.25 × LuckRate
```

狂音流 incluye un multiplicador adicional ×1.5:

```
LuckyMultiplier = 1.5 × (0.4 + 0.25 × LuckRate)
```

---

### 2.2 Fórmula de 幸运增效 (LuckyAmplify)

La presentación define:

```
LuckyAmplify = 1 + LuckRate
```

狂音流 agrega +0.15 y un ×1.5:

```
LuckyAmplify = 1.5 × (1 + 1.5 × LuckRate + 0.15)
```

---

### 2.3 Fórmula de 幸运期望倍率 (Expected Lucky Multiplier)

Se deriva de:

```
ExpectedLuckyMultiplier = LuckRate × LuckyMultiplier × LuckyAmplify
```

Sustituyendo los modificadores exclusivos de 狂音流:

```
ExpectedLuckyMultiplier =
1.5 × LuckRate × (0.4 + 1.25 × LuckRate) × (1.15 + 1.5 × LuckRate)
```

---

## 3. Fórmula General de Daño de 狂音流

La fórmula completa presentada es:

```
Damage = (ATK_base + ATK_refine + ATK_element)
       × (0.4 + 1.25 × LuckRate)
       × (1.15 + LuckRate + OtrosBonos)
       × ElementBonus
       × Versatility
       × CritBonus
```

Los factores se desglosan en las siguientes secciones.

---

## 4. Componentes del Daño

### 4.1 Ataque Total
Valores usados en el ejemplo:

- 面板攻击: 1411  
- 精炼攻击: 408  
- 元素攻击: 45  

Total:

```
ATK_total = 1411 + 408 + 45 = 1864
```

---

### 4.2 Conversión de 元素强度 a Porcentaje de Daño

La presentación establece:

```
ElementBonusFromStrength = x / (x + 4460)
```

Este valor se combina posteriormente con 元素加伤.

---

### 4.3 Otros Bonos de Daño (其他加伤)

El expositor proporciona:

- 模组精英伤: 0.66  
- 模组智力: 0.6  
- 全元素强度加成: 0.0044  

Total:

```
OtrosBonos = 0.66 + 0.6 + 0.0044 = 1.2644
```

---

### 4.4 Contribuciones de 加伤区

Valores incluidos:

- 元素加伤区: 天赋精英 8%、烈焰狂想 10%  
- 攻击区: 万众瞩目 8% + 80  

---

## 5. Cálculo Completo de Ejemplo

Sustitución directa realizada en la presentación:

```
Damage =
(1592 + 408 + 45)
× (0.4 + 1.25 × 0.6303)
× (1.15 + 0.6303 + 0.066 + 0.06)
× (1 + ElementBonus)
× (1 + 全能加伤)
× (1 + 暴击加伤)
```

Resultado mostrado:

```
= 5484.7104
```

---

## 6. Habilidades que Activan o No Activan Suerte

### Habilidades que **sí** activan 幸运:

- 普攻每段  
- 增幅节拍每段  
- 无限狂想每段  
- 聚合乐章每段  
- 烈焰狂想每段  
- 安可琴弦每段  

### Habilidades que **no** activan 幸运:

- 火柱冲击  
- 烈火冲击  

---

## 7. Observaciones Técnicas Importantes

1. El muñeco utilizado corresponde al tipo **精英属性**, no jefe.  
2. La conversión de **生命波动 10%** equivale a aproximadamente **15% de 幸运概率** para 狂音流.  
3. 幸运 no recibe beneficios por distancia.  
4. Las habilidades multigolpe generan un número extremadamente alto de activaciones por segundo.  

---

## 8. Conclusión General

La estructura de daño de 狂音流 se fundamenta completamente en la optimización del **LuckRate**, debido a que:

- Tanto 幸运倍率 como 幸运增效 escalan de manera **no lineal**, multiplicándose entre sí.  
- Los multiplicadores ×1.5 exclusivos de la clase producen un crecimiento exponencial.  
- Otros atributos (全能, 暴击, 距离) aportan mucho menos que cualquier incremento marginal de 幸运概率.  

El resultado es una build donde la prioridad absoluta es maximizar la probabilidad de Suerte y los factores que la amplifican.

