# Batallas API

El sistema de batallas te permite simular combates entre Pokemon con resultados realistas basados en estadísticas.

## Crear Batalla

```http
POST /v1/battle
```

Inicia una nueva batalla entre dos Pokemon.

**Body de la petición:**

```json
{
    "pokemon1_id": 25,
    "pokemon2_id": 6,
    "terrain": "campo",
    "weather": "soleado"
}
```

**Parámetros:**

| Campo | Tipo | Requerido | Descripción |
|-------|------|-----------|-------------|
| `pokemon1_id` | integer | Sí | ID del primer Pokemon |
| `pokemon2_id` | integer | Sí | ID del segundo Pokemon |
| `terrain` | string | No | Tipo de terreno (campo, agua, montaña) |
| `weather` | string | No | Clima (soleado, lluvioso, nevando) |

=== "Ejemplo de Request"

    ```javascript
    const battle = await fetch('https://api.pokemon.com/v1/battle', {
        method: 'POST',
        headers: {
            'Authorization': 'Bearer tu_api_key',
            'Content-Type': 'application/json'
        },
        body: JSON.stringify({
            pokemon1_id: 25, // Pikachu
            pokemon2_id: 6,  // Charizard
            terrain: "campo"
        })
    });
    ```

=== "Respuesta"

    ```json
    {
        "battle_id": "battle_abc123",
        "status": "completed",
        "winner": {
            "id": 25,
            "name": "Pikachu"
        },
        "loser": {
            "id": 6,
            "name": "Charizard"
        },
        "battle_log": [
            {
                "turn": 1,
                "attacker": "Pikachu",
                "move": "Impactrueno",
                "damage": 45,
                "effectiveness": "super_efectivo"
            }
        ],
        "duration": "00:02:34",
        "total_turns": 6
    }
    ```

## Obtener Batalla

```http
GET /v1/battle/{battle_id}
```

Recupera los detalles de una batalla específica.

## Historial de Batallas

```http
GET /v1/battles?trainer_id={id}
```

Obtiene el historial de batallas de un entrenador.

!!! warning "Limitaciones"
    - Máximo 10 batallas simultáneas por usuario
    - Cada batalla tiene un timeout de 5 minutos
    - Los resultados se basan en algoritmos de probabilidad

## Tipos de Terreno

Los diferentes terrenos afectan las batallas:

- **Campo**: Sin modificadores especiales
- **Agua**: +20% daño para tipos Agua
- **Montaña**: +15% defensa para tipos Roca/Tierra
- **Bosque**: +10% velocidad para tipos Planta

Para crear un entrenador y gestionar tu equipo, consulta [Entrenadores API](entrenadores.md).
