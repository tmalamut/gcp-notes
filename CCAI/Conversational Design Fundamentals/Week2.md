# Conversational Design Fundamentals

### Designing the virtual agent
* Identify user roles and use cases
* Write personas
* Model user-agent interactions
* Handle various user scenarios
* Use Dialogflow tools to test

### Pieces of the conversation
* Intents
* Entities
* Parameters

### What are intents?
* Intents are the actions your users want to execute
* Intents represent something a user might ask for

### Intents help the agent determine what's needed
* 2 mocha coffees please
    * Intent: Order coffee
* Upgrade me
    * Intent: Change tier

### Built-in intents
* Welcome intent
    * Hi
* Fallback intent
    * Sorry, I didn't understand
* Follow-up intent
    * Ok, checking or savings?

### What are entities?
* Help you get to the specifcs of the interaction: Who, What, When, Where

### Built-in entities
* My first name is Noyomi
    * @sys.given-name > "Noyomi"
* Which Pop song is the most popular?
    * @sys.music-genre > "Pop"
* My phone number is 4155551212
    * @sys.phone-number > "4155551212"

### Custom entities
* What songs are in Pop Favorites?
    * Playlist > "Pop Favorites"
* Upgrade me to the best service level
    * Tier > "Best" = Platinum
* My pin is 1234
    * Pin > "1234"

### Fulfillment and responses
* Static response messages
* Webhook calls for dynamic responses and/or to take actions
* Parameter presets to set or override parameter values
* In the event of multiple fulfillments, Dialogflow maintains the responses in a queue, sends the ordered responses to the end-user

### Actions and parameters
* How the virtual agent captures key parts of the conversation
* Set values for parameters from the user
* Prompt for parameter value if not already mentioned in the utterance

### Responses to intents
* What to tell the user when Dialogflow matches this intent
* Can be personalized by referencing parameters
















