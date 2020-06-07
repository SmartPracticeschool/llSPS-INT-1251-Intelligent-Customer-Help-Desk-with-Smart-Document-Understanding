# Intelligent Customer Help Desk with Smart Document Understanding

### Node_Red Dasboard link after deploying : https://myhelpdesk.mybluemix.net/ui/
### Demonstration Video link : https://youtu.be/fOXd9k6Rx3E

The typical customer care chatbot can answer simple questions, such as store locations and hours, directions, and maybe even making appointments. When a question falls outside of the scope of the pre-determined question set, the option is typically to tell the customer the question isn’t valid or offer to speak to a real person.

In this project, there will be another option. If the customer question is about the operation of a device, the application shall pass the question onto Watson Discovery Service, which has been pre-loaded with the device’s owners manual. So now, instead of “Would you like to speak to a customer representative?” we can return relevant sections of the owners manual to help solve our customers’ problems.

To take it a step further, the project shall use the Smart Document Understanding feature of Watson Discovery to train it on what text in the owners manual is important and what is not. This will improve the answers returned from the queries.

## Project Scope
- Create a customer care dialog skill in Watson Assistant
- Use Smart Document Understanding to build an enhanced Watson Discovery collection
- Create an IBM Cloud Functions web action that allows Watson Assistant to post queries to Watson Discovery
- Build a web application with integration to all these services & deploy the same on IBM Cloud Platform

In Watson Discovery I have added ecobee3_userguide.

#### Goto the Node-RED UI : https://myhelpdesk.mybluemix.net/ui/

Have a casual talks like hello, bye, good morning, etc, for (SDU) like how to set time, how to turn on heater, how to access setting, how to operate thermostat, how to set up thermostat only.

With the help of Smart Document Understanding feature, Watson Discovery model will be customized so that the queries will be focused on the search for most relevant information from the users manual uploaded in Discovery.

Watson Assistant will acts as the Chatbot will predefined standard dialogs loaded to handle typical conversation between customer. When the query comes under technical domain, it will communicate with Discovery service with the help of 'Webhook'.
Webhook will be created by defining a web action using Cloud Functions.

Node-Red will wire all the services utilized in this project and create a UI for the customers.

## Flow

![Image description](https://github.com/IBM/watson-discovery-sdu-with-assistant/blob/master/doc/source/images/architecture.png)

This flow basically summarizes the project. It begins with :
1. The annotation of document using Watson Dicovery SDU.
2. The user interacts with Node-Red app UI.The chatbot engages the user in conversation.
3. Dialog in this interaction is coordinated by Watson Assistant.
4. If the customer asks a technical question, it will be passed to Cloud Functions action.
5. This action will further pass onto to Watson Discovery and return with appropriate solution.
