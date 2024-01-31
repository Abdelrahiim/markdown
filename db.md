- Overview
  - Panora cloud → Dashboard for every admin
  - Admin → Magic links
  - Customer login with their accounts with magic links ( user connects event )
- Fields Mapping
  - Easily extend Panora’s unified model to recognize specific fields
  - Defining a custom field on Panora’s side, and then mapping it to a field from your customer’s software.
 - How to add?
   - Click Add Field Mapping. Select a unified object you want to extend, and give your custom field a slug and a friendly name. You also need to select a data type.
   - Now, move to the Map Fields section. To finish the mapping, select the custom field you just created, and fill the fields Provider and Linked User ID.

- Connection 
  - The connection object represents an access right to a user’s data
  - It's made using magic links 
- platforms
  - Service 
  - CRM or ticketing or ....
- What's panora?
  - Add an integration catalog to your product in minutes instead of months
    - integration catalog → 
  - Panora is the API for building all your customer-facing integrations.
    - customer-facing integrations
  - Build integrations quickly, without a dedicated team. Meet your customer’s expectations and stop losing deals because of unsupported integrations.
  - Move fast with our APIs & SDKs.
- API keys ( from docs )
  - From dashboard ( hosted and )
- connection_token
  - A connection_token is created everytime a user connects an account to your platform. 
  - You need to setup a webhook and listen to events `connection.created` to catch a connection_token. 
  - `connection_token` is a string, located in the “data” object, inside a connection.created event.
```json
{
    "id_event": "dc2d12b9-dd07-4e33-a244-d0560a9eeed7",
    "type": "connection.created",
    "data": {
        "id" : "6fc7017a-6596-4b05-81b6-595296a59f87"
        "connection_token": "CONNECTION_TOKEN_HERE",
        "provider_slug": "hubspot",
        ...
    },
    ...
}
```
- Magic link
  - Ask customers to grant you access to their tools, without writing code
- Webhook
  - Listen to events coming from multiple platforms
  - A notificaiton sent to the backend
  - Panora webhook: event → your endpoint
    - You can add webhooks as much as you like and filter the type of events you want to send to each endpoint
- Jobs
- CRM
  - Write contanct, deals and more?
- Ticketing
  - Opening, closing tickets and more

## Components
- Docs
  - Mintlify
- API → packages/api
  - Prisma
- Webapp
  - QuickStartPage → Integrate Panora
  - DashboardPage → API Requests
  - LogsPage → Jobs → useEvents
  - TaskPage → useEvents
  - ConfigurationPage 
    - useLinkedUsers
    - useWebhooks
    - useFieldMappings
  - ConnectionsPage
    - useConnections
    - Mostly magic links connections
  - ApiKeysPage
    - useApiKeys
- frontend-snippet
- embedded-catalog
- Shared-types

## Tasks 
- Create an initial figma design
- Make a list of bugs to fix
- Make a list of features to add
  - Only allow certain platforms in a magic link
  - Customise magic links
  - Add integrations
    - Slack
  - Revoke connection in a magic link
  - Build a dedecated page for each feature 
    - Easy integration
    - Unified
    - Secure
    - Grow faster
- Make 10 PR before mid of the month

## SDK code example
- PANORASDK_ACCESS_TOKEN?
- sdk.crmContact?

```javascript
import { PanoraSDK } from './src';

const sdk = new PanoraSDK({ accessToken: process.env.PANORASDK_ACCESS_TOKEN });

(async () => {
  const input = {
    email_addresses: [],
    field_mappings: {},
    first_name: 'John',
    last_name: 'Doe',
    phone_numbers: [],
  };
  const result = await sdk.crmContact.addContact(input, 'integrationId', 'linkedUserId', {
    remoteData: true,
  });
  console.log(result);
})();
```

## For who?
1. **Rapid Integration Catalog for SaaS Products:**
   - **Challenge:** A SaaS company in the project management space wants to quickly expand its product's functionality by integrating with popular tools used by project teams.
   - **Solution:** Panora allows the SaaS company to add an integration catalog that includes seamless connections with collaboration tools (e.g., Slack, Microsoft Teams), file-sharing platforms (e.g., Google Drive, Dropbox), and task management tools (e.g., Trello, Asana). Target customers for this integration are project managers, team leads, and professionals who rely on a variety of tools to manage their projects efficiently.

2. **Accelerated Development of Customer-Facing Integrations:**
   - **Challenge:** A software development company is building a customer relationship management (CRM) platform and needs to integrate with various communication tools and social media platforms.
   - **Solution:** Panora's API and SDKs enable the development team to build integrations quickly with email services (e.g., Gmail, Outlook), messaging platforms (e.g., Slack, Microsoft Teams), and social media platforms (e.g., Twitter, LinkedIn). The target customers for this integration are sales and marketing teams who use the CRM platform to streamline customer interactions and manage leads effectively.

3. **Improved Growth and Retention for SaaS Companies:**
   - **Challenge:** A subscription-based e-learning platform wants to enhance user engagement by integrating with collaboration and productivity tools commonly used by educators and students.
   - **Solution:** Panora facilitates out-of-the-box integrations with learning management systems (LMS), collaboration tools (e.g., Google Classroom), and communication platforms (e.g., Zoom). The target customers include educational institutions, teachers, and students who benefit from a seamless connection between the e-learning platform and their preferred tools, fostering a more integrated and user-friendly learning experience.
