# ChallengeYou Resurrection
The plan for the ChallengeYou Resurrection 

# Table of contents
1. [Introduction](#intro)
2. [Languages](#lang)
    1. [C++](#lang-cpp)
    2. [Lua](#lang-lua)
3. [Level Format](#lvl-fmt)
    1. [Sector 7](#fmt-sect-7)


## Introduction <div id = "intro">
  ChallengeYou Resurrection (CYR) is a fan-made project created by people who loved ChallengeYou back in the day (2008-2009 times). The original game over on [ChallengeYou.com](challengeyou.com) does not work anymore on newer systems, and so we want to recreate the game so we can once again experience part of our childhoods.
  
## Languages <div id = "lang">
  CYR will be using multiple languages for the different aspects of the game.
  
### C++  <div id = "lang-cpp">
  C++ will used for the rendering.
    
  Libraries will used to assist in doing this.
  
##### SFML
SFML will be used as a windowing library and for other basic utilities, such as keyboard input, mouse input, and texture loading.

##### OpenGL 
OpenGL will be used for the 3D rendering. GLAD will be used to load the OpenGL functions.

##### GLM
GLM will be used for the maths relating to OpenGL
  
### Lua  <div id = "lang-lua">
  Lua will be used for the game logic.

## Level Format <div id = "lvl-fmt">
The original ChallengeYou game format looked something like this:
```
#walls: [[10, 0, 220, 290, [4, 4], 1], [15, 0, 220, 250, [2, 2],
    2], [0, 40, 220, 250, [2, 2], 2], [0, 30, 260, 250, [2, 2], 2],
    [-40, 0, 260, 290, [2, 2], 2], [-15, 0, 260, 250, [2, 2], 2], 
    [0, -40, 260, 290, [4, 4] ..etc
```
This had some problems such as file size, as quite a lot of the data in this file was unnessary commas, brackets, hashtags, and spaces. So, to overcome this, we decided it would be best to convert the games to a custom binary format, that would not only reduce the file size, but be a lot easier to read and write from/to.
    
It has the following format:

| Area     | Data             | Notes                                               |Type|
|----------|------------------|-----------------------------------------------------|------|
| Sector 1 | Game creator     | 2 to 13 bytes in size (12 + null terminator)        |String|
| Sector 2 | Game name        | 2 to 21 bytes in size (20 + null terminator)        |String|
| Sector 3 | Number of Floors | 1 to 20                                             |Byte  |
| Sector 4 | Music            | 0: Default, 1: Scary, 2: Lounge, 3: Space, 4: Asian |Byte  |
| Sector 5 | Theme            | 0: Default, 1: Night, 2: Scary                      |Byte  |
| Sector 6 | Weather          | 0: Default, 1: Rain, 2: Fog, 3: Fog II, 4: Snow     |Byte  |
| Sector 7 | Game data        | More info below                                     |      |
| EOF      | End of file      | Magic number 0xFFFF                                 |Integer |

### Sector 7 <div id = "fmt-sect-7">
Sector 7 is the bulk of the file. It contains information about the entire level, such as walls, object properties, location of pickups, and location of enemies.
    
 
