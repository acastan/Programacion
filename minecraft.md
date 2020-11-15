# Com programar Minecraft amb Python

De les proves que havia fet fins ara per intentar programar amb Python sobre el Minecraft al nostre institut, les coses que no han funcionat són:

---

## Ha fallat: Minecraft Pi amb VirtualBox

Per la Raspberry Pi existeix una versió antiga, gratuïta i especial de Minecraft, anomenada Minecraft Pi, que permet programar molt fàcilment sobre Minecraft amb Python.
 
He intentat descarregar la distribució Raspbian per Raspberry PI, però en una versió especial per PC, de l’adreça <https://www.raspberrypi.org/downloads/raspberry-pi-desktop/>, i executar-la sobre el nostre VirtualBox, però llavors he trobat que la distribució Raspbian per PC no ve amb l'aplicació Minecraft Pi.

---

## Ha fallat: Minecraft per Windows amb la nostra versió de VirtualBox

El programari Minecraft es pot descarregar lliurement a la seva web, però cal pagar per un compte d'usuari per poder jugar. No he trobat una versió d'avaluació, així que per fer proves a classe he acabat buscant una versió pirata.
 
La versió pirata fàcil de trobar és per la plataforma Windows, però llavors al nostre institut, on treballem amb Linux, l'hauríem d'executar sobre una màquina virtual Windows. Tanmateix, la versió de VirtualBox del nostre institut no proporciona l'acceleració gràfica necessària per executar Minecraft per Windows sobre una màquina virtual.

La versió educativa de Minecraft tampoc té versió nativa per Linux, i la seva versió per Windows tampoc funciona sobre el nostre VirtualBox.

---

## Ha funcionat: Minecraft per Linux + servidor Spigot + plugin RaspberryJuice + llibreries mcpi

Ho podrem deixar tot a la carpeta "dades". No cal instal·lar res. Tant Minecraft com el servidor Spigot s'executen sobre Java.

Per executar codi Python a Minecraft hem d'instal·lar un servidor de Minecraft, com Spigot o Paper, que contingui el plugin RaspberryJuice. Llavors quan l'usuari llenci el joc Minecraft ha d'escollir joc multijugador, i escriure la IP de l'ordinador on s'executa Spigot.

Els passos són:

 01. Descarrega el servidor de Spigot adient de l'adreça:

     <https://getbukkit.org/download/spigot>

     Spigot en executar-se generarà molts fitxers. Millor que el tinguis en una carpeta per ell sol.

 02. Descarrega RaspberryJuice de l'adreça:

     <https://www.spigotmc.org/resources/raspberryjuice.22724/>

     Crea una carpeta anomenada plugins dintre de la carpeta on tinguis el servidor Spigot, i posa aquest fitxer raspberryjuice-1.12.1.jar dintre d'aquesta carpeta "plugins"

 03. Executa el servidor escrivint al terminal: `java -jar spigot-1.16.3.jar`

     Aquesta primera execució crearà un fitxer "eula.txt" que et demanarà modificar. Canvia a "eula.txt" on diu `eula=false` per `eula=true`

     Si el Minecraft era pirata, canvia també al fitxer "server.properties" d'Spigot, on diu `online-mode=true` per `online-mode=false`

     Si vols treballar en mode "creatiu" enlloc de mode "supervivència", canvia també al fitxer "server.properties" d'Spigot, on diu `gamemode=survival` per `gamemode=creative`

     Executa de nou el servidor escrivint al terminal: `java -jar spigot-1.16.3.jar`

 04. Descarrega Minecraft 1.16.3 pirata per Linux de l'adreça:

     <https://btdb.eu/search/minecraft%20linux/0/>

     Descomprimeix Minecraft 1.16.3 i executa el joc Minecraft. Selecciona menú "Multiplayer". Al submenú "Direct Connect" escriu 127.0.0.1 o localhost , per jugar dins el teu propi servidor Spigot
     
     Ara que estàs a una partida de Minecraft hauràs de prèmer simultàniament les tecles F3 + P per tal que cada vegada que deixis la finestra de Minecraft, aquesta no aturi el joc.

 05. A la carpeta on vulguis guardar el teu programa Python, descarrega les llibreries per Minecraft de la següent adreça:

     <https://github.com/martinohanlon/mcpi>

     La carpeta mcpi ha d'estar disponible on escrius el programa

 06. Comença els teus programes amb una línia `import mcpi` i fes servir les funcions de la llibreria:

     <http://www.stuffaboutcode.com/p/minecraft-api-reference.html>

     Aquí hi ha un llibre gratuït amb programes per fer proves:

     <https://magpi.raspberrypi.org/books/essentials-minecraft-v1/pdf>

---

## Ha funcionat a casa: paquets Minetest i PyCraft per Linux des dels repositoris

Cal instal·lar programari, i no tenim permisos, però a casa m'ha funcionat bé Minetest amb el mòdul Pycraft, que és una opció gratuïta i també més senzilla que Minecraft amb RaspberryJuice.

Aquí deixo la recepta. Ho he fet sobre Debian Testing, però estic segur que els paquets estan disponibles als repositoris de les últimes Ubuntu.

Minetest és un clon de Minecraft, escrit en el llenguatge de programació Lua. Pycraft és l'adaptació per Minetest del mòdul RaspberryJuice. Tot el que hem programat per Minecraft + RaspberryJuice hauria de funcionar a Minetest + Pycraft.

Els passos són:

 01. Instal·la els paquets dels repositoris:

         sudo apt install minetest minetest-mod-pycraft python3-minecraftpi
        
 02. Arrenca Minetest. Selecciona la casella "mode creatiu" i desselecciona la casella "permetre danys"
 
     Fes clic a "Nou". Un cop creat el nou joc, abans d'executar-lo clica "Configurar".
 
     A "Configurar" selecciona el mòdul "pycraft" i fes clic a la casella "Activat". Guarda canvis.
    
     A la pestanya "Configuració" clica el botó "All Settings". Clica la casella "Mostra els noms tècnics". Busca "secur" i t'apareixerà "secure.enable_security" , que hauràs de donar-li el valor "Desactivat" fent doble clic sobre ell.
    
     (Hagués estat millor no tocar l'opció secure.enable_security, i en canvi donar el valor pycraft a l'opció secure.trusted_mods, però a mi no m'ha funcionat).
    
     Prem <esc>, torna a la pestanya "Start Game" i clica el botó "Jugar Joc".
    
     Els canvis han quedat guardats (joc creat, mòdul pycraft activat, i seguretat dels mòduls inhabilitada) i no caldrà que els proper cops que vulguis obrir el joc repeteixis tots els passos anteriors.

---

## API i REFERÈNCIES

 * <https://github.com/zhuowei/RaspberryJuice>

 * <https://www.stuffaboutcode.com/p/minecraft-api-reference.html>

 * <https://minecraft.gamepedia.com/>

---

## API: FUNCIONS

| COMANDA                                            | ACCIÓ                                         |
| -------------------------------------------------- | --------------------------------------------- |
| Minecraft.getBlock(x,y,z) -> id:int                | Obté tipus de bloc a les coordenades          |
| Minecraft.getBlockWithData(x,y,z) -> Block         | Obté informació del block a les coordenades   |
| Minecraft.getBlocks(x0,y0,z0,x1,y1,z1) -> [id:int] | Obté tipus de blocs entre les coordenades     |
| Minecraft.setBlock(x,y,z,id,[data])                | Posa un bloc a les coordenades                |
| Minecraft.setBlocks(x0,y0,z0,x1,y1,z1,id,[data])   | Posa un cuboid de blocs entre les coordenades |
| Minecraft.getHeight(x,z) -> y:int                  | Obté l'alçada vertical a les coordenades      |
| Minecraft.getPlayerEntityIds() -> [id:int]         | Obté els identificadors dels jugadors         |
| Minecraft.postToChat(missatge)                     | Imprimeix un missatge al xat del joc          |
| Minecraft.player.getPos() -> [x,y,x]               | Obté les coordenades del jugador              |
| Minecraft.player.setPos(x,y,z)                     | Tele-transporta el jugador a les coordenades   |
| Minecraft.player.getTilePos() -> [x,y,x]           | Obté les coordenades del terra del jugador    |
| Minecraft.player.setTilePos(x,y,z)                 | Tele-transporta el jugador a les coordenades   |
| Minecraft.entity.getPos(entityId) -> [x,y,x]       | Obté les coordenades de l' entitat            |
| Minecraft.entity.setPos(entityId,x,y,z)            | Tele-transporta l'entitat a les coordenades    |
| Minecraft.entity.getTilePos(entityId) -> [x,y,x]   | Obté les coordenades del terra de l'entitat   |
| Minecraft.entity.setTilePos(entityId,x,y,z)        | Tele-transporta l'entitat a les coordenades    |
| Minecraft.events.clearAll()                        | Esborra la cua d'esdeveniments                |
| Minecraft.events.pollBlockHits() -> [BlockEvent]   | Obté la llista d'accions sobre blocs          |

---

## API: BLOCS

| BLOC                  | COMANDA / ID     | SUBTIPUS DEL BLOC                     |
| --------------------- | ---------------- | ------------------------------------- | 
| AIR                   | block.Block(0)   |                                       |
| STONE                 | block.Block(1)   |                                       |
| GRASS                 | block.Block(2)   |                                       |
| DIRT                  | block.Block(3)   |                                       |
| COBBLESTONE           | block.Block(4)   |                                       |
| WOOD_PLANKS           | block.Block(5)   | 0:Oak 1:Spruce 2:Birch 3:Jungle       |
| SAPLING               | block.Block(6)   | 0:Oak 1:Spruce 2:Birch 3:Jungle       |
| BEDROCK               | block.Block(7)   |                                       |
| WATER , WATER_FLOWING | block.Block(8)   |                                       |
| WATER_STATIONARY      | block.Block(9)   | 0-7:Level   0:highest ... 7:lowest    |
| LAVA , LAVA_FLOWING   | block.Block(10)  |                                       |
| LAVA_STATIONARY       | block.Block(11)  | 0-7:Level   0:highest ... 7:lowest    |
| SAND                  | block.Block(12)  |                                       |
| GRAVEL                | block.Block(13)  |                                       |
| GOLD_ORE              | block.Block(14)  |                                       |
| IRON_ORE              | block.Block(15)  |                                       |
| COAL_ORE              | block.Block(16)  |                                       |
| WOOD                  | block.Block(17)  | 0-15:Tipus de fusta                   |
| LEAVES                | block.Block(18)  | 1:Oak 2:Spruce 3:Birch                |
| GLASS                 | block.Block(20)  |                                       |
| LAPIS_LAZULI_ORE      | block.Block(21)  |                                       |
| LAPIS_LAZULI_BLOCK    | block.Block(22)  |                                       |
| SANDSTONE             | block.Block(24)  | 0:Sandstone 1:Chiseled 2:Smooth       |
| BED                   | block.Block(26)  |                                       |
| COBWEB                | block.Block(30)  |                                       |
| GRASS_TALL            | block.Block(31)  | 0:Shrub 1:Grass 2:Fern 3:BiomeColor   |
| WOOL                  | block.Block(35)  | 0-15:Color                            |
| FLOWER_YELLOW         | block.Block(37)  |                                       |
| FLOWER_CYAN           | block.Block(38)  |                                       |
| MUSHROOM_BROWN        | block.Block(39)  |                                       |
| MUSHROOM_RED          | block.Block(40)  |                                       |
| GOLD_BLOCK            | block.Block(41)  |                                       |
| IRON_BLOCK            | block.Block(42)  |                                       |
| STONE_SLAB_DOUBLE     | block.Block(43)  | 0-7:Tipus de pedra                              |
| STONE_SLAB            | block.Block(44)  | 0-7:Tipus de pedra                    |
| BRICK_BLOCK           | block.Block(45)  |                                       |
| TNT                   | block.Block(46)  | 0:Inactive 1:Ready_to_explode         |
| BOOKSHELF             | block.Block(47)  |                                       |
| MOSS_STONE            | block.Block(48)  |                                       |
| OBSIDIAN              | block.Block(49)  |                                       |
| TORCH                 | block.Block(50)  | 1:East 2:West 3:South 4:North 5:Up    |
| FIRE                  | block.Block(51)  |                                       |
| STAIRS_WOOD           | block.Block(53)  | 0:East 1:West 2:South 3:North         |
| CHEST                 | block.Block(54)  | 2:North 3:South 4:West 5:East         |
| DIAMOND_ORE           | block.Block(56)  |                                       |
| DIAMOND_BLOCK         | block.Block(57)  |                                       |
| CRAFTING_TABLE        | block.Block(58)  |                                       |
| FARMLAND              | block.Block(60)  |                                       |
| FURNACE_INACTIVE      | block.Block(61)  | 2:North 3:South 4:West 5:East         |
| FURNACE_ACTIVE        | block.Block(62)  | 2:North 3:South 4:West 5:East         |
| DOOR_WOOD             | block.Block(64)  |                                       |
| LADDER                | block.Block(65)  | 2:North 3:South 4:West 5:East         |
| STAIRS_COBBLESTONE    | block.Block(67)  | 0:East 1:West 2:South 3:North         |
| DOOR_IRON             | block.Block(71)  |                                       |
| REDSTONE_ORE          | block.Block(73)  |                                       |
| SNOW                  | block.Block(78)  |                                       |
| ICE                   | block.Block(79)  |                                       |
| SNOW_BLOCK            | block.Block(80)  | 0-7:Height   0:lowest ... 7:highest   |
| CACTUS                | block.Block(81)  |                                       |
| CLAY                  | block.Block(82)  |                                       |
| SUGAR_CANE            | block.Block(83)  |                                       |
| FENCE                 | block.Block(85)  |                                       |
| GLOWSTONE_BLOCK       | block.Block(89)  |                                       |
| BEDROCK_INVISIBLE     | block.Block(95)  |                                       |
| STONE_BRICK           | block.Block(98)  | 0:Normal 1:Mossy 2:Cracked 3:Chiseled |
| GLASS_PANE            | block.Block(102) |                                       |
| MELON                 | block.Block(103) |                                       |
| FENCE_GATE            | block.Block(107) | 2:North 3:South 4:West 5:East         |
| GLOWING_OBSIDIAN      | block.Block(246) |                                       |
| NETHER_REACTOR_CORE   | block.Block(247) | 0:Unused 1:Active 2:Stopped/Used      |

---

## TECLAT

![](https://gamepedia.cursecdn.com/minecraft_gamepedia/2/2e/Kbd-minecraft.svg)

| TECLA           | ACCIÓ                     |
| --------------- | ------------------------- |
| A               | gira esquerra             |
| D               | gira dreta                |
| S               | camina enrere             |
| W               | camina endavant           |
| espai           | salta , neda , vola       |
| ctrl esquerra   | corre                     |
| maj. esquerra   | ajupeix                   |
| ratolí esquerra | golpeja                   |
| ratolí dreta    | usar , posar              |
| E               | inventari                 |
| Q               | deixa ítem de mà dreta    |
| 1–9 	          | selecciona ítem           |
| F 	          | intercanvia ítems de mans |

---

## EXEMPLES

```python
from mcpi.minecraft import Minecraft
from mcpi import block
from time import sleep

# inicialitza
mc = Minecraft.create()

# Diu alguna cosa
mc.postToChat('Hola mon!')

# Obté el tipus del bloc sota del personatge
x, y, z = mc.player.getPos()
mc.postToChat('El bloc sota teu és ' + str(mc.getBlock(x, y-1, z)))

# Obté les coordenades del personatge i teletransportal amunt
x, y, z = mc.player.getPos()
mc.postToChat('Teletransportat en un segon amunt a y=' + str(y+100))
sleep(1)
mc.player.setPos(x, y+100, z)

# Posa un bloc de aire sota el personatge i
# blocs de lava, aigua i pedra al voltant cada 3 segons
x, y, z = mc.player.getPos()
sleep(3)
mc.setBlock(x, y, z+3, block.LAVA.id)
mc.postToChat('Fuego es mi espiritu')
sleep(3)
mc.setBlock(x+3, y, z, block.WATER.id)
mc.postToChat('Agua es mi sangre')
sleep(3)
mc.setBlock(x-3, y, z, block.STONE.id)
mc.postToChat('Tierra es mi cuerpo')
sleep(3)
mc.setBlock(x, y-1, z, block.AIR.id)
mc.postToChat('Aire es mi aliento')

# Posa una torre de blocs d'explosius amb una iteració
mc.postToChat('Aquesta torre és la bomba')
i = 1
while i <= 100:
    mc.setBlock(x, y+i, z+5, block.TNT.id, 1)
    i = i + 1
    sleep(0.1)

# Posa una piscina (blocs de pedra amb aigua dintre)
mc.postToChat('En un segon estaràs a una piscina')
sleep(1)
mc.setBlocks(x-2, y, z-2, x+2, y-2, z+2, block.STONE.id)
mc.setBlocks(x-1, y, z-1, x+1, y-1, z+1, block.WATER.id)

# Fes una casa (blocs de fusta amb aire dintre i una porta)
# ...

# Posa una piràmide de diamants amb una iteració
mc.postToChat('Ara construeixo una piràmide')
h = 5
z = z + 2*h
i = 0
while i < h:
    mc.setBlocks(x-h+i, y+i, z-h+i, x+h-i, y+i, z+h-i, block.DIAMOND_BLOCK.id)
    i = i + 1
    sleep(0.1)

# Dibuixa una corona al cel
from math import sin, cos, pi
mc.postToChat('Ara dibuixo una corona de colors al cel')
a = 0
R = 100
h = 20
b = 5
i = 0.01
color = 0
x, y, z = mc.player.getPos()
while a < 2*pi:
    mc.setBlock(x + R*cos(a), y + 50 + h*cos(a*b), z + R*sin(a), block.WOOL.id, color)
    a = a + i
    color = (color + 1) % 16

# Quan el personatge camina, fes créixer flors a l'herba trepitjada
while True:
    x, y, z = mc.player.getPos()
    if mc.getBlock(x, y-1, z) == block.GRASS.id:
        mc.setBlock(x, y, z, block.FLOWER_CYAN.id)
    sleep(0.1)
```
