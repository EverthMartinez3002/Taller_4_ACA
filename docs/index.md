# Pokemon API Documentation

¡Bienvenido a la documentación oficial de Pokemon API! Esta API te permite acceder a información detallada sobre Pokemon, gestionar batallas y entrenar a tus Pokemon favoritos.

![Pokemon Logo](img/pokemon-logo.png)

## ¿Qué puedes hacer?

- **🔍 Buscar Pokemon**: Encuentra información detallada sobre cualquier Pokemon
- **⚔️ Crear Batallas**: Simula batallas entre Pokemon
- **�‍🎓 Gestionar Entrenadores**: Administra perfiles de entrenadores
- **📊 Estadísticas**: Accede a stats, habilidades y movimientos

!!! tip "Consejo"
    Si eres nuevo, te recomendamos empezar con nuestra [Guía de Inicio Rápido](guia/inicio.md) para configurar tu primera llamada a la API.

## Pokemon Más Populares

| Pokemon | Tipo | Poder | Rareza |
|---------|------|-------|--------|
| Pikachu | Eléctrico | 320 | Común |
| Charizard | Fuego/Volador | 534 | Raro |
| Mewtwo | Psíquico | 680 | Legendario |
| Mew | Psíquico | 600 | Mítico |

## Ejemplo Rápido

Aquí tienes un ejemplo de cómo obtener información de Pikachu:

=== "JavaScript"

    ```javascript
    const response = await fetch('https://api.pokemon.com/v1/pokemon/pikachu', {
        headers: {
            'Authorization': 'Bearer tu_api_key'
        }
    });
    const pikachu = await response.json();
    console.log(pikachu.name); // "Pikachu"
    ```

=== "Python"

    ```python
    import requests
    
    response = requests.get(
        'https://api.pokemon.com/v1/pokemon/pikachu',
        headers={'Authorization': 'Bearer tu_api_key'}
    )
    pikachu = response.json()
    print(pikachu['name'])  # "Pikachu"
    ```

=== "cURL"

    ```bash
    curl -H "Authorization: Bearer tu_api_key" \
         https://api.pokemon.com/v1/pokemon/pikachu
    ```

!!! warning "Autenticación Requerida"
    Necesitas una API key válida para acceder a los endpoints. Consulta nuestra [guía de autenticación](guia/autenticacion.md) para obtener tu clave.

## Enlaces Útiles

- [🚀 Inicio Rápido](guia/inicio.md) - Primeros pasos
- [� Autenticación](guia/autenticacion.md) - Configura tu API key
- [� Endpoints](guia/endpoints.md) - Lista completa de endpoints
- [� Pokemon](api/pokemon.md) - API de Pokemon
- [⚔️ Batallas](api/batallas.md) - Sistema de batallas
---