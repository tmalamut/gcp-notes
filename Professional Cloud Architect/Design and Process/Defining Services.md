# Defining Services

### Requirements, Analysis, and Design
* Qualitative requirements define systems from the user's point of view
* Who
    * Are the users?
    * Are the developers?
    * Are the stakeholders?
* What
    * Does the system do?
    * Are the main features?
* Why
    * Is the system needed?
* When
    * Do the users need and/or want the solution?
    * Can the developers be done?
* How
    * Will the system work?
    * Many users will there be?
    * Much data will there be?
* Roles represent the goal of a user at some point
* Roles aren't people or job titles
    * People can play multiple roles
    * A single role can be played by multiple people
* Roles should describe a users objective
    * What does the user want to do?
    * "User" is not a good role (everyone is a user)
* Examples of roles
    * Shopper
    * Account holder
    * Customer
    * Admin
    * Manager
* Personas describe a typical person who plays a role
    * In a real-world app, go find your users and talk to them
    * Personas tell a story of who they are
    * Aren't a list of job functions
    * For each role, there could be many personas
* Example persona:
    * Jocelyn is a busy working mom who wants to access MegaCorp Bank to check her account balances and make sure that there are enough funds to pay for her kids' music and sport lessons. She also uses the site to automate payment of bills and view her balances. She wants to save time and money, and wants a card that gives her cash back.
* User stories describe a feature from the user's point of view
    * Give each story a title that describes its purpose
    * Write a short, one sentence description
    * Specify the user role, what they want to do, and why
    * Use the template: As a [role], I want to..., so that I can...
* Example user story:
    * As an account holder, I want to check my available balance at any time of day so I am sure not to overdraw my account
* Evaluate user stories with the INVEST criteria:
    * Independent, Negotiable, Valuable, Estimatable, Small, Testable


### SLOs, SLIs, and SLAs
* Quantitative requriements are things that are measurable
    * Given the constraints:
        * Time
        * Finance
        * People
    * What can be achieved:
        * How many users are there?
        * How much data is there?
        * What are the rewards and risks?
        * Which features can be launched?
* KPIs and SLIs
    * Key performance indicators (KPIs) are metrics that can be used to measure success
        * In business, common KPIs include:
            * Return on investment
            * Earnings before interest and taxes
            * Employee turnover
            * Customer churn
        * In software, common KPIs include:
            * Page views
            * User registrations
            * Clickthroughs
            * Checkouts
        * KPIs indicate whether you're on track to achieve the goal
            * Goal: Increase turnover for an online store
            * KPI: The percentage of conversions on the website
    * For KPIs to be effective, they must be SMART
        * Specific
        * Measurable
        * Achievable
        * Relevant
        * Time-bound
    * An SLI is a measurable attribute of a service (e.g., availability)
* SLOs and SLAs
    * The SLO is the number or goal you want to achieve for a given SLI for a given duration
        * Do you want 95%, 99%, or 99.99% availability?
    * An SLA is a binding contract providing the customer compensation if the service doesn't meet specific expectations
        * The SLA is a more restrictive version of the SLO
    * Tips for determining SLOs
        * Goal isn't to make SLOs as high as possible; goal is to make them as low as you can get away with while still making users happy. That's why it's important to understand your users
        * The higher you set the SLO, the higher the cost in compute resources (redundancy) and operations support (people time)
        * Apps should not significantly outperform their SLOs, because users come to expect the level of reliability you usually give them
    * The SLA stipulates that:
        * A penalty will apply to the provider if the service doesn't maintain certain availability and/or performance thresholds
        * If the SLA is broken, the customer will receive compensation from the provider
    * Not all services have an SLA, but all services should have an SLO
    * Your SLO thresholds should be stricter than your SLA
    * Example SLI, SLO, and SLA:
        * SLI: The latency of successful HTTP responses (HTTP 200)
        * SLO: The latency of 99% of the responses must be ≤ 200ms
        * SLA: The user is compensated if 99th percentile latency exceeds 300ms
  
