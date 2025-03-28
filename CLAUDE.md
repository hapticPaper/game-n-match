# Poker Game Matching Algorithm Experimentation Framework

**Inspiration:**
We were having an academic conversation about matching algos. we were using a poker game between friends in a js ui as the frame for the discussion. 
We talked about things like what actually matters, like ELO, vs just letting a user say they dont want to play with someone, to gamemodes and options like 'with friends' 'with strangers' etc. 
We also talked about the difficulty of saying one approach is actually better than another - metrics and measurement, reward etc. i also mentioned things like determining what skill level to make bots when theyre needed to fill tables because there arent enough players in the queue to make a whole table.

We want to experiment with some parts of it. 


**Purpose:**

This project aims to create a flexible and scalable framework for experimenting with various matching algorithms in a poker game context. The framework should allow for:

* **Simulation:** Running large-scale simulations of poker games with various matching algorithms.
* **Analysis:** Visualizing and analyzing the results of these simulations.
* **Interactive UI:** Providing a user interface for both playing the game and controlling simulations.
* **Agent (Bot) Implementation:** Creating and testing different bot strategies and skill levels.
* **Modular Design:** Enabling easy swapping and modification of matching algorithms and game parameters.

**Key Requirements:**

* **Decoupled Architecture:** The backend (game logic, matching algorithms, simulations) must be separated from the frontend (UI).
* **Python Backend:** The backend should be implemented in Python.
* **JavaScript Frontend:** The frontend should be implemented using a modern JavaScript framework (React, Vue.js, or Svelte).
* **Flexible Matching Algorithms:** The framework must support a range of matching algorithms, from simple (random) to complex (ELO-based, preference-based).
* **Scalable Simulations:** The system must be capable of running simulations with a large number of players and games.
* **Interactive Data Visualization:** The results of the simulations must be visualized in an interactive and informative way.
* **Agent/Bot Variability:** The system must allow for different agent skill levels and strategies.
* **Configuration Driven:** The system must use configuration files to allow for easy adjustments to game parameters and matching algorithms.

**Project Structure:**

poker_sim/
├── backend/
│   ├── api.py (Flask/FastAPI REST API)
│   ├── game/
│   │   ├── game_engine.py (Core game logic)
│   │   ├── player.py (Player class)
│   │   ├── deck.py (Deck class)
│   │   ├── hand.py (Hand class)
│   │   ├── table.py (Table class)
│   │   ├── ... (Other game-related classes)
│   ├── matching/
│   │   ├── matcher.py (AbstractMatcher class)
│   │   ├── elo_matcher.py (ELO-based matching)
│   │   ├── preference_matcher.py (Preference-based matching)
│   │   ├── random_matcher.py (Random matching)
│   │   ├── ... (Other matching algorithms)
│   ├── agents/
│   │   ├── agent.py (AbstractAgent class)
│   │   ├── random_agent.py (Random agent strategy)
│   │   ├── rule_based_agent.py (Rule-based agent strategy)
│   │   ├── ml_agent.py (Machine learning agent strategy)
│   │   ├── ... (Other agent strategies)
│   ├── config.yaml (Game configuration)
│   ├── database.py (Database interactions)
├── frontend/
│   ├── src/
│   │   ├── App.js (Main UI component)
│   │   ├── Game.js (Game UI component)
│   │   ├── Queue.js (Queue UI component)
│   │   ├── ... (Other UI components)
│   ├── public/
│   ├── package.json
├── notebooks/
│   ├── simulation_analysis.ipynb (Jupyter notebook for analysis)
├── gradio_ui/
│   ├── gradio_app.py (Gradio UI for simulations)
├── dash_ui/
│   ├── dash_app.py (Dash web app for simulation control and visualization)
├── README.md


**Detailed Component Breakdown:**

* **Backend (Python):**
    * **API (api.py):**
        * Use Flask or FastAPI to create a REST API for communication with the frontend.
        * Endpoints:
            * `/join_queue`: Add a player to the queue.
            * `/game_state`: Retrieve the current game state.
            * `/player_action`: Submit a player's action.
            * `/start_simulation`: Start a simulation with specified parameters.
            * `/stop_simulation`: Stop a running simulation.
            * `/simulation_results`: Retrieve simulation results.
    * **Game Logic (game/):**
        * Implement the core poker game logic using object-oriented design.
        * Classes: `Player`, `Deck`, `Hand`, `Table`, `GameEngine`.
        * `GameEngine` should be able to run games independently of the UI.
    * **Matching Algorithms (matching/):**
        * Implement an `AbstractMatcher` class with a `match(queue, game_options)` method.
        * Implement specific matching algorithms as subclasses (e.g., `EloMatcher`, `PreferenceMatcher`, `RandomMatcher`).
        * The system must be able to change the used matching algorithm through the config file.
    * **Agents (agents/):**
        * Implement an `AbstractAgent` class with a `make_move(game_state)` method.
        * Implement various agent strategies as subclasses (e.g., `RandomAgent`, `RuleBasedAgent`, `MLAgent`).
        * Agents should have a skill level parameter.
    * **Configuration (config.yaml):**
        * Use YAML to store game parameters, matching algorithm settings, and other configuration options.
    * **Database (database.py):**
        * Use SQLite or PostgreSQL to store game results, player statistics, and simulation data.

* **Frontend (JavaScript):**
    * Use React, Vue.js, or Svelte to create an interactive UI.
    * Components:
        * `App`: Main application component.
        * `Game`: Game UI component for displaying the poker game.
        * `Queue`: UI component for joining and viewing the player queue.
        * Use WebSockets for real-time communication with the backend.

* **Notebooks (notebooks/):**
    * Use Jupyter notebooks for interactive data analysis and visualization.
    * Analyze simulation results, generate plots, and explore different matching algorithm parameters.
    * Use Pandas, Matplotlib, Seaborn, and Plotly.

* **Gradio UI (gradio_ui/):**
    * Use Gradio to create simple UIs for running simulations.
    * Allow users to adjust simulation parameters and view results.
    * Value: quick iterative testing, and simple parameter adjustment.

* **Dash UI (dash_ui/):**
    * Use Dash to create interactive web-based dashboards for controlling simulations and visualizing results.
    * Provide real-time feedback and allow users to explore data in detail.
    * Value: Detailed interactive results, and real time simulation control.

**LLM Instructions:**

1.  Follow the project structure and component breakdown.
2.  Prioritize modularity and flexibility.
3.  Use clear and concise code with appropriate comments.
4.  Implement robust error handling and input validation.
5.  Create comprehensive documentation for each component.
6.  Ensure the system is scalable and performant.
7.  Create a functional config.yaml file that can change core parts of the simulation.
8.  Prioritize the creation of the Dash application, as it provides the most value for interactive visualization and control.
9.  Consider using type hinting within the python backend.
10. Ensure the API is fully functional.