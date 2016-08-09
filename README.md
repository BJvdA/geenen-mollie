# geenen-mollie

Unofficial implementation of the mollie-reseller API for node. This package is created
because some other implementations are outdated or bloated.

All available methods are supported, you should, however, always check the results for
any validation errors reported by Mollie, as this module does not check for required
parameters.

https://www.mollie.com/nl/support/post/documentatie-reseller-api

## About

Mollie is a Payment Service Provider from the Netherlands. They allow you to create
new customers trough their re-seller API as part of your platform integration.

The following API methods are supported:

* account-claim
* account-create
* account-edit
* account-valid
* available-payment-methods
* bankaccount-edit
* bankaccounts
* disconnect-account
* get-login-link
* profile-create
* profiles
* set-fees

## Example

The folowing is an example of how to create a new Mollie account for your customer.
You will need to sign up for a mollie account and the reseller program in order to
retrieve the correct credentials. Check the tests for more examples.

```javascript
    const Mollie = require('geenen-mollie');

    Mollie.configure({
        partner_id: '<MOLLIE_PARTNER_ID>',
        profile_key: '<MOLLIE_PROFILE_KEY>',
        app_secret: '<MOLLIE_APP_SECRET>'
    });

    Mollie.accountCreate({
        testmode: 1,
        username: 'glenngeenen',
        name: 'Glenn Geenen',
        company_name: 'GeenenTijd',
        email: 'glenn@geenentijd.be',
        address: 'My Address 1',
        zipcode: '1000',
        city: 'Brussels',
        country: 'BE'
    }, function(err, result) {
        console.log(result);
    });
````
