# Simulación del despegue de un cohete experimental

Desafío de **Métodos Numéricos**: método de Euler y ecuaciones diferenciales de primer orden.
Aplicación web que simula el ascenso vertical de un cohete, calcula la solución analítica y compara los resultados con los métodos de **Euler**, **Heun** y **Runge-Kutta de cuarto orden (RK4)**.

**Universidad Mayor de San Andrés — Carrera de Informática**
**Estudiante:** JOSE MANUEL HUANCA TITO · **Año:** 2026

## Enlaces

| Entregable | Enlace |
|---|---|
| Aplicación web | https://josema365.github.io/simulacion-cohete/ |
| Repositorio | https://github.com/josema365/simulacion-cohete |
| Video explicativo | https://youtu.be/qi7fja_kZE8 |

## Modelo matemático

Con la segunda ley de Newton, para un cohete con empuje constante y resistencia lineal:

```
m · dv/dt = T − m·g − k·v
dy/dt = v
```

Parámetros por defecto: m = 1000 kg, T = 15000 N, g = 9,81 m/s², k = 100 kg/s, v(0) = 0, y(0) = 0.
Con ellos: `dv/dt = 5,19 − 0,1·v`.

**Solución analítica:**

```
v(t) = 51,9 · (1 − e^(−0,1·t))
y(t) = 51,9·t − 519 · (1 − e^(−0,1·t))
```

La velocidad terminal es `(T − m·g)/k = 51,9 m/s`.

##  Qué hace la aplicación

- Permite ingresar m, T, g, k, tiempo final y paso h.
- Calcula la solución exacta y las aproximaciones de Euler, Heun y RK4.
- Muestra una **tabla de iteraciones** con el error absoluto de cada método en velocidad y en altura.
- Dibuja las **gráficas** de v(t) e y(t) comparando los cuatro resultados.
- Incluye una **animación** del despegue.
- Valida los datos: k > 0, T > m·g, h ≤ tf y avisa si tf no es múltiplo de h.

## Resultados en t = 20 s (h = 2 s)

| Método | Orden | v(20) m/s | Error v | y(20) m | Error y |
|---|---|---|---|---|---|
| Euler | O(h) | 46,3273 | 1,4512 | 574,7272 | 14,5118 |
| Heun | O(h²) | 44,7664 | 0,1097 | 590,3356 | 1,0966 |
| RK4 | O(h⁴) | 44,8759 | 0,0002 | 589,2412 | 0,0022 |
| **Exacta** | — | **44,8761** | 0 | **589,2390** | 0 |

**Conclusión:** con el mismo paso, **RK4 es el más preciso**, seguido de Heun y, por último, Euler. No basta obtener un resultado numérico: hay que evaluar su error.

## Cómo ejecutarlo

```bash
git clone https://github.com/josema365/simulacion-cohete.git
cd simulacion-cohete
```
Abre `index.html` en el navegador. No necesita instalar nada; solo requiere conexión a internet para cargar Chart.js desde CDN.

## Tecnologías

- HTML5, CSS3 y JavaScript
- [Chart.js 4.4.0](https://www.chartjs.org/) para las gráficas
- LaTeX para el informe

