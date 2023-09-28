# Conversational Design Fundamentals

### Why is CCAI Needed
* Traditional interactive voice response (IVR) systems can't provide the quality experiences customers expect today
    * Expense and complex
    * Require IVR experts
* Most of all, they often fail to serve the end customer, which means they fail to serve your purpose

### From the business perspective
* Businesses have had to make a tradeoff between great customer service and operational efficiency
* Concerns include:
    * High cost of quality agents
    * Customer and agent churn
    * Agents answer same basic questions repeatedly

### From the customer perspective
* Complaints may include
    * Long wait/hold times
    * Unlimited call transfers
    * IVR difficult to navigate
    * Right resources aren't availale
    * Inadequate information

### Ideal Experience
* For the customer
    * Available 24/7
    * No wait
    * Needs met on first contact
* For the business
    * Resolutions w/o human
    * Efficiency when human needed
    * Lower onboarding costs

### What is CCAI
* A solution that provides the ability to augment and improve the contact center without the need for deep AI expertise

### What does CCAI do
* Captures what customer said
    * Speech-To-Text (STT)
* Understands
    * Natural Language Understanding (NLU)
* Talks
    * Text-To-Speech (TTS)
* Personalizes your brand or region
    * Voice generation
* Combines with other best-in-class technology
    * One-click integration with top telephony providers

### Three Pillars of CCAI
* Dialogflow
    * Virtual Agent and NLU for Chat and Voice
* Agent Assist
    * Live call transcription
    * Doc suggestions
    * Agent assistive AI
* Insights
    * Call search, scoring, and sentiment analysis
    * Topic extraction
    * For PM, team leads, and QA

### What is Dialogflow
* A natural language understanding (NLU) platform and development suite for intelligent and sophisticated conversational user interfaces
* The part of CCAI that handles the conversation
* Part conversational core and part virtual agent

### The Core of CCAI
* Captures
    * Speech-To-Text
* Understands
    * Natural Language Understanding
* Talks
    * Text-to-Speech

### Agent Assist
* Continous support
    * Provides the context necessary for a seamless transition, then stays active in the conversation behind the scenes
* Real-time assistance
    * Delivers information, workflows, and turn by turn guidance to agents, in real time, ensuring a consistent experience
* Knowledge feedback
    * Lets agents provide feedback on article relevance, which helps improve your models

### Defining a conversational experience
* Any voice or chat interface that relies on NLU for interacting with users

### Challenges to building conversational interfaces
* NLU is not easy
    * Few companies have the expertise to do NLU well
* Maximizing reach takes effort
    * Building support for multiple languages, platforms, devices, and apps is complex
* Enterprise integration is critical
    * Integration with backend services requires open, flexible infrastructure
* Don't over scope
    * Is this a strong use case? What can the virtual agent do well?
* Human escalation protocol is necessary
    * Few virtual agents have an escalation workflow that enables a human to take over when it can't help

### Natural language processing (NLP) terminology
* Utterance
    * Anything said in a conversation
    * Both users and bots make utterances
* Intent
    * Something a user is trying to do or express
        * Ex: Schedule an appointment
* Entity
    * A piece of information to extract from a natural language utterance

### NLP capabilities
* Syntax analysis
    * Allows you to extract tokens and sentences, identify parts of speech, and create depencency parse trees for each sentence
* Entity recognition
    * Enables your virtual agent to identify entities and label by types such as a person, organization, location, events, and media
* Sentiment analysis
    * Gives a measurement of a user's emotional state
    * Values are between -1.0 and +1.0
    * Ex: A score of -0.9 means the user is a little perturbed
    * Can be used as a decision point for bringing in a live agent
* Built-in text-to-speech
    * Dialogflow uses WaveNet technology to deliver natural, precise speech responses
        * Closes audio-quality gap with human speech by 70%
        * Useful for telephony and IoT applications
        * Configuration is different from Google Assistant


### Principles of conversational design methodology
* Use real end-user input
* Integrate business and user needs
* Be thorough in design stage
* Keep designers close to the user
* Address all contextual scenarios for reprompts
    * Persona (branding)
    * Application need (rejects/reprompts)
    * User fillers (language not supported by grammar)
    * Language use (lead with prompts)
    * Discourse (resolicit after discourse)

### Principles of design decisions
* Minimize cognitive load
* Accommodate conversational expectations
* Maximize efficiency
* Maximize clarity
* Ensure high accuracy
* Gracefully recover from errors

### Conversation best practices
* Use good conversational design principles
* Design for audio, not just visual
* Always ask follow-up questions
* Use a clear welcome intent
* Create a persona for your agent


### Use of SSML for enhancing the conversation
* By using Speech Synthesis Markup Language, you can make your conversation responses seem more like natural speech
    * Pronunciations
    * Breaks/Pauses
    * Pitch
    * Audio
* Leverage SSML for things like:
    * Distinguishing spelling
    * Specifying how a number should be read

