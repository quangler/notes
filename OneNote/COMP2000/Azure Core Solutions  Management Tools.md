**Azure IoT -** Internet of Things

- Enables devices to gather and relay info
- Any device that has a sensor and internet connection capable of sending data
    
    - (temp, geo location, light, pressure sensors etc.)

IoT use cases:

- Running a refrigerated vending machine business; got to make sure the sensors are all working and it can detect stock, temperature, etc.
- This concerns us because we have to make sure that we can support businesses

  

Azure IoT hub:

- Managed cloud services that acts as the hub for IoT devices/applications
- Handles communication, data/messaging, and command/control.

  

**Azure AI -** Artificial Intelligence

- Idea is to create something that can adapt

Two approaches to AI:

- Deep learning system, based on neural network of human brain, allows it to grow through experience
- Machine learning, uses existing data to train a model then use it to create new data, or estimate outcomes

  

**Azure AI Services:**

- **Azure Machine Learning**
    
    - Platform for data analysis, data sources are connected to platform and users to train/test models.
    - Can interact real time with API endpoints
- **Azure Cognitive Services**
    
    - Prebuild machine learning models
    - Enables apps to see, hear, speak, understand, and begin to reason
    - Cognitive services are accessed through APIs - this means flexible deployment
    - 4 categories: Language, Speech, Vision, Decision
- **Azure Bot Services**
    
    - Combined with bot framework to provide a platform for virtual assistants
    - Typically rely on cognitive services to understand what the bot is being asked for
    - Goal of bots is to reduce simple tasks that would be better automated

  

**Azure serverless topologies**

- Ide is no infrastructure or maintenance is required
- Still servers running a serverless environment
- Serverless computing is provided by:
    
    - Azure functions
    - Azure logic apps

  

Azure Functions:

- Event based code snippets - run in response to an event
- Functions can be written in most common languages
- **Functions behave like they are restarted every time it responds to an event** #important
- Functions can be linked together (durable functions)￼

Azure logic apps:

- Low/no-code development platform
- Executes logic triggered by an azure service
- Over 200 service connectors + infinite custom ones

  

**Azure Devops / GitHub**

- Designed to facilitate larger tch teams working towards a common goal
- Automation of development, maintenance, and deployment of software systems
- Speed up releases of software changes, while maintaining quality standards

  

- Split into 5 categories:
    
    - Azure Repos
    - Azure boards
    - Azure pipelines
    - Azure artifacts
    - Azure test plans

  

GitHub

- Repository for open-source software
- Git is decentralized source-code management tool
- Best used for dev teams that need:
    
    - Coordination
    - Progress / issue reporting
    - Discussion / resolving issues
    - Provide documentation

  

DevOps Puzzle

- Automated deployment and teardown of software testing VMs/software builds
- Pre-create test labs are prepped once and deployed as needed
- Cost control built in as test VMs don’t have to run 24/7 and can be used to test and delete code quickly

  

**Managing / configuring Azure**

- Azure management can be done through CLI or GUI
- Main tools:
    
    - Azure portal
    - Azure mobile app - kinda sucks
    - Azure powershell: commands call a REST API to manage the orchestrator
    - Azure cli - running powershell through bash (its just bash): also use REST APIs
    - ARM templates - azure resource manager: **use JSON format**, ARM templates allow admins/devs to expedite deploying/tearing down hundreds of resources quickly
      
    

  

**Monitoring Services**

General: - are we using the cloud correctly?

Are we spending more than we need to?

Do we have everything secured properly?

How resilient are our resources?

  

Azure monitor has three primary offerings (more that are 3rd party):

- **Azure Advisor**
    
    - Used to evaluate your cloud implementation
    - Recommendations are made through the azure portal/API: reliability, security, performance, operational excellence, cost performance
- **Azure Monitor**
    
    - Used with azure/hybrid cloud
    - Data can be: collected, analyzed, visualized, use to generate even based actions
      
    
- **Azure Service Health**
    
    - Provides personalized view of your instance: (services, regions, resources)
    - Health.azure.com (I think? You don’t need to sign in)
    - Service health allows you to keep an eye on server event types: service issues, planned maintenance, health advisories.