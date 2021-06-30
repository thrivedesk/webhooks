## ThriveDesk

### Apps/Webhooks

Webhooks are the way to have ThriveDesk call a script on your server when one or more events have happened, enabling you to react however you like. Webhooks can be thought of as event listeners or push notifications.

### Available Events:

> Each request body uses the object format linked in the table below. All webhooks use the v1 payload.

| Event Name                            | Event Type                        |
| ------------------------------------- | --------------------------------- |
| *Conversation created*                | *conversation.created*            |
| *Conversation assigned*               | *conversation.assigned*           |
| *Note added to conversation*          | *conversation.note.added*         |
| *User replies to conversation*        | *conversation.agent.reply*        |
| *Customer replies to conversation*    | *conversation.contact.reply*      |
| *Conversation status updated*         | *conversation.status.updated*     |
| *Conversation Tags added/updated*     | *conversation.tags.updated*       |
| *Conversation moved*                  | *conversation.moved*              |

### Response:

> A sample response body has been demonstrated here:

```json
{
  "eventType": "conversation.tags.updated",
  "data": {
    "id": "dea1fca0-6529-43fd-91df-044afbf2a1d4",
    "ticketId": 26,
    "subject": "Duis aute irure dolor in reprehenderit in voluptate velit",
    "excerpt": "Cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat...",
    "status": "Active",
    "priority": "Normal",
    "active": true,
    "createdAt": "2021-06-29T13:04:05.000000Z",
    "tags": [
      {
        "name": "Beatae"
      },
      {
        "name": "Consequuntur"
      },
      {
        "name": "Cumque"
      }
    ],
    "inbox": {
      "id": "f86385ff-9ce5-456a-a207-0bbf4ec59c0e",
      "name": "Dev",
      "inboxAddress": "example@app.thrivedesk.email",
      "connectedEmailAddress": "example@mail.com",
      "defaultStatus": "Active"
    },
    "cc": [
      "examplecc@mail.com"
    ],
    "bcc": [
      "examplebcc@mail.com"
    ],
    "assignedTo": {
      "id": "050cbdb6-a973-40df-a5dd-b7f72c993055",
      "firstName": "Assigned",
      "lastName": "Example",
      "email": "exampleassigned@mail.com"
    },
    "contactInfo": {
      "id": "925298d4-a7d9-4d6b-8a01-10b2dea439aa",
      "name": "example",
      "email": "example@mail.com",
      "avatar": null
    },
    "hasAttachment": false,
    "hasInlineAttachment": false,
    "isDraft": false,
    "threadsCount": 3,
    "threads": [
      {
        "id": "967b48b3-32d7-4d63-81cc-4f6d04d879b1",
        "type": "Email",
        "status": "Active",
        "messageId": "<eb906211-6a52-4351-b9bd-f886933d6cf8@thrivedesk.test>",
        "direction": "Outbound",
        "htmlBody": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut...",
        "textBody": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut...",
        "createdAt": "2021-06-29T13:04:05.000000Z",
        "updatedAt": "2021-06-29T13:04:05.000000Z",
        "viewedAt": null
      },
      {
        "id": "e84aea7e-65ee-4b5a-a8d0-4f216192847e",
        "type": "Email",
        "status": "Active",
        "messageId": "<e8fa8cbc-47b1-4e7e-996d-a37fe4ef76dd@thrivedesk.test>",
        "direction": "Outbound",
        "htmlBody": "Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea...",
        "textBody": null,
        "createdAt": "2021-06-29T13:04:46.000000Z",
        "updatedAt": "2021-06-29T13:04:46.000000Z",
        "viewedAt": null
      },
      {
        "id": "ce7946ae-86c4-4891-af2a-485d984a6a74",
        "type": "Note",
        "status": "Active",
        "messageId": "<0bd13e23-9d3a-4c61-a490-c3e8b0136bc4@thrivedesk.test>",
        "direction": null,
        "htmlBody": "Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla...",
        "textBody": null,
        "createdAt": "2021-06-29T13:04:59.000000Z",
        "updatedAt": "2021-06-29T13:04:59.000000Z",
        "viewedAt": null
      }
    ]
  }
}
```

### Response fields (Conversation):

| Path                      | Type          | Description |
|---------------------------|---------------|-------------|
| *eventType*               | *String*      | Type of the event, one of the available events |
| *data*                    | *Object*      | Main response body |
| *id*                      | *String*      | Unique identifier |
| *ticketId*                | *Integer*     | Unique ticket identifier |
| *subject*                 | *String*      | Conversation subject |
| *excerpt*                 | *String*      | Conversation excerpt |
| *status*                  | *String*      | Conversation status, one of: <br/> ***Active*** <br/> ***Pending*** <br/> ***Closed*** |
| *priority*                | *String*      | Conversation priority, one of: <br/> ***High*** <br/> ***Normal*** <br/> ***Low*** |
| *active*                  | *Boolean*     | Conversation active status |
| *createdAt*               | *String*      | UTC time when the conversation was created |
| *tags*                    | *Array*       | List of tags, with the following fields: <br/> ***name*** |
| *inbox*                   | *Object*      | Inbox information of the conversation, with the following fields: <br/> ***id*** <br/> ***name*** <br/> ***inboxAddress*** <br/> ***connectedEmailAddress*** <br/> ***defaultStatus*** |
| *cc*                      | *Array*       | List of emails that are cc’d |
| *bcc*                     | *Array*       | List of emails that are bcc’d |
| *assignedTo*              | *Object*      | Who the conversation is assigned to, with the following fields: <br/> ***id*** <br/> ***firstName*** <br/> ***lastName*** <br/> ***email*** |
| *contactInfo*             | *Object*      | An object containing the contact information associate with the conversation with the following fields: <br/> ***id*** <br/> ***name*** <br/> ***email*** <br/> ***avatar*** |
| *hasAttachment*           | *Boolean*     | Conversation contain attachment or not |
| *hasInlineAttachment*     | *Boolean*     | Conversation contains inline attachment or not |
| *isDraft*                 | *Boolean*     | Is conversation drafted or not |
| *threadsCount*            | *Integer*     | Number of threads the conversation has |
| *threads*                 | *Array*       | List of threads, with the following fields: <br/> ***id*** <br/> ***type (Email, Note, Draft)*** <br/> ***status*** <br/> ***messageId*** <br/> ***Direction (Inbound, Outbound )*** <br/> ***htmlBody*** <br/> ***textBody*** <br/> ***createdAt*** <br/> ***updatedAt*** <br/> ***viewedAt*** |

### Headers:

> Each webhook includes one ThriveDesk header:

- ***X-TD-SIGNATURE:*** The computed signature generated by ThriveDesk. Used to know if the request is valid or not.

### Verifying:

Webhooks can be verified as coming from ThriveDesk by calculating a digital signature. Each webhook request contains an ***X-TD-SIGNATURE*** header, generated using the given secret key, along with the JSON encoded payload data (only the ***data*** field of response data) sent in the request.

To verify if the request came from ThriveDesk, compute the HMAC hash and compare it to the header value sent in the request. If the computed signatures match, you can be sure the request was sent from ThriveDesk.

Signatures are calculated based on the raw request body passed to your servers by ThriveDesk. This means that if non-ASCII characters are contained in the payload, you will need to calculate the signature based on the escaped, transliterated string passed to you by ThriveDesk. We recommend this as best practice in general, even for those primarily working with ASCII data.

#### PHP:

```php
function isFromThriveDesk($data, $signature, $secret_key) {
    $calculate = base64_encode(hash_hmac('sha1', json_encode($data), $secret_key, true));

    return $signature == $calculate;
}

/**
 * $request->get('data')
 * 
 * only the data field of request body
 */ 
if (isFromThriveDesk($request->get('data'), $signature, $secret_key)) { 
	// do something
}
```

#### NODE JS:

```javascript
const crypto = require('crypto');

/**
 * request.body.data
 *
 * only the data field of reqeust body
 */
if (isFromThriveDesk(request.body.data, signature, secret_key)) {
    // do something
}

let isFromThriveDesk = (data, signature, secret_key) => {
    return signature === crypto
        .createHmac('SHA1', secret_key)
        .update(JSON.stringify(data))
        .digest('base64');
}
```

### Responses:

Anything returned to the body of the response will be discarded. In order to know the webhook was successful, an HTTP status code between ***200*** and ***299*** must be returned.

A status code of ***410*** will cause the webhook to get deactivated/deleted.

Any status codes other than something between ***200*** and ***299*** or ***410*** is a failure of some kind. If the event fails several times, it is discarded. Webhooks are automatically deactivated if three or more events get discarded.
