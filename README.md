# Solver de Circuitos RLC
## Recursos para resolver analíticamente ecuaciones diferenciales de circuitos RLC

Este proyecto contiene herramientas para resolver circuitos RLC serie usando métodos analíticos.

## 📁 Archivos Incluidos

### 1. `rlc_solver.py` - Módulo Python
Clase `RLCSolver` para resolver circuitos RLC analíticamente.

**Características:**
- Resuelve la EDO: $L \cdot q'' + R \cdot q' + \frac{1}{C} \cdot q = V$
- Entrega funciones compiladas: `q(t)`, `i(t)`, `V_L(t)`
- Maneja casos: subamortiguado, críticamente amortiguado, sobreamortiguado

**Uso básico:**
```python
from rlc_solver import RLCSolver

solver = RLCSolver(L=1, R=2, C=0.5, V=4)
q_func, i_func, v_l_func = solver.get_functions(q0=5, i0=6)

# Evaluar en tiempo t=1
q_t = q_func(1)  # Carga
i_t = i_func(1)  # Corriente
v_l_t = v_l_func(1)  # Voltaje en inductor
```

### 2. `RLC_Interactivo.ipynb` - Notebook Jupyter
Notebook interactivo para resolver circuitos RLC paso a paso.

**Secciones:**
1. Importar librerías y configurar formato
2. Definir parámetros del circuito RLC
3. Resolver la ecuación diferencial
4. Calcular corriente y voltaje en el inductor
5. Visualizar resultados con gráficas
6. Verificar la solución

**Cómo usar:**
- Abrir en Jupyter Notebook o Google Colab
- Ejecutar celdas secuencialmente
- Ingresar parámetros cuando se solicite: L, R, C, V, q(0), i(0)
- Visualizar gráficas y tabla de valores

## 🔬 Fundamento Matemático

### Ecuación diferencial del circuito RLC serie
$$L \frac{d^2q}{dt^2} + R \frac{dq}{dt} + \frac{1}{C}q = V(t)$$

Donde:
- **q(t)**: Carga en el capacitor (culombios)
- **i(t) = q'(t)**: Corriente (amperios)
- **V_L(t) = L \cdot i'(t)**: Voltaje en el inductor (voltios)
- **V_R(t) = R \cdot i(t)**: Voltaje en la resistencia (voltios)

### Tipos de respuesta
La solución depende de la ecuación característica: $Lr^2 + Rr + \frac{1}{C} = 0$

**Discriminante:** $\Delta = R^2 - 4L/C$

- **$\Delta > 0$** (Sobreamortiguado): Dos raíces reales distintas
- **$\Delta = 0$** (Críticamente amortiguado): Raíz doble
- **$\Delta < 0$** (Subamortiguado): Dos raíces complejas conjugadas

## 📊 Ejemplo de Uso

**Parámetros:**
- L = 1 H
- R = 2 Ω
- C = 1/3 F
- V = 4 V
- q(0) = 5 C
- i(0) = 6 A

**Ecuación diferencial:**
$$q'' + 2q' + 3q = 4$$

**Solución:**
$$q(t) = \left(\frac{29\sqrt{2}}{6}\sin(\sqrt{2}t) + \frac{11}{3}\cos(\sqrt{2}t)\right)e^{-t} + \frac{4}{3}$$

## 🚀 Requisitos

```
sympy >= 1.10
numpy >= 1.20
matplotlib >= 3.3
scipy >= 1.6
```

Instalar con:
```bash
pip install sympy numpy matplotlib scipy
```

## 📝 Notas

- El módulo `rlc_solver.py` utiliza **SymPy** para cálculo simbólico
- El notebook incluye verificación automática de las soluciones
- Las gráficas muestran el comportamiento dinámico del circuito
- Compatible con Python 3.7+

## 🔗 Relación con el archivo original

Este proyecto extrae la lógica del notebook `Notebook_Interactivo_EDO_orden2.txt` y la adapta específicamente para circuitos RLC, con énfasis en:
- Carga del capacitor q(t)
- Corriente i(t)
- Voltaje en el inductor V_L(t)

---

**Autor:** Desarrollo basado en solución de EDO de orden 2  
**Fecha:** 2025
