# qaae-training-test-app

## Overview
This project includes a NodeJS based web app comprised of ExpressJS for the server-side, and ReactJS for the client-side.
Additionally this project includes REST API's, and GraphQL API's.
This project is intentionally buggy and not pretty in order to design tests that find bugs.

This project contains the code for unit tests, mocks, and integration tests for REST and GraphQL API's, as well as Cypress, Test Cafe, and Selenium UI end-to-end tests.

## Setup steps
1.  Install node v18.15.0 LTS, and NPM 9.6.2
2.  npm install -g npm@latest
3.  node -v
    v18.15.0
4.  npm -v
    9.6.2
5.  nvm list
6.  nvm use 18.15.0

### Run the test server web app:
1.  Open a terminal, and execute these commands:
2.  `cd qaae-training-test-app/`
3.  `cd server/`
4.  `npm install`
5.  Run Jest tests
6.  `npx jest __tests__/jest.test.js`
```
GET / 200 377.697 ms - 969
PASS __tests__/jest.test.js
  test the root path
    ✓ it should respond to the GET method (415 ms)

Test Suites: 1 passed, 1 total
Tests:       1 passed, 1 total
Snapshots:   0 total
Time:        3.265 s
Ran all test suites matching /__tests__\/jest.test.js/i.
```
7.  `npx jest models/*`
8.  `npx jest routes/__tests__/.+_route.test.js`
9.  `npx jest graphql/__tests__/.+_route.test.js`
```
POST /graphql 200 2.220 ms - 266
POST /graphql 200 2.216 ms - 270
POST /graphql 200 2.134 ms - 408

Test Suites: 3 passed, 3 total
Tests:       9 passed, 9 total
Snapshots:   0 total
Time:        3.141 s
Ran all test suites matching /graphql\/__tests__\/.+_route.test.js/i.

```
10.  The tests should run and pass
11.  Run tests from NPM
12.  `npm test -- models/*`
13.  `npm test -- routes/__tests__/(.+)_route.test.js`
14.  `npm test -- graphql/__tests__/(.+)_route.test.js`
15.  The tests should run and pass
16.  Start the web app
17.  `npm start`
18.  Open a browser to http://localhost:9000/
19.  The test web app page should display
20.  Open a **second** terminal, and execute these commands:
21.  Control+C to shut down the server
22.  The test web app page will not display
23.  `npx nodemon index.js`
24.  Open a browser to http://localhost:9000/
25.  The test web app page should display
26.  Run Jest tests
27.  `npx jest routes/__tests__/(.+)_rest.test.js`
28.  `npx jest graphql/__tests__/(.+)_gql.test.js`
29.  The tests should run and pass
30.  Run tests from NPM
31.  `npm test -- routes/__tests__/(.+)_rest.test.js`
32.  `npm test -- graphql/__tests__/(.+)_gql.test.js`
33.  The tests should run and pass
34.  Open a browser to http://localhost:9000/graphql
35.  Run a query in GraphiQL:
36.  `{ companies { id company location rating reviews } }`
37.  Control+C to shut down the server
38.  The test web app page will not display

### Run the test client web app:
1.  Open a **third** terminal, and execute these commands:
2.  `cd myTestApp/`
3.  `cd client/`
4.  `npm install`
5.  `npm start`
6.  Open a browser to http://localhost:3000/
7.  The test web app page should display
8.  Control+C to shut down the server
9.  The test web app page will not display

### Run the Cypress tests:
1.  Open a **first** terminal, and execute these commands:
2.  `cd myTestApp/`
3.  `cd server/`
4.  `npm start`
5.  Open a **second** terminal, and execute these commands:
6.  `cd myTestApp/`
7.  `cd server/`
8.  `npx cypress open`
9.  In the Cypress browser, select `E2E Tssting`
10.  Select a browser, select `Start E2E Testing`
11.  After the tests finish, close the Cypress browsers
12.  `npx cypress run --browser chrome --headed --spec "cypress/e2e/cypress.test.cy.js"`
13.  `npx cypress run --browser firefox --headed --spec "cypress/e2e/cypress.test.cy.js"`
14.  Open a **third** terminal, and execute these commands:
15.  `cd myTestApp/`
16.  `cd client/`
17.  `npm start`
18.  Open a **fourth** terminal, and execute these commands:
19.  `cd myTestApp/`
20.  `cd client/`
21.  `npx cypress open`
22.  In the Cypress browser, select `E2E Tssting`
23.  Select a browser, select `Start E2E Testing`
24.  After the tests finish, close the Cypress browsers
25.  `npx cypress run --browser chrome --headed --spec "cypress/e2e/cypress.test.cy.js"`
26.  `npx cypress run --browser firefox --headed --spec "cypress/e2e/cypress.test.cy.js"`

### Run the TestCafe tests:
1.  Open a **first** terminal, and execute these commands:
2.  `cd myTestApp/`
3.  `cd server/`
4.  `npm start`
5.  Open a **second** terminal, and execute these commands:
6.  `cd myTestApp/`
7.  `cd server/`
8.  `npx testcafe chrome testcafe/testcafe.test.js`
9.  Open a **third** terminal, and execute these commands:
10.  `cd myTestApp/`
11.  `cd client/`
12.  `npm start`
13.  Open a **fourth** terminal, and execute these commands:
14.  `cd myTestApp/`
15.  `cd client/`
16.  `npx testcafe firefox testcafe/testcafe.test.js`

### Run the Selenium-Webdriver tests:
You may run into this error "ENOENT: no such file or directory, open 'node:events'", see the fix below.
1.  Open a **first** terminal, and execute these commands:
2.  `cd myTestApp/`
3.  `cd server/`
4.  `npm start`
5.  Open a **second** terminal, and execute these commands:
6.  `cd myTestApp/`
7.  `cd server/`
8.  `npx jest selenium/__tests__/selenium.test.js --browsers=chrome`
9.  `npx jest selenium/__tests__/workflow.test.js --browsers=firefox`
10.  Open a **third** terminal, and execute these commands:
11.  `cd myTestApp/`
12.  `cd client/`
13.  `npm start`
14.  Open a **fourth** terminal, and execute these commands:
15.  `cd myTestApp/`
16.  `cd client/`
17.  `npx jest selenium/__tests__/selenium.test.js --browsers=chrome`
18.  `npx jest selenium/__tests__/workflow.test.js --browsers=firefox`

If you run into this error "ENOENT: no such file or directory, open 'node:events'", it is a problem with the Selenium library trying to load the events library.
You can fix this by opening this file:

`qaae-training-test-app\server\node_modules\selenium-webdriver\bidi\index.js`

Then change this line of code from:

`const { EventEmitter } = require('node:events')`

to:

`const { EventEmitter } = require('events')`

Then rerun your Selenium tests


