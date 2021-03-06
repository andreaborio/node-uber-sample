### node-uber-sample

This is a simple node application for the Uber API. It implements that OAuth 2.0 flow and allows the user to request a
ride using a lat/lon or a location on a map. The application can also be configured to talk to the developer sandbox
rather than production to demonstrate how that flow works.

### Requirements
 * [NodeJS](https://nodejs.org/en/)
 * [npm](https://www.npmjs.com/)

### Getting Started
 * `git clone git@github.com:noonhub/node-uber-sample.git`
 * `cd node-uber-sample`
 * `npm install`
 * `cp config/example.default.json`
 * `open `config/default.json` and fill in your applications configuration found at https://developer.uber.com/dashboard
 * Run the app! `node app.js`

### Sandbox vs Production
The [Uber developer sandbox](https://developer.uber.com/docs/sandbox) allows a developer to simulate ride requests on
the API without requesting real cars and spending real $$.

The application is initially configured to run in sandbox mode. This can be changed to production mode by altering the
`env` variable in `config/default.json` from `sand` to `prod`.

When in sandbox mode you can change the status of a request by issuing a GET to `host/trips/:tripID/:status` where
`status` can be any of the [documented request statuses](https://developer.uber.com/docs/sandbox#section-put-request-statuses).

### Webhooks
This application can be set up to receive webhook events from Uber. In order to take advantage of this you will need to
configure a webhook URL in the application dashboard. This URL must be a publicly accessible HTTPS
address. If running this application on your local machine you can use [Ngrok](https://ngrok.com/) to expose a local
port from your machine at an HTTPS address.

### Surge
This application can handle the surge acceptance flow required for completing ride requests when surge is in affect.
In order for this to work properly the surge redirect URI in the application dashboard must be set correctly according
to the `host + webhook_path` configured in `config/default.json`.