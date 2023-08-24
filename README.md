# lti-example-app
App demonstrating the use of the laravel-celtic-lti library.

## Setup
We assume that you already know how to setup and run a Laravel app, including:
* Setting the APP_KEY and APP_URL environment variables
* Starting the Laravel server
* Running database migrations and other `php artisan` commands

This app was built following the instructions in the wiki at https://github.com/longhornopen/laravel-celtic-lti/wiki .  See that wiki for more details about how to get started writing your own app, once you understand this one.

This app is an LTI 1.3 app.  The laravel-celtic-lti library supports LTI 1.0-1.2, but those standards are
deprecated and not recommended for new development.

You'll need to do the following to get this app hooked up to the LMS of your choice:
* Set the RSA public/private key pair in config/lti.php.  (You can generate a key pair at https://cryptotools.net/rsagen if you don't have a better tool for doing that.)
* Tell this app about the LMS, via the `php artisan lti:add_platform_1.3` command.  Mostly these are URLs and IDs that you get from your LMS administrator.  Some shortcuts are provided for popular LMSes that have documented their URLs.
* Tell the LMS about this app, by giving the LMS several URLs that the app provides.  See routes/web.php for those URLs.  The UI for how you do this is LMS-specific, but generally there's an app settings list or app registry of some kind, which will contain these URLs.

After those steps are completed, the LMS and this app will know how to talk to each other, and you should be able to launch this app as an LTI tool in your LMS.

## Walkthrough
See the comments in the following files for explanation of the various parts of the app:
- routes/web.php
- config/lti.php
- app/Http/Controllers/LtiController.php
- app/Http/Middleware/VerifyCsrfToken.php

## Thanks!
Please contact us if we can clarify anything.