# UI-Testing-e-commerce-Playwright-js
UI testing for a e-commere using Playwright with JS
### **Project Overview**

This project is a Playwright-based test automation framework designed to perform end-to-end testing on the UI. It employs the Page Object Model (POM) design pattern to encapsulate page-specific logic and enhance test maintainability.

### **Technologies Used**

* **Playwright:** A Node.js library to automate Chromium, Firefox and WebKit with a single API.
* **JavaScript:** The primary programming language for test scripts.
* **Page Object Model (POM):** A design pattern that separates page-specific logic from test cases.

### **Project Structure**

### **Getting Started**

1. **Clone the repository:**
   ```bash
   git clone https://github.com/olivaalbert1/UI-Testing-e-commerce-Playwright-js
   ```
2. **Install dependencies:**
   ```bash
   npm init playwright@latest
   ```

### **Running Tests**

* **All tests in headed mode:**
   ```bash
   BASEURL='PUT_HERE_YOUR_URL' npx playwright test --headed
   ```
* **Specific test file in headless mode:**
   ```bash
   BASEURL='PUT_HERE_YOUR_URL' npx playwright test tests/console-errors.spec.js
   ```
* **Specific test scenario in headless mode:**
   ```bash
   BASEURL='PUT_HERE_YOUR_URL' npx playwright test -g "No errors"
   ```
* **All tests in headless mode:**
   ```bash
   BASEURL='PUT_HERE_YOUR_URL' npx playwright test
   ```
* **If all the tests pass, no report will be prompted, but you can see the report with - Show report command:**
   ```bash
   npx playwright show-report
   ```
* **Execute test showing trace:**
   ```bash
   npx playwright test --ui
   ```

### **Configuration**

* **Base URL:** Set the base URL for your application in the terminal before running tests using the `BASEURL` environment variable. You can parameterize only the environment part, for example having in playwright.config.js baseUrl: 'https://{env}.myapplication.com/' and when executing the command just indicate qa,uat,prod... or the environment in which you want to run the tests. But as it has been explicitly indicated in the technical test statement not to upload the application URL to the repository, I have decided to parameterize the entire URL by command.
We can also use tags to assign some tests to certain environments, but that was outside the scope of the test.
* **Playwright Config:** Customize the Playwright configuration in `playwright.config.js` to suit your project needs.
<br> * I've configured a single retry for failed tests.
   ```js
   module.exports = defineConfig({
     retries: 1,
   })
   ```
<br> * I've divided the 4 tests into separate files to enable parallel execution. This configuration is adjustable.
<br> * Test traces are saved for every run, regardless of the outcome. However, this behavior can be customized ('off','on','on-all-retries','on-first-retry','retain-on-failure','retain-on-first-failure','retry-with-trace').
```js
   module.exports = defineConfig({
     trace: 'on',
   })
   ```
<br> * The tests are optimized to minimize wait times, only pausing for page loads or element visibility. 'await page.waitForTimeout(3000)' should be avoided.
<br> * I've selected Chrome as the default browser, but others can be added, and tests can even be run on mobile devices.
```js
   /* Configure projects for major browsers */
  projects: [
    {
      name: 'chromium',
      use: { ...devices['Desktop Chrome'] },
    },
  ]
   ```

### **Known Bugs and Issues**

* [Bug 1: blabla.]

### **Proposed Improvements**
1. blabla