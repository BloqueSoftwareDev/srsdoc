# Game Name Here
> Game Design Document

# Table of Content

- [Game Design](#game-design)
    - [Summary](#summary)
    - [Gameplay](#gameplay)
    - [Mindset](#mindset)
- [Technical](#technical)
    - [Screens](#screens)
    - [Controls](#controls)
    - [Mechanics](#mechanics)
- [Level Design](#level-design)
    - [Themes](#themes)
    - [Game Flow](#game-flow)
- [Development](#development)
    - [Abstract Classes / Components](#abstract-classes--components)
    - [Derived Classes / Component Compositions](#derived-classes--component-compositions)
- [Graphics](#graphics)
    - [Style Attributes](#style-attributes)
    - [Graphics Needed](#graphics-needed)
- [Sounds/Music](#soundsmusic)
    - [Style Attributes](#style-attributes-1)
    - [Sounds Needed](#sounds-needed)
    - [Music Needed](#music-needed)
- [Schedule](#schedule)



# Game Design

## Summary
Wrecking Pandemic es un platformer 2D sobre una ingeniera biomédica que debe salvar al mundo de una pandemia y de aquellos que no siguen las regulaciones. Ella diseña y construye las herramientas perfectas para cada nivel; incluyendo un spray curativo, pócima de doble salto y armadura protectiva.

## Gameplay
Al ser un platformer 2D, Wrecking Pandemic incluye principalmente movimiento de izquierda a derecha con saltos para evitar enemigos y llegar a plataformas. El objetivo del juego es llegar al final, derrotar el mini-boss y conseguir el componente de la cura del nivel correspondiente. Al principio de cada nivel Emily diseña una herramienta que le otorga una habilidad perfecta para el nivel, y debe de usar esta para sobrepasar los objetivos particulares del nivel. El jugador debe adaptarse para estas situaciones únicas, pero siempre manteniendo la esencia de moverse de izquierda a derecha y saltar. 

## Mindset
Es deseado que el jugador tenga la mentalidad de empoderamiento y aventura, para motivarlo hacia la toma de decisión de una carrera relacionada a STEM. Esto se hará a través de las grandes habilidades del personaje principal Emily, y los grandes obstáculos que logra sobrepasar por el bien del mundo. Al ver la capacidad y el resultado del esfuerzo de Emily, el jugador sentirá todo esto y más.

# Technical
 
## Screens

```
1. Title Screen
2. Between Levels Screen
3. Game
    a. Power-ups Obtained
4. End Credits
```

## Controls
El jugador no puede modificar los controles, pero se les dirá cuales son al comenzar el juego. El jugador podrá interactuar con ciertos objetos en su alrededor, incluyendo las mesas de construcción, checkpoints, y enemigos. Esto principalmente se hace simplemente caminando por el objeto, aunque el jugador podrá derrotar a los enemigos presionando la tecla "P" para disparar el proyectil.

## Mechanics
Al comenzar el juego el avatar solo puede moverse hacia los lados y saltar una sola vez. Durante el transcurso del juego obtienes nuevas habilidades, en el siguiente orden:

```
Principio del nivel 1 - Obtienes la habilidad de disparar el proyectil de spray al presionar la tecla "P". Este proyectil destruye a los enemigos comunes con un solo golpe, pero a los bosses se les debe disparar varias veces.

Principio del nivel 2 - Obtienes la habilidad de saltar una vez adicional después de tu primer salto. Esto se hace a través de un int que mide cuantos saltos te quedan, comenzando con 1 pero volviendose 2 al conseguir esta habilidad. Este int se resettea al tocar el suelo después de saltar.

Principio del nivel 3 - Obtienes la habilidad de protección con el escudo, bloqueando proyectiles con la tecla "O". Esos proyectiles solo se pueden bloquear frente a Emily, proyectiles detrás aún causarán daño.
```

Cada boss tiene sus propias mecánicas:


```
El Anti-masker tiene la habilidad de llamar a mini anti-maskers para correr hacia el jugador, aunque no sean atacados, estos siempre se moveran a la derecha sin regresar. Si son atacados, son derrotados en un solo golpe como el resto de los enemigos comunes. El anti-masker también tiene la habilidad de gritar tan fuerte que lanza un proyectil que se debe evitar saltando por encima o caminando por debajo. El anti-masker debe recibir 5 ataques antes de ser derrotado y tiene unos segundos de invulnerabilidad al ser atacado.

El granjero tiene la habilidad de 
```

Las mecánicas principales son el doble salto y el proyectil. Esto se cumplirá a través de checks de estado para ver si puedes saltar, al igual que mecánicas dentro del sistema para diseñar proyectiles que se originan del personaje y se hacen más grandes al alejarse de este.

The enemies walk left to right 

# Level Design
 (Note : These sections can safely be skipped if they’re not relevant, or you’d rather go about it another way. For most games, at least one of them should be useful. But I’ll understand if you don’t want to use them. It’ll only hurt my feelings a little bit.)

## Themes
```
1.	City at Night
    a.	Mood
        i.	Suspenseful, dark, dangerous
    b.	Objects
        i.	Ambient
            1.	Trash
            2.	Moonlight
            3.	Cars
            4.	Advertising Billboards
        ii.	Interactive
            1.	Wooden Platforms
            2.	Sick Citizens (Enemy)
            3.	Chasms
            4.	Anti-masker (Karen) boss 
2.	Plains
    a.	Mood
        i.	Peaceful, calm, active
    b.	Objects
        i.	Ambient
            1.	Trees
            2.	Grass
            3.	Critters
            4.	Fences
        ii.	Interactive
            1.	Sick Countrymen (Enemy)
            2.	Platforms
            3.	Workbench
            4.	Sick Farmer boss
3.	Cavern
    a.	Mood
        i.	Spooky, threatening, silent
    b.	Objects
        i.	Ambient
            1.	Stalagmite
            2.	Dew drops
            3.	Critters
            4.	Danger signs
        ii.	Interactive
            1.	Mini-Bats (Enemy)
            2.	Stalagmites/Stalactites
            3.	Workbench
            4.	Bat Boss

```

_(example)_

## Game Flow
```
1.	Player starts in forest
2.	Pond to the left, must move right
3.	To the right is a hill, player jumps to traverse it (“jump” taught)
4.	Player encounters castle - door’s shut and locked
5.	There’s a window within jump height, and a rock on the ground
6.	Player picks up rock and throws at glass (“throw” taught)
7.	… etc.
```
(example)


# Development
 
## Abstract Classes / Components
```
1.	BasePhysics
    a.	BasePlayer
    b.	BaseEnemy
    c.	BaseObject
2.	BaseObstacle
3.	BaseInteractable
```
_(example)_ 

## Derived Classes / Component Compositions
```
1.	BasePlayer
    a.	PlayerMain
    b.	PlayerUnlockable
2.	BaseEnemy
    a.	EnemyWolf
    b.	EnemyGoblin
    c.	EnemyGuard (may drop key)
    d.	EnemyGiantRat
    e.	EnemyPrisoner
3.	BaseObject
    a.	ObjectRock (pick-up-able, throwable)
    b.	ObjectChest (pick-up-able, throwable, spits gold coins with key)
    c.	ObjectGoldCoin (cha-ching!)
    d.	ObjectKey (pick-up-able, throwable)
4.	BaseObstacle
    a.	ObstacleWindow (destroyed with rock)
    b.	ObstacleWall
    c.	ObstacleGate (watches to see if certain buttons are pressed)
5.	BaseInteractable
    a.	InteractableButton
```
_(example)_

# Graphics

## Style Attributes
What kinds of colors will you be using? Do you have a limited palette to work with? A post-processed HSV map/image? Consistency is key for immersion.

What kind of graphic style are you going for? Cartoony? Pixel-y? Cute? How, specifically? Solid, thick outlines with flat hues? Non-black outlines with limited tints/shades? Emphasize smooth curvatures over sharp angles? Describe a set of general rules depicting your style here.

	Well-designed feedback, both good (e.g. leveling up) and bad (e.g. being hit), are great for teaching the player how to play through trial and error, instead of scripting a lengthy tutorial. What kind of visual feedback are you going to use to let the player know they’re interacting with something? That they *can* interact with something?

## Graphics Needed
```
1.	Characters
    a.	Human-like
        i.	Goblin (idle, walking, throwing)
        ii.	Guard (idle, walking, stabbing)
        iii.	Prisoner (walking, running)
    b.	Other
        i.	Wolf (idle, walking, running)
        ii.	Giant Rat (idle, scurrying)
2.	Blocks
    a.	Dirt
    b.	Dirt/Grass
    c.	Stone Block
    d.	Stone Bricks
    e.	Tiled Floor
    f.	Weathered Stone Block
    g.	Weathered Stone Bricks
3.	Ambient
    a.	Tall Grass
    b.	Rodent (idle, scurrying)
    c.	Torch
    d.	Armored Suit
    e.	Chains (matching Weathered Stone Bricks)
    f.	Blood stains (matching Weathered Stone Bricks)
4.	Other
    a.	Chest
    b.	Door (matching Stone Bricks)
    c.	Gate
    d.	Button (matching Weathered Stone Bricks)
```
_(example)_

_(Note : If you’re soloing you might not need to define this part, as you can just use the Derived_ 
_Classes + Themes section as a reference. It’s up to you.)_


# Sounds/Music
 
## Style Attributes
Again, consistency is key. Define that consistency here. What kind of instruments do you want to use in your music? Any particular tempo, key? Influences, genre? Mood?

Stylistically, what kind of sound effects are you looking for? Do you want to exaggerate actions with lengthy, cartoony sounds (e.g. mario’s jump), or use just enough to let the player know something happened (e.g. mega man’s landing)? Going for realism? You can use the music style as a bit of a reference too.
	
Remember, auditory feedback should stand out from the music and other sound effects so the player hears it well. Volume, panning, and frequency/pitch are all important aspects to consider in both music and sounds - so plan accordingly!

## Sounds Needed
```
1.	Effects
    a.	Soft Footsteps (dirt floor)
    b.	Sharper Footsteps (stone floor)
    c.	Soft Landing (low vertical velocity)
    d.	Hard Landing (high vertical velocity)
    e.	Glass Breaking
    f.	Chest Opening
    g.	Door Opening
2.	Feedback
    a.	Relieved “Ahhhh!” (health)
    b.	Shocked “Ooomph!” (attacked)
    c.	Happy chime (extra life)
    d.	Sad chime (died)
```
_(example)_

## Music Needed
```
1.	Slow-paced, nerve-racking “forest” track
2.	Exciting “castle” track
3.	Creepy, slow “dungeon” track
4.	Happy ending credits track
5.	Rick Astley’s hit #1 single “Never Gonna Give You Up”
``` 
_(example)_

_(Note : Again, if you’re soloing you might be able to / want to skip this section. It’s up to you.)_

# Schedule
 
(what is a schedule, i don’t even. list is good enough, right? if not add some dates i guess)

```
1.	develop base classes
    a.	base entity
        i.	base player
        ii.	base enemy
        iii.	base block
    b.	base app state
        i.	game world
        ii.	menu world
2.	develop player and basic block classes
    a.	physics / collisions
3.	find some smooth controls/physics
4.	develop other derived classes
    a.	blocks
        i.	moving
        ii.	falling
        iii. breaking
        iv.	cloud
    b.	enemies
        i. soldier
        ii.	rat
        iii. etc.
5.	design levels
a.	introduce motion/jumping
b.	introduce throwing
c.	mind the pacing, let the player play between lessons
6.	design sounds
7.	design music
```
_(example)_

