# Server API // via POST, as JSON

* /login
	* Input:
		* username (string)
		* lat (float)
		* long (float)
	* Output:
		* success (bool)
		* username (string)
		* token (string)
		* wins (int)
		* losses (int)
	
* /fire
	* Input:
		* token (string)
		* angle (float)
		* power (float)
	* Output:
		* success (bool)
		* hp (int) // HP left of enemy
		* lat (float) // Where did the projectile land
		* long (float)
		
* /get-updates // Because PHP cannot do long polling and it''s too late for nodejs.
	* Input
		* token (string)
	* Output
		* updates (array)
			* action
			* data
		
# Server-to-Client API // via Apple Push Notification Service

* found-match // Server has found a match for you
	* username (string)
	* lat (float)
	* long (float)
	* your-turn (bool) // True if it is your turn
	
* hit // opponent has fired
	* lat (float)
	* long (float)
	* hp (float) // Your HP left

* match-ended // Match has been forcefully ended.