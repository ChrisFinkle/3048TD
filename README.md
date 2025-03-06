# 3048TD

INITIAL DEVELOPMENT DESCRIPTION

On a turn, players can swap the contents of any two adjacent squares in a 7x5 grid. Each square in the grid is always occupied by a resource. 

Random resources spawn at the top of the playing field whenever there is an empty square, and move down when squares below them are vacated. Only the basic resources (trees, crystals, treasures, cannonballs, bricks) can spawn.

If a vertical or horizontal line of three or more identical resources is formed, the resources merge into the next tier up along that resource chain - trees become crossbows, cannonballs become cannons, treasure becomes treasure chests, ice crystals become ice walls, and bricks become towers. The merged resource unit is located in the square previously occupied by the resource which was swapped in to create the line. The other squares in the line are vacated, and resources fall down to fill the gaps as in a conventional match-3 game.

Crossbows shoot arrows straight down their column. Cannons shoot cannonballs all the way across their row. Treasure chests can be opened at will during game days and contain extra moves (more swaps the player can make before the level ends). Ice crystals slow down any dragons that fly over them. Towers shoot short-range arrows at all adjacent squares.

Each of these units starts at a base rank. If you then manage to merge three base units, they become a Bronze unit which shoots twice as fast, and likewise three Bronzes become a Silver unit which is 4x as fast as the base level, and so on for three Silvers becoming Gold (the highest tier).  Treasure chests advance even faster - a base chest contains 2 moves, bronze 10, silver 50, and gold 250. More advanced ice walls slow dragons down to 1/4 speed, 1/8th speed, etc.

Gameplay is divided into days and nights. Each time a new day starts, the player receives seven moves, which can be augmented by opening treasure chests or making especially good swap combos (ones that match 4 or more tiles at once, or chain multiple matches together in a chain reaction). Once all a day's moves are exhausted, night comes and a swarm of tiny dragons flies up from the bottom of the screen. The columns these dragons fly along are randomized each night, and the number of dragons increases each night, requiring ever more robust defenses. 

Dragons have two hit points. A cannonball or crossbow bolt does two damage. An arrow from a tower does one damage. If a dragon makes it through the attacks and hits the top castle wall, the castle loses half a heart of health.

Swapping a brick resource tile "into" the castle at the top of the screen restores or adds one heart of health, up to a total of 15 hearts.

draggy-towers-roguelite/
├── assets/
│   ├── images/
│   │   ├── resources/          # Base resources (trees, crystals, etc.)
│   │   ├── units/              # Combat units (crossbows, cannons, etc.)
│   │   │   ├── base/
│   │   │   ├── bronze/
│   │   │   ├── silver/
│   │   │   └── gold/
│   │   ├── enemies/            # Dragons and future enemy types
│   │   ├── effects/            # Visual effects (projectiles, explosions)
│   │   ├── ui/                 # UI elements
│   │   └── background/         # Background elements
│   ├── audio/
│   │   ├── music/
│   │   └── sfx/
│   └── fonts/
├── src/
│   ├── config/
│   │   ├── game-config.js      # Phaser configuration
│   │   └── resource-config.js  # Resource definitions and upgrade paths
│   ├── scenes/
│   │   ├── boot-scene.js
│   │   ├── preload-scene.js
│   │   ├── menu-scene.js
│   │   ├── game-scene.js       # Main gameplay
│   │   ├── night-scene.js      # Night battle phase
│   │   ├── day-scene.js        # Day building phase
│   │   └── meta-progression-scene.js
│   ├── entities/
│   │   ├── grid.js             # The game grid manager
│   │   ├── cell.js             # Individual grid cells
│   │   ├── resource.js         # Base resource class
│   │   ├── resources/          # Specific resource types
│   │   │   ├── tree.js
│   │   │   ├── crystal.js
│   │   │   ├── treasure.js
│   │   │   ├── cannonball.js
│   │   │   └── brick.js
│   │   ├── unit.js             # Base unit class
│   │   ├── units/              # Combat units
│   │   │   ├── crossbow.js
│   │   │   ├── cannon.js
│   │   │   ├── treasure-chest.js
│   │   │   ├── ice-wall.js
│   │   │   └── tower.js
│   │   ├── enemy.js            # Base enemy class
│   │   ├── enemies/            # Enemy types
│   │   │   └── dragon.js
│   │   ├── projectile.js       # Base projectile class
│   │   └── projectiles/        # Projectile types
│   │       ├── arrow.js
│   │       └── cannonball.js
│   ├── managers/
│   │   ├── input-manager.js    # Handle player inputs
│   │   ├── spawn-manager.js    # Handle resource spawning
│   │   ├── merge-manager.js    # Handle matching and merging
│   │   ├── wave-manager.js     # Handle enemy waves
│   │   ├── combat-manager.js   # Handle combat calculations
│   │   ├── day-night-manager.js # Handle day/night cycle
│   │   ├── move-manager.js     # Handle player moves and limits
│   │   └── progression-manager.js # Handle meta-progression
│   ├── systems/
│   │   ├── upgrade-system.js   # Resource upgrade paths
│   │   ├── meta-system.js      # Meta-progression unlocks
│   │   ├── save-system.js      # Game saving/loading
│   │   └── achievement-system.js
│   ├── ui/
│   │   ├── hud.js              # Heads-up display
│   │   ├── day-night-indicator.js
│   │   ├── move-counter.js
│   │   ├── health-display.js
│   │   └── menu.js             # Game menus
│   ├── utils/
│   │   ├── math-utils.js       # Math helper functions
│   │   ├── animation-utils.js  # Animation helpers
│   │   ├── grid-utils.js       # Grid manipulation helpers
│   │   └── sound-utils.js      # Sound helpers
│   └── main.js                 # Entry point
├── index.html
├── package.json
├── webpack.config.js
└── README.md
