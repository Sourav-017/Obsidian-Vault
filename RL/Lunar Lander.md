
1. Observation space
	`Observation Space Shape = (8,)
	- Horizontal pad coordinate (x)
	- Vertical pad coordinate (y)
	- Horizontal speed (x)
	- Vertical speed (y)
	- Angle
	- Angular speed
	- If the left leg contact point has touched the land (boolean)
	- If the right leg contact point has touched the land (boolean)
2. Action Space:
	The action space (the set of possible actions the agent can take) is discrete with 4 actions available 🎮:

	- Action 0: Do nothing,
	- Action 1: Fire left orientation engine,
	- Action 2: Fire the main engine,
	- Action 3: Fire right orientation engine.
3. **Reward:**
	Reward function (the function that will give a reward at each timestep) 💰:
	
	After every step a reward is granted. The total reward of an episode is the **sum of the rewards for all the steps within that episode**.
	
	For each step, the reward:
	
	- Is increased/decreased the closer/further the lander is to the landing pad.
	- Is increased/decreased the slower/faster the lander is moving.
	- Is decreased the more the lander is tilted (angle not horizontal).
	- Is increased by 10 points for each leg that is in contact with the ground.
	- Is decreased by 0.03 points each frame a side engine is firing.
	- Is decreased by 0.3 points each frame the main engine is firing.
	
	The episode receive an **additional reward of -100 or +100 points for crashing or landing safely respectively.**
4. 