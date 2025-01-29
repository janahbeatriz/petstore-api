# Petstore API Tests with Newman

This repository contains automated API tests for the [Petstore API](https://petstore.swagger.io/), implemented using [Newman](https://www.npmjs.com/package/newman). These tests ensure the reliability and correctness of the Petstore API endpoints. The project also includes a CI/CD workflow to run the tests and deploy the results to GitHub Pages.

## Features

- **Automated API Testing**: Ensures the functionality and reliability of Petstore API endpoints.
- **Newman Integration**: Executes tests written in Postman collections.
- **GitHub Actions CI/CD**: Runs tests automatically on every push to the `main` branch.
- **HTML Report Deployment**: Publishes detailed test reports to GitHub Pages.

---

## Project Structure

```
📦 petstore-api
├── .github/workflows    # GitHub Actions workflows
│   ├── newman.yml       # CI/CD workflow for Newman tests
├── petstore-api.json    # Postman collection with API tests
├── petstore-api-env.json # Environment variables for the API tests
├── README.md            # Project documentation
```

---

## Prerequisites

- [Node.js](https://nodejs.org/) (v16 or higher)
- [Newman](https://www.npmjs.com/package/newman) (installed globally)

---

## Installation and Setup

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/janahbeatriz/petstore-api.git
   cd petstore-api
   ```

2. **Install Dependencies**:
   ```bash
   npm install
   ```

3. **Install Newman** (if not already installed):
   ```bash
   npm install -g newman newman-reporter-html
   ```

---

## Running the Tests Locally

1. Run the Postman tests using Newman:
   ```bash
   newman run petstore-api.json -e petstore-api-env.json -r html,cli --reporter-html-export newman-report.html
   ```

2. View the generated HTML report:
   Open the `newman-report.html` file in your browser to view detailed test results.

---

## CI/CD Workflow

This repository includes a GitHub Actions workflow (`newman.yml`) that:
1. Runs Newman tests on every push to the `main` branch.
2. Generates an HTML report of the test results.
3. Deploys the report to GitHub Pages.

### Trigger the Workflow

Push changes to the `main` branch to automatically run the tests and deploy the report.

---

## View Test Reports

After the workflow runs successfully, the HTML report will be available via GitHub Pages at:
[https://janahbeatriz.github.io/petstore-api/](https://janahbeatriz.github.io/petstore-api/)

---

## Contributing

Feel free to fork this repository and create a pull request for improvements or additional test cases. Contributions are welcome!

---

## License

This project is licensed under the MIT License.
