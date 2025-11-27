## 1. Introducción
Este documento resume todas las fórmulas utilizadas para calcular el rendimiento del **Ice Mage (冰魔导师)**.

Incluye:
- Conversión de estadísticas base → porcentajes
- Conversión de penetración / defensa
- Fórmulas completas de daño
- Ejemplos numéricos

## 2. Conversión de Stats (Base → %)

### 2.1 Crit Rate (暴击率)
Chino:
```
暴击率 = 暴击 / 1512
```
Español:
```
CritRate = Crit / 1512
```

### 2.2 Crit Damage (暴击伤害)
Chino:
```
暴击伤害 = 爆伤 / 1512
```
Español:
```
CritDMG = CritDamage / 1512
```

### 2.3 Haste → Attack Speed (急速 → 攻速%)
Chino:
```
攻速增益 = 急速 / 756
```
Español:
```
AttackSpeedBonus = Haste / 756
```

### 2.4 Elemental Damage % (元素增伤)
Chino:
```
元素增伤 = 冰元素增伤%
```
Español:
```
ElementalBonus = IceElementalDMG%
```

### 2.5 Omni-Boost (全能 → 全能加伤)
Chino:
```
全能加伤 = 全能 / 2268
```
Español:
```
OmniBonus = Omni / 2268
```

## 3. Conversión de Defensa del Enemigo
Chino:
```
防御修正 = 1 - 怪物防御 / (怪物防御 + 1400)
```
Español:
```
DefenseModifier = 1 - EnemyDEF / (EnemyDEF + 1400)
```

## 4. Ataque Base del Ice Mage (面板攻击)
Chino:
```
面板攻击 = 魔法攻击 + 智力 × 系数
```
Español:
```
BaseATK = MATK + Intellect × Coefficient
```

## 5. Lucky System (para fórmulas generales)

### 5.1 Lucky Multiplier (幸运倍率)
Chino:
```
幸运倍率 = 0.4 + 0.25 × 幸运概率
```
Español:
```
LuckyMultiplier = 0.4 + 0.25 × LuckChance
```

### 5.2 Lucky Bonus (幸运增效)
Chino:
```
幸运增效 = 1 + 幸运概率
```
Español:
```
LuckyBonus = 1 + LuckChance
```

## 6. Fórmula Final de Daño — Ice Mage

Chino:
```
最终伤害
= (面板攻击 * 防御修正 + 精炼攻击 + 元素攻击)
  * 幸运特效倍率
  * (1 + 幸运增效 + 其他加伤)
  * (1 + 对应元素加伤)
  * (1 + 全能加伤)
  * (1 + 暴击率 * 暴击伤害)
```

Español:
```
FinalDamage =
  (BaseATK × DefenseModifier + RefineATK + ElementalATK)
× LuckyMultiplier
× (1 + LuckyBonus + OtherDMG)
× (1 + ElementalBonus)
× (1 + OmniBonus)
× (1 + CritRate × CritDMG)
```

## 7. Ejemplos Numéricos

### 7.1 Ejemplo: 风哥被动伤害
Chino:
```
= (2176 × 0.92 + 544)
× 0.56
× (1 + 0.4878 + 0.15)
× (1 + 0.1555)
= 2698
```

### 7.2 Ejemplo: 哥布林爪手 / 异蜂被动伤害
Chino:
```
= (2176 × 0.7 + 544)
× 0.28
× (1 + 0.4878 + 0.15)
× (1 + 0.1555)
= 1095
```

## 8. Resumen para Ice Mage

| Stat | Conversión |
|------|------------|
| Crit Rate | Crit / 1512 |
| Crit DMG | CritDMG / 1512 |
| Attack Speed | Haste / 756 |
| Elemental DMG | % directo |
| Omni Bonus | Omni / 2268 |
| Defense Modifier | 1 − DEF/(DEF+1400) |
| Base ATK | MATK + INT×coef. |
| Lucky Multiplier | 0.4 + 0.25×Luck |
| Lucky Bonus | 1 + Luck |
| Fórmula final | sección 6 |

## 9. Notas Importantes para Ice Mage
- Ice Mage escala con MATK, Intellect, Ice Elemental, Omni, Crit, CritDMG
- Lucky es secundario para esta clase
- Omni tiene alta sinergia
- Haste no aumenta daño directamente
