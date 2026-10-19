# Laboratorio: Minimax y Poda Alfa-Beta

## Descripción
Este proyecto implementa los algoritmos Minimax y Poda Alfa-Beta para resolver un árbol de decisión simplificado.

## Objetivo
Comparar el resultado y la eficiencia de Minimax frente a Poda Alfa-Beta.

## Instalación
```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

## Ejecución
```bash
python -m src.main
```

## Pruebas
```bash
pytest --cov=src --cov-report=term-missing
```

## Preguntas de análisis
1. ¿Por qué Minimax y Alfa-Beta devuelven el mismo valor?
Devuelven el mismo valor porque la Poda Alfa-Beta no elimina ni altera ninguna opción óptima del juego. Únicamente omite explorar aquellos subárboles y ramas cuyas puntuaciones se ha demostrado matemáticamente que no pueden influir en la decisión final de jugadores racionales.
2. ¿Cuándo Alfa-Beta reduce más nodos?
Alfa-Beta reduce el máximo número de nodos cuando el árbol está adecuadamente ordenado, es decir, cuando el algoritmo evalúa primero las mejores jugadas u opciones más prometedoras para cada jugador. Esto permite alcanzar rápidamente los límites $\alpha$ y $\beta$ ($\beta \le \alpha$), podando ramas completas desde etapas tempranas de la exploración.
3. ¿Qué ocurre si el árbol está mal ordenado?
Si el árbol está mal ordenado y las mejores jugadas se encuentran al final de las ramas, los cortes de Poda Alfa-Beta se vuelven ineficaces o nulos. En el peor escenario posible, el algoritmo terminará evaluando todos los nodos del árbol, comportándose de manera idéntica al algoritmo Minimax tradicional.
4. ¿Cómo se aplicaría este algoritmo en ajedrez, damas o tres en raya?
En juegos por turnos como ajedrez, damas o tres en raya, el algoritmo se aplica de la siguiente manera:

Estados del tablero: Cada nodo del árbol representa una configuración completa del tablero de juego.

Turnos alternados: El jugador actual actúa como el nodo MAX (buscando la mejor jugada a su favor) y el oponente como el nodo MIN.

Función de evaluación / Puntuación: Para estados terminales (victoria, derrota, empate) o estados intermedios a cierta profundidad límite, una función heurística asigna un valor numérico al estado del tablero.

Toma de decisiones: El agente analiza las respuestas del oponente varios turnos hacia el futuro y selecciona el movimiento que garantice el mejor resultado en el peor escenario posible.
```
