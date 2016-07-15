NPM Vendor DevOps Requirements
==============================

###Vendors must write [12 Factor Apps](http://12factor.net/):

- Use declarative formats for setup automation to minimize time and cost for new developers joining the project
- Have a clean contract with the underlying operating system, offering maximum portability between execution environments
- Are suitable for deployment on modern cloud platforms, obviating the need for servers and systems administration
- Minimize divergence between development and production, enabling continuous deployment for maximum agility
- Scale up without significant changes to tooling, architecture, or development practices

**Examples**:

- Apps should not rely on the underlying filesystem as it is ephemeral
    - User uploads should be stored on cloud storage
    - App logs should be sent to `stdout` or `stderr`
    - Session data should not be stored in a file
- Apps should communicate with external services (db, queue, cache) via URL provided in the App's config
- App servers should not rely on knowledge of other app servers in a horizontally scaled setup as these other servers come and go

###Vendors must use NPM Digital's approved tech stack:

**Hosting**

Currently, all apps are deployed to [Heroku](https://heroku.com). Vendors will be given appropriate access to the apps they're working on within NPM Digital's Enterprise account.

- [Heroku PHP Docs](https://devcenter.heroku.com/categories/php)
- [Heroku Ruby Docs](https://devcenter.heroku.com/categories/ruby)
- As an app's security needs require, apps will be deployed within a [Heroku Private Space](https://www.heroku.com/private-spaces)

**Webservers**

- Apache 2.4+ for legacy PHP apps
- Nginx 1.8+ for new PHP apps
- Puma for Rails apps

**Data Stores**

- Postgresql for new apps
- MySQL 5.7+ for legacy apps
    - the version is important as 5.7 added support for UTF8-MB4 and changed some default config for other things like `GROUP BY`
- Redis for caching, queueing, sessions

**Backend Languages**

- PHP 5.6+ for legacy PHP apps
- PHP 7+ for new PHP apps
- Ruby 2.3+ for Rails apps
- NodeJS 0.12+ for legacy apps
- NodeJS 6+ for new apps

**Continuous Integration and Delivery**

- Unit, integration, and acceptance level testing should be able to run via Codeship.io
    - PHP: [https://codeship.com/documentation/languages/php/](https://codeship.com/documentation/languages/php/)
    - Ruby: [https://codeship.com/documentation/languages/ruby/](https://codeship.com/documentation/languages/ruby/)

**Dependency Management**

- PHP: Composer
- Ruby: Bundler

**Git Repository Hosting**

- Github should be used for all app code, including 3rd party packages

### Questions of Concerns?

Feel free to reach out in the #devops channel on NPM Digitla's Slack.
