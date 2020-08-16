# Run Tests

## Setup
1) Copy `web/core/phpunit.xml.dist` to `web/core/phpunit.xml`.
The start settings is to run in your local environment.
2) Unzip the base database (`docker/database/start-test/base.zip`)

## Run
1) Run `make test`


# Deprecated
## E2E

In this momment the test only run in your computer

### Dependencies
- NPM

### Run
1. Create user to e2e test in the admin
2. Add user and password in this variables in `src/front/.env`
```.env
## e2e (nightwatch)
NUXT_NW_E2E_USER=
NUXT_NW_E2E_PASS=
```
1. Go to `src/front/`
2. Run `npm run e2e`