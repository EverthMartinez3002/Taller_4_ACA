# Inicio Rápido - Pokemon API

¡Bienvenido entrenador! Esta guía te ayudará a capturar tu primer Pokemon usando nuestra API en menos de 5 minutos.

![Pikachu Welcome](/img/pokemon-logo.png)

## Requisitos Previos

Antes de comenzar tu aventura Pokemon, necesitas:

- Conocimientos básicos de APIs REST
- Una herramienta para hacer peticiones HTTP (Postman, cURL, o código)
- Ganas de ser el mejor entrenador Pokemon

## Paso 1: Registrarte como Entrenador

### 1.1 Crear Cuenta de Entrenador

1. Visita el [Portal de Entrenadores](https://portal.pokemon-api.com)
2. Haz clic en "Convertirse en Entrenador"
3. Completa tu perfil:
   ```
   Nombre de Entrenador: Ash Ketchum
   Email: ash@pokemon.com
   Ciudad de Origen: Pueblo Paleta
   Pokemon Favorito: Pikachu
   ```

### 1.2 Verificar tu Pokedex Digital

Después del registro, recibirás un email con tu Pokedex digital. ¡Actívala haciendo clic en el enlace!

### 1.3 Obtener tu Licencia de Entrenador (API Key)

1. Inicia sesión en tu portal
2. Ve a "Mi Pokedex" → "Licencias"
3. Genera tu "Licencia de Entrenador Oficial"
4. Guarda tu API Key secreta

!!! warning "¡Mantén tu licencia segura!"
    Tu API Key es como tu insignia de entrenador. No la compartas con otros entrenadores.

## Paso 2: Configurar tu Equipo de Desarrollo

### URL Base del Centro Pokemon
```
https://api.pokemon.com/v1/
```

### Headers de Entrenador Requeridos
```http
Authorization: Bearer TU_LICENCIA_DE_ENTRENADOR
Content-Type: application/json
Accept: application/json
```

### Configuración por Lenguaje

=== "JavaScript (Entrenador Web)"

    ```javascript
    // Configuración de tu Pokedex digital
    const POKEMON_API_BASE = 'https://api.pokemon.com/v1';
    const MI_LICENCIA = 'tu_licencia_de_entrenador_aqui';
    
    const pokedexHeaders = {
        'Authorization': `Bearer ${MI_LICENCIA}`,
        'Content-Type': 'application/json',
        'Accept': 'application/json'
    };
    
    // Función para buscar Pokemon
    async function buscarPokemon(nombre) {
        const response = await fetch(`${POKEMON_API_BASE}/pokemon/${nombre}`, {
            headers: pokedexHeaders
        });
        return await response.json();
    }
    ```

=== "Python (Entrenador Científico)"

    ```python
    import requests
    import json
    
    # Tu laboratorio Pokemon
    POKEMON_API_BASE = 'https://api.pokemon.com/v1'
    MI_LICENCIA = 'tu_licencia_de_entrenador_aqui'
    
    # Configuración del Pokedex
    pokedex_headers = {
        'Authorization': f'Bearer {MI_LICENCIA}',
        'Content-Type': 'application/json',
        'Accept': 'application/json'
    }
    
    def buscar_pokemon(nombre):
        """Busca un Pokemon en la Pokedex Nacional"""
        response = requests.get(
            f'{POKEMON_API_BASE}/pokemon/{nombre}',
            headers=pokedex_headers
        )
        return response.json()
    ```

=== "cURL (Entrenador Terminal)"

    ```bash
    # Variables de entrenador
    export POKEMON_API_BASE="https://api.pokemon.com/v1"
    export MI_LICENCIA="tu_licencia_de_entrenador_aqui"
    
    # Función para capturar Pokemon
    buscar_pokemon() {
        curl -H "Authorization: Bearer $MI_LICENCIA" \
             -H "Content-Type: application/json" \
             -H "Accept: application/json" \
             "$POKEMON_API_BASE/pokemon/$1"
    }
    
    # Uso: buscar_pokemon pikachu
    ```

## Paso 3: ¡Tu Primer Encuentro Pokemon!

Vamos a encontrar a Pikachu, el Pokemon más famoso:

=== "JavaScript"

    ```javascript
    // ¡Encuentra a Pikachu!
    async function encontrarPikachu() {
        try {
            console.log('🔍 Buscando a Pikachu...');
            
            const pikachu = await buscarPokemon('pikachu');
            
            console.log('⚡ ¡Pikachu encontrado!');
            console.log(`Nombre: ${pikachu.name}`);
            console.log(`Tipo: ${pikachu.type.join(', ')}`);
            console.log(`HP: ${pikachu.stats.hp}`);
            console.log(`Habilidades: ${pikachu.abilities.join(', ')}`);
            
            return pikachu;
        } catch (error) {
            console.error('❌ Pikachu se escapó:', error);
        }
    }
    
    // ¡Ejecuta tu primera captura!
    encontrarPikachu();
    ```

=== "Python"

    ```python
    def encontrar_pikachu():
        """¡Tu primer encuentro Pokemon!"""
        try:
            print('🔍 Buscando a Pikachu...')
            
            pikachu = buscar_pokemon('pikachu')
            
            print('⚡ ¡Pikachu encontrado!')
            print(f"Nombre: {pikachu['name']}")
            print(f"Tipo: {', '.join(pikachu['type'])}")
            print(f"HP: {pikachu['stats']['hp']}")
            print(f"Habilidades: {', '.join(pikachu['abilities'])}")
            
            return pikachu
            
        except Exception as error:
            print(f'❌ Pikachu se escapó: {error}')
    
    # ¡Ejecuta tu primera captura!
    if __name__ == "__main__":
        encontrar_pikachu()
    ```

## Respuesta de tu Primer Pokemon

Si todo va bien, deberías ver algo así:

```json
{
    "id": 25,
    "name": "Pikachu",
    "type": ["Eléctrico"],
    "generation": 1,
    "stats": {
        "hp": 35,
        "attack": 55,
        "defense": 40,
        "sp_attack": 50,
        "sp_defense": 50,
        "speed": 90,
        "total": 320
    },
    "abilities": [
        "Electricidad Estática",
        "Pararrayos"
    ],
    "moves": [
        "Impactrueno",
        "Ataque Rápido",
        "Rayo",
        "Trueno"
    ],
    "region": "Kanto",
    "habitat": "Bosque",
    "capture_rate": 190,
    "is_legendary": false
}
```

!!! success "¡Felicidades, Entrenador!"
    ¡Has capturado exitosamente tu primer Pokemon usando la API! Pikachu ahora forma parte de tu equipo digital.

## Manejo de Errores Comunes

Como todo entrenador experimentado, debes saber qué hacer cuando las cosas salen mal:

| Error | Causa | Solución |
|-------|-------|----------|
| 401 - Licencia Inválida | API Key incorrecta | Verifica tu licencia de entrenador |
| 404 - Pokemon No Encontrado | Nombre incorrecto | Revisa la ortografía del Pokemon |
| 429 - Demasiados Encuentros | Rate limit excedido | Espera antes de buscar más Pokemon |
| 500 - Centro Pokemon Caído | Error del servidor | Inténtalo más tarde |

## Próximos Pasos en tu Aventura

Ahora que has capturado tu primer Pokemon, ¡es hora de convertirte en un maestro Pokemon!

### 🔗 Continúa tu Entrenamiento

- [🔐 Autenticación Avanzada](autenticacion.md) - Mejora tu licencia de entrenador
- [📋 Todos los Endpoints](endpoints.md) - Explora más funciones de la Pokedex
- [🐉 API de Pokemon](../api/pokemon.md) - Documentación completa de Pokemon
- [⚔️ Sistema de Batallas](../api/batallas.md) - ¡Lucha con otros entrenadores!
- [👨‍🎓 Gestión de Entrenadores](../api/entrenadores.md) - Administra tu perfil

### 💡 Consejos de Entrenador Experto

!!! tip "Optimiza tu Pokedex"
    Usa parámetros de filtro para encontrar Pokemon específicos:
    ```
    GET /pokemon?type=fuego&generation=1&limit=10
    ```

!!! info "Rate Limits"
    Como entrenador novato, puedes hacer 1000 peticiones por hora. ¡Los maestros Pokemon tienen límites más altos!

¡Que tengas una gran aventura, Entrenador! 🌟