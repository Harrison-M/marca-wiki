THIS IS A WORK IN PROGRESS just keeping notes for myself as I go so I can tell everybody what they need to do when the time comes -- Andy

* Three new parameters are needed:
  * pay_to_enroll (set to true to use the payment infrastructure, false to turn it off)
  * stripe_secret_key (null if not using payment, or stripe secret key from the stripe api)
  * stripe_publishable_key (null if not using, or stripe publishable key from api)

* PHP extensions need to be installed to work correctly 
  * curl extension (ubuntu package php5-curl)
  * intl extension (ubunut package php5-intl)