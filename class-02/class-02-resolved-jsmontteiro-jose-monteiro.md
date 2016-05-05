# MongoDB - Aula 02 - Exercício
autor: José Maria monteiro Junior

## Criando a database
use be-mean-pokemons

## Listagem das databases (passo 2)
```
show dbs
be-mean-pokemons  → 0.078GB
be-mean-instagram → 0.078GB
be-mean-teste     → 0.078GB
local             → 0.078GB
be-mean           → 0.078GB
```

## Listagem das coleções (passo 3)
```
show collections
pokemons       → 0.027MB / 0.039MB
system.indexes → 0.000MB / 0.008MB
```

## Cadastro dos pokemons (passo 4)

```
var pokemons = [{"name": "Bulbasaur", "description": "The seed on its back is filled with nutrients. The seed grows steadily larger as its body grows.", "type": "poison/grass", "attack": 49, "height": 7, "defense": 49},
{"name": "Ivysaur", "description": "The bulb on its back grows as it absorbs nutrients. The bulb gives off a pleasant aroma when it blooms.", "type": "poison/grass", "attack": 62, "height": 10, "defense": 63},
{"name": "Venusaur", "description": "It is able to con vert sunlight into energy. As a result, it is more powerful in the summertime.", "type": "poison/grass", "attack": 82, "height": 20, "defense": 83},
{"name": "Charmander", "description": "Obviously prefers hot places. When it rains, steam is said to spout from the tip of its tail.", "type": "fire", "attack": 52, "height": 6, "defense": 43},
{"name": "Charmeleon", "description": "When it swings its burning tail, it elevates the temperature to unbearably high levels.", "type": "fire", "attack": 64, "height": 11, "defense": 58},
{"name": "Charizard", "description": "Spits fire that is hot enough to melt boulders. Known to cause forest fires unintentionally.", "type": "flying/fire", "attack": 84, "height": 17, "defense": 78},
{"name": "Squirtle", "description": "After birth, its back swells and hardens into a shell. Powerfully sprays foam from its mouth.", "type": "water", "attack": 48, "height": 5, "defense": 65},
{"name": "Wartortle", "description": "Its large tail is covered with rich, thick fur that deepens in color with age. The scratches on its shell are evidence of this POKMONs toughness in battle.", "type": "water", "attack": 63, "height": 10, "defense": 80},
{"name": "Blastoise", "description": "A brutal POKMON with pressurized water jets on its shell. They are used for high speed tackles.", "type": "water", "attack": 83, "height": 16, "defense": 100},
{"name": "Caterpie", "description": "For protection, it releases a horrible stench from the antennae on its head to drive away enemies.", "type": "bug", "attack": 30, "height": 3, "defense": 35},
{"name": "Metapod", "description": "This is its pre- evolved form. At this stage, it can only harden, so it remains motionless to avoid attack.", "type": "bug", "attack": 20, "height": 7, "defense": 55},
{"name": "Butterfree", "description": "In battle, it flaps its wings at high speed to release highly toxic dust into the air.", "type": "flying/bug", "attack": 45, "height": 11, "defense": 50},
{"name": "Weedle", "description": "Often found in forests and grasslands. It has a sharp, toxic barb of around two inches on top of its head.", "type": "poison/bug", "attack": 35, "height": 3, "defense": 30},
{"name": "Kakuna", "description": "Almost incapable of moving, this POKMON can only harden its shell to protect itself from predators.", "type": "poison/bug", "attack": 25, "height": 6, "defense": 50},
{"name": "Beedrill", "description": "It can take down any opponent with its powerful poi son stingers. It sometimes attacks in swarms.", "type": "poison/bug", "attack": 90, "height": 10, "defense": 40},
{"name": "Pidgey", "description": "It has an extremely sharp sense of direction. It can unerringly return home to its nest, however far it may be removed from its familiar surroundings.", "type": "normal/flying", "attack": 45, "height": 3, "defense": 40},
{"name": "Pidgeotto", "description": "PIDGEOTTO claims a large area as its own territory. This POKMON flies around, patrolling its living space. If its territory is violated, it shows no mercy in thoroughly punishing the foe with its sharp claws.", "type": "normal/flying", "attack": 60, "height": 11, "defense": 55},
{"name": "Pidgeot", "description": "PIDGEOTTO claims a large area as its own territory. This POKMON flies around, patrolling its living space. If its territory is violated, it shows no mercy in thoroughly punishing the foe with its sharp claws.", "type": "normal/flying", "attack": 80, "height": 15, "defense": 75},
{"name": "Rattata", "description": "It eats anything. Wherever food is available, it will settle down and produce offspring continuously.", "type": "normal", "attack": 56, "height": 3, "defense": 35},
{"name": "Raticate", "description": "The webs on its hind legs enable it to cross rivers. It search es wide areas for food.", "type": "normal", "attack": 81, "height": 7, "defense": 60},
{"name": "Spearow", "description": "Eats bugs in grassy areas. It has to flap its short wings at high speed to stay airborne.", "type": "normal/flying", "attack": 60, "height": 3, "defense": 30},
{"name": "Fearow", "description": "It has the stamina to fly all day on its broad wings. It fights by using its sharp beak.", "type": "normal/flying", "attack": 90, "height": 12, "defense": 65},
{"name": "Ekans", "description": "It flutters the tip of its tongue to seek out the scent of prey, then swallows the prey whole.", "type": "poison", "attack": 60, "height": 20, "defense": 44},
{"name": "Arbok", "description": "The frightening patterns on its belly have been studied. Six variations have been confirmed.", "type": "poison", "attack": 85, "height": 35, "defense": 69},
{"name": "Pikachu", "description": "It raises its tail to check its sur roundings. The tail is sometimes struck by light ning in this pose.", "type": "electric", "attack": 55, "height": 4, "defense": 40},
{"name": "Raichu", "description": "If the electric pouches in its cheeks become fully charged, both ears will stand straight up.", "type": "electric", "attack": 90, "height": 8, "defense": 55},
{"name": "Sandshrew", "description": "To protect itself from attackers, it curls up into a ball. It lives in arid regions with minimal rainfall.", "type": "ground", "attack": 75, "height": 6, "defense": 85},
{"name": "Sandslash", "description": "Adept at climbing trees, it rolls into a spiny ball, then attacks its enemies from above.", "type": "ground", "attack": 100, "height": 10, "defense": 110},
{"name": "Nidoran-f", "description": "Although small, its venomous barbs render this POKMON dangerous. The female has smaller horns.", "type": "poison", "attack": 47, "height": 4, "defense": 52},
{"name": "Nidorina", "description": "When NIDORINA are with their friends or family, they keep their barbs tucked away to prevent hurting each other. This POKMON appears to become nervous if separated from the others.", "type": "poison", "attack": 62, "height": 8, "defense": 67},
{"name": "Nidoqueen", "description": "Its hard scales provide strong protection. It uses its hefty bulk to execute powerful moves.", "type": "poison/ground", "attack": 92, "height": 13, "defense": 87},
{"name": "Nidoran-m", "description": "It is small, but its horn is filled with poison. It charges then stabs with the horn to inject poison.", "type": "poison", "attack": 57, "height": 5, "defense": 40},
{"name": "Nidorino", "description": "Quick to anger, it stabs enemies with its horn to inject a powerful poison when it becomes agitated.", "type": "poison", "attack": 72, "height": 9, "defense": 57},
{"name": "Nidoking", "description": "Its tail is thick and powerful. If it binds an enemy, it can snap the victim's spine quite easily.", "type": "poison/ground", "attack": 102, "height": 14, "defense": 77},
{"name": "Clefairy", "description": "Adored for their cute looks and playfulness. They are thought to be rare, as they do not appear often.", "type": "fairy", "attack": 45, "height": 6, "defense": 48},
{"name": "Clefable", "description": "With its acute hearing, it can pick up sounds from far away. It usually hides in quiet places.", "type": "fairy", "attack": 70, "height": 13, "defense": 73},
{"name": "Vulpix", "description": "If it is attacked by an enemy that is stronger than itself, it feigns injury to fool the enemy and escapes.", "type": "fire", "attack": 41, "height": 6, "defense": 40},
{"name": "Ninetales", "description": "Its nine tails are said to be imbued with a mystic power. It can live for a thousand years.", "type": "fire", "attack": 76, "height": 11, "defense": 75},
{"name": "Jigglypuff", "description": "When this POKMON sings, it never pauses to breathe. If it is in a battle against an opponent that does not easily fall asleep, JIGGLYPUFF cannot breathe, endangering its life.", "type": "normal/fairy", "attack": 45, "height": 5, "defense": 20},
{"name": "Wigglytuff", "description": "The body is soft and rubbery. When angered, it will suck in air and inflate itself to an enormous size.", "type": "normal/fairy", "attack": 70, "height": 10, "defense": 45},
{"name": "Zubat", "description": "ZUBAT avoids sunlight because exposure causes it to become unhealthy. During the daytime, it stays in caves or under the eaves of old houses, sleeping while hanging upside down.", "type": "flying/poison", "attack": 45, "height": 8, "defense": 35},
{"name": "Golbat", "description": "It can drink more than 10 ounces of blood at once. If it has too much, it gets heavy and flies clumsily.", "type": "flying/poison", "attack": 80, "height": 16, "defense": 70},
{"name": "Oddish", "description": "If exposed to moonlight, it starts to move. It roams far and wide at night to scatter its seeds.", "type": "poison/grass", "attack": 50, "height": 5, "defense": 55},
{"name": "Gloom", "description": "GLOOM releases a foul fragrance from the pistil of its flower. When faced with danger, the stench worsens. If this POKMON is feeling calm and secure, it does not release its usual stinky aroma.", "type": "poison/grass", "attack": 65, "height": 8, "defense": 70},
{"name": "Vileplume", "description": "The larger its petals, the more toxic pollen it contains. Its big head is heavy and hard to hold up.", "type": "poison/grass", "attack": 80, "height": 12, "defense": 85},
{"name": "Paras", "description": "PARAS has parasitic mushrooms growing on its back called tochukaso. They grow large by drawing nutrients from the BUG POKMON host. They are highly valued as a medicine for extending life.", "type": "bug/grass", "attack": 70, "height": 3, "defense": 55},
{"name": "Parasect", "description": "The larger the mushroom on its back grows, the stronger the mush room spores it scatters.", "type": "bug/grass", "attack": 95, "height": 10, "defense": 80},
{"name": "Venonat", "description": "Lives in the shadows of tall trees where it eats insects. It is attracted by light at night.", "type": "poison/bug", "attack": 55, "height": 10, "defense": 50},
{"name": "Venomoth", "description": "It flutters its wings to scatter dustlike scales. The scales leach toxins if they contact skin.", "type": "poison/bug", "attack": 65, "height": 15, "defense": 60},
{"name": "Diglett", "description": "If a DIGLETT DIGS through a field, it leaves the soil perfectly tilled and ideal for planting crops.", "type": "ground", "attack": 55, "height": 2, "defense": 25},
{"name": "Dugtrio", "description": "Its three heads move alternately, driving it through tough soil to depths of over 60 miles.", "type": "ground", "attack": 80, "height": 7, "defense": 50},
{"name": "Meowth", "description": "All it does is sleep during the daytime. At night, it patrols its territory with its eyes aglow.", "type": "normal", "attack": 45, "height": 4, "defense": 35},
{"name": "Persian", "description": "Many adore it for its sophisticated air. However, it will lash out and scratch for little reason.", "type": "normal", "attack": 70, "height": 10, "defense": 60},
{"name": "Psyduck", "description": "When headaches stimulate its brain cells, which are usually inactive, it can use a mysterious power.", "type": "water", "attack": 52, "height": 8, "defense": 48},
{"name": "Golduck", "description": "Often seen swim ming elegantly by lake shores. It is often mistaken for the Japanese monster, Kappa.", "type": "water", "attack": 82, "height": 17, "defense": 78},
{"name": "Mankey", "description": "Extremely quick to anger. It could be docile one moment then thrashing away the next instant.", "type": "fighting", "attack": 80, "height": 5, "defense": 35},
{"name": "Primeape", "description": "When it becomes furious, its blood circulation becomes more robust, and its muscles are made stronger. But it also becomes much less intelligent.", "type": "fighting", "attack": 105, "height": 10, "defense": 60},
{"name": "Growlithe", "description": "A POKMON with a friendly nature. However, it will bark fiercely at anything invading its territory.", "type": "fire", "attack": 70, "height": 7, "defense": 45},
{"name": "Arcanine", "description": "This legendary Chinese POKEMON is considered magnif icent. Many people are enchanted by its grand mane.", "type": "fire", "attack": 110, "height": 19, "defense": 80},
{"name": "Poliwag", "description": "It is possible to see this POKMONs spiral innards right through its thin skin. However, the skin is also very flexible. Even sharp fangs bounce right off it.", "type": "water", "attack": 50, "height": 6, "defense": 40},
{"name": "Poliwhirl", "description": "The surface of POLIWHIRLs body is always wet and slick with an oily fluid. Because of this greasy covering, it can easily slip and slide out of the clutches of any enemy in battle.", "type": "water", "attack": 65, "height": 10, "defense": 65},
{"name": "Poliwrath", "description": "An adept swimmer at both the front crawl and breast stroke. Easily overtakes the best human swimmers.", "type": "fighting/water", "attack": 95, "height": 13, "defense": 95},
{"name": "Abra", "description": "It hypnotizes itself so that it can teleport away when it senses danger, even if it is asleep.", "type": "psychic", "attack": 20, "height": 9, "defense": 15},
{"name": "Kadabra", "description": "It possesses strong spiritual power. The more danger it faces, the stronger its psychic power.", "type": "psychic", "attack": 35, "height": 13, "defense": 30},
{"name": "Alakazam", "description": "The spoons clutched in its hands are said to have been created by its psychic powers.", "type": "psychic", "attack": 50, "height": 15, "defense": 45},
{"name": "Machop", "description": "It loves to work out and build its muscles. It is never satisfied, even if it trains hard all day long.", "type": "fighting", "attack": 80, "height": 8, "defense": 50},
{"name": "Machoke", "description": "The belt around its waist holds back its energy. Without it, this POKMON would be unstoppable.", "type": "fighting", "attack": 100, "height": 15, "defense": 70},
{"name": "Machamp", "description": "One arm alone can move mountains. Using all four arms, this POKMON fires off awesome punches.", "type": "fighting", "attack": 130, "height": 16, "defense": 80},
{"name": "Bellsprout", "description": "Prefers hot and humid places. It ensnares tiny insects with its vines and devours them.", "type": "poison/grass", "attack": 75, "height": 7, "defense": 35},
{"name": "Weepinbell", "description": "The leafy parts act as cutters for slashing foes. It spits a fluid that dissolves everything.", "type": "poison/grass", "attack": 90, "height": 10, "defense": 50},
{"name": "Victreebel", "description": "Lures prey with the sweet aroma of honey. Swallowed whole, the prey is melted in a day, bones and all.", "type": "poison/grass", "attack": 105, "height": 17, "defense": 65},
{"name": "Tentacool", "description": "When the tide goes out, dehydrated TENTACOOL remains can be found washed up on the shore.", "type": "poison/water", "attack": 40, "height": 9, "defense": 35},
{"name": "Tentacruel", "description": "TENTACRUEL has large red orbs on its head. The orbs glow before lashing the vicinity with a harsh ultrasonic blast. This POKMONs outburst creates rough waves around it.", "type": "poison/water", "attack": 70, "height": 16, "defense": 65},
{"name": "Geodude", "description": "Most people may not notice, but a closer look should reveal that there are many GEODUDE around.", "type": "ground/rock", "attack": 80, "height": 4, "defense": 100},
{"name": "Graveler", "description": "It rolls on mountain paths to move. Once it builds momentum, no Pokmon can stop it without difficulty.", "type": "ground/rock", "attack": 95, "height": 10, "defense": 115},
{"name": "Golem", "description": "It is capable of blowing itself up. It uses this explosive force to jump from mountain to mountain.", "type": "ground/rock", "attack": 120, "height": 14, "defense": 130},
{"name": "Ponyta", "description": "It is a weak run ner immediately after birth. It gradually becomes faster by chasing after its parents.", "type": "fire", "attack": 85, "height": 10, "defense": 55},
{"name": "Rapidash", "description": "Just loves to run. If it sees some thing faster than itself, it will give chase at top speed.", "type": "fire", "attack": 100, "height": 17, "defense": 70},
{"name": "Slowpoke", "description": "A sweet sap leaks from its tail's tip. Although not nutritious, the tail is pleasant to chew on.", "type": "water/psychic", "attack": 65, "height": 12, "defense": 65},
{"name": "Slowbro", "description": "Naturally dull to begin with, it lost its ability to feel pain due to SHELLDERs seeping poison.", "type": "water/psychic", "attack": 75, "height": 16, "defense": 110},
{"name": "Magnemite", "description": "The units at its sides are extremely powerful magnets. They generate enough magnetism to draw in iron objects from over 300 feet away.", "type": "steel/electric", "attack": 35, "height": 3, "defense": 70},
{"name": "Magneton", "description": "Formed by several MAGNEMITEs linked together. They frequently appear when sunspots flare up.", "type": "steel/electric", "attack": 60, "height": 10, "defense": 95},
{"name": "Farfetchd", "description": "It is always seen with a stick from a plant. Apparently, there are good sticks and bad sticks. This POKMON occasionally fights with others over choice sticks.", "type": "normal/flying", "attack": 65, "height": 8, "defense": 55},
{"name": "Doduo", "description": "DODUOs two heads never sleep at the same time. Its two heads take turns sleeping, so one head can always keep watch for enemies while the other one sleeps.", "type": "normal/flying", "attack": 85, "height": 14, "defense": 45},
{"name": "Dodrio", "description": "Uses its three brains to execute complex plans. While two heads sleep, one head stays awake.", "type": "normal/flying", "attack": 110, "height": 18, "defense": 70},
{"name": "Seel", "description": "The protruding horn on its head is very hard. It is used for bashing through thick ice.", "type": "water", "attack": 45, "height": 11, "defense": 55},
{"name": "Dewgong", "description": "Stores thermal energy in its body. Swims at a steady 8 knots even in intensely cold waters.", "type": "water/ice", "attack": 70, "height": 17, "defense": 80},
{"name": "Grimer", "description": "Appears in filthy areas. Thrives by sucking up polluted sludge that is pumped out of factories.", "type": "poison", "attack": 80, "height": 9, "defense": 50},
{"name": "Muk", "description": "They love to gath er in smelly areas where sludge ac cumulates, making the stench around them worse.", "type": "poison", "attack": 105, "height": 12, "defense": 75},
{"name": "Shellder", "description": "It swims facing backward by open ing and closing its two-piece shell. It is surprisingly fast.", "type": "water", "attack": 65, "height": 3, "defense": 100},
{"name": "Cloyster", "description": "When attacked, it launches its horns in quick volleys. Its innards have never been seen.", "type": "water/ice", "attack": 95, "height": 15, "defense": 180},
{"name": "Gastly", "description": "This Pokmons body is 95% made up of gases, which are blown away by strong gusts of wind.", "type": "poison/ghost", "attack": 35, "height": 13, "defense": 30},
{"name": "Haunter", "description": "In total darkness, where nothing is visible, HAUNTER lurks, silently stalking its next victim.", "type": "poison/ghost", "attack": 50, "height": 16, "defense": 45},
{"name": "Gengar", "description": "The leer that floats in darkness belongs to a GENGAR delighting in casting curses on people.", "type": "poison/ghost", "attack": 65, "height": 15, "defense": 60},
{"name": "Onix", "description": "As it digs through the ground, it absorbs many hard objects. This is what makes its body so solid.", "type": "ground/rock", "attack": 45, "height": 88, "defense": 160},
{"name": "Drowzee", "description": "Puts enemies to sleep then eats their dreams. Occasionally gets sick from eating bad dreams.", "type": "psychic", "attack": 48, "height": 10, "defense": 45},
{"name": "Hypno", "description": "HYPNO holds a pendulum in its hand. The arcing movement and glitter of the pendulum lull the foe into a deep state of hypnosis. While this POKMON searches for prey, it polishes the pendulum.", "type": "psychic", "attack": 73, "height": 16, "defense": 70},
{"name": "Krabby", "description": "KRABBY live on beaches, burrowed inside holes dug into the sand. On sandy beaches with little in the way of food, these POKMON can be seen squabbling with each other over territory.", "type": "water", "attack": 105, "height": 4, "defense": 90},
{"name": "Kingler", "description": "It can hardly lift its massive, overgrown pincer. The pincer's size makes it difficult to aim properly.", "type": "water", "attack": 130, "height": 13, "defense": 115},
{"name": "Voltorb", "description": "It was discovered when POK BALLS were introduced. It is said that there is some connection.", "type": "electric", "attack": 30, "height": 5, "defense": 50}]

db.pokemons.save(pokemons)
```

## Lista dos pokemons (passo 5)
```
db.pokemons.find()
{
  "_id": ObjectId("5660887d6cd102947b0c1598"),
  "name": "Bulbasaur",
  "description": "The seed on its back is filled with nutrients. The seed grows steadily larger as its body grows.",
  "type": "poison/grass",
  "attack": 49,
  "height": 7,
  "defense": 49
}
{
  "_id": ObjectId("5660887d6cd102947b0c1599"),
  "name": "Ivysaur",
  "description": "The bulb on its back grows as it absorbs nutrients. The bulb gives off a pleasant aroma when it blooms.",
  "type": "poison/grass",
  "attack": 62,
  "height": 10,
  "defense": 63
}
{
  "_id": ObjectId("5660887d6cd102947b0c159a"),
  "name": "Venusaur",
  "description": "It is able to con vert sunlight into energy. As a result, it is more powerful in the summertime.",
  "type": "poison/grass",
  "attack": 82,
  "height": 20,
  "defense": 83
}
{
  "_id": ObjectId("5660887d6cd102947b0c159b"),
  "name": "Charmander",
  "description": "Obviously prefers hot places. When it rains, steam is said to spout from the tip of its tail.",
  "type": "fire",
  "attack": 52,
  "height": 6,
  "defense": 43
}
{
  "_id": ObjectId("5660887d6cd102947b0c159c"),
  "name": "Charmeleon",
  "description": "When it swings its burning tail, it elevates the temperature to unbearably high levels.",
  "type": "fire",
  "attack": 64,
  "height": 11,
  "defense": 58
}

```
...........


## Buscar Pokemon (passo 6)
```
var poke = db.pokemons.findOne({"name":"Charizard"})
poke
{
  "_id": ObjectId("5660887d6cd102947b0c159d"),
  "name": "Charizard",
  "description": "Spits fire that is hot enough to melt boulders. Known to cause forest fires unintentionally.",
  "type": "flying/fire",
  "attack": 84,
  "height": 17,
  "defense": 78
}
```

## Atualização do Pokemon (passo 7)
```
db.pokemons.update(poke,{$set:{"description":"A porra do pokemon mais foda de todos"}})
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

db.pokemons.findOne({"name":"Charizard"})
{
  "_id": ObjectId("5660887d6cd102947b0c159d"),
  "name": "Charizard",
  "description": "A porra do pokemon mais foda de todos",
  "type": "flying/fire",
  "attack": 84,
  "height": 17,
  "defense": 78
}
```






