Project contains:

AI:
BP_Enemy - Main enemy character object
BP_AI_Controller - Main enemy controller
ESQ_GetPlayerLocation - Uses Environmental Query System to get closest available point to the player
ESQ_PlayerVisible - Checks if a player is visible
EQC_PlayerContext - Produces a player pawn specific context for ESQ
BTT_Patrol - Patrol task for the enemy to do during patrols (Using Target Points within an array inside the enemy character pawn)
BT_Enemy - Main enemy behaviour tree
BB_Enemy - Main enemy blackboard
Attack_PrimaryA - Visual animation for when the enemy "attacks" the player (all conditions met for attack to occur)

Everything else is a combination of the First and Thirdperson example projects to get access to the mannequin and its animations.

AI will:
Patrol around its patrol targets (failing to do patrol if there are no targets in its list).

1) If seeing player will begin to chase after the player.

2) If reaches player point - Will get as close as it can and begin attacking.

3) If reaches player point but player has moved out of sight - returns to patrol 
(there's no cooldown or "search area" for now, it wouldn't be difficult to implement,
have done it before (See FPS Assignment with Bart, though that didn't use ESQ and was probably far inferior to this). Just didn't feel like it this time).

4) If reaches player point and can see player at different position - Repeats from step 1.

Patrol -> Chase -> Attack

AI uses: 
AI Perception to see player initialy (forcing players to be infront of the AI for them to notice the first time).
ESQ to get point of the player when noticed.
ESQ to check if player is still within AI "Sight" meaning you can't just move behind it to get away, you have to get behind some solid objects like a wall.
NavMesh to move.
Behaviour tree to maintain "states" and logic within those states.
Blackboard for all the data needed to be used in the Behaviour tree.