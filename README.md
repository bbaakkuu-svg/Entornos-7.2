# Entornos-7.2


**# Entornos-7.2 - CASOS DE USO

## Ej 1: El Sistema de Iluminación Inteligente

**Contexto:** Queremos modelar una aplicación móvil sencilla para controlar las luces de una casa.

* **Actores:** Un **Usuario**.
* **Funcionalidades:** El usuario debe poder "Encender luces" y "Apagar luces".
* **Reto:** Representar la interacción básica actor-sistema.

```mermaid

graph LR

%%Entidades externas al sistema
%% Actores

Usuario((Usuario))


%% Casos de Uso

subgraph "El Sistema de Iluminación"
%% Verbo infinitivo que describe la acción
CU1([Encender luces])			 

CU2([Apagar luces])

end


%% Relaciones actor-casos de uso
%% Asociaciones simples
Usuario --- CU1		

Usuario --- CU2

```

---

## Ej 2: Gestión de Tienda Online

**Contexto:** Un sistema de comercio electrónico donde interactúan diferentes perfiles.

* **Actores: Cliente** y **Administrador**.
* **Funcionalidades:**

  * El **Cliente** puede "Comprar Producto".
  * El **Administrador** puede "Gestionar Stock".
* **Relaciones Especiales:** Al "Comprar Producto", el sistema permite de forma opcional "Aplicar Cupón Descuento" (si el cliente tiene uno).
* **Reto:** Aplicar correctamente la relación de extensión (<`<extend>`>).

```mermaid

graph LR

%%Entidades externas al sistema
%% Actores

Cliente((Cliente))

Admin((Administrador))


%% Casos de Uso

subgraph "Gestión de Tienda Online"

%% Verbo infinitivo que describe la acción 

CU1([Comprar Producto])

CU2([Aplicar Cupón Descuento])

CU3([Gestionar Stock])


%% Relación Extend

%% Relaciones de opcionalidad (Cupón Descuento)

CU2 -.->|<<extend>>| CU1

end


%% Relaciones actor-casos de uso

%% Asociaciones simples 

Cliente --- CU1	

Admin --- CU3

```

---

## Ej 3: Complejo - Plataforma de Streaming (Estilo Netflix)

**Contexto:** Un sistema con dependencias obligatorias y múltiples actores, incluyendo sistemas externos.

* **Actores: Espectador**, **Editor de Contenido** y un sistema externo llamado **Pasarela de Pagos**.
* **Funcionalidades y Relaciones:**

  * El **Espectador** puede "Reproducir Película". Para ello, el sistema debe "Validar Suscripción" obligatoriamente cada vez.
  * Al "Reproducir Película", el espectador tiene la opción de "Activar Subtítulos".
  * El **Editor de Contenido** puede "Subir Nuevo Video".
  * El sistema debe permitir "Renovar Suscripción", proceso que requiere la comunicación con la **Pasarela de Pagos**.
* **Reto:** Gestionar el límite del sistema, actores externos y la relación de inclusión (<`<include>`>).

```mermaid

graph LR

%%Entidades externas al sistema
%% Actores

Espectador(("Espectador"))

Editor(("Editor de Contenido"))

Pasarela(("Pasarela de Pagos"))


%% Casos de Uso

subgraph Plataforma de Streaming

%% Verbo infinitivo que describe la acción

UC1([Reproducir Película]) 	 

UC2([Validar Suscripción])

UC3([Activar Subtítulos])

UC4([Subir Nuevo Video])

UC5([Renovar Suscripción])

end


%% Relaciones Include y Extend

%% Relaciones de obligatoriedad
UC1 -.->|<<include>>| UC2


%% Relaciones de opcionalidad (Activar Subtítulos)
UC3 -.->|<<extend>>| UC1


%% Relaciones actor-casos de uso

%% Asociaciones simples

Espectador --- UC1

Espectador --- UC5

Editor --- UC4

Pasarela --- UC5

```

**
