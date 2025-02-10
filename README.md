# 🚀 Petstore API Testing Project

Welcome to the **Petstore API Testing Project**! This repository demonstrates robust API testing practices for the [Swagger Petstore API](https://petstore.swagger.io/). It showcases automated testing, CI/CD integration, dynamic reporting, and deployment to GitHub Pages. This project is designed to validate API functionalities and ensure reliability with automation-driven workflows.

---

## 📝 Project Overview

This project leverages **Postman** and **Newman** for automated testing of the Swagger Petstore API. The tests ensure seamless functionality for the following operations:
- Placing an order
- Retrieving order details
- Deleting an order

Additionally, test reports are auto-generated and deployed to **GitHub Pages** for transparency and accessibility.

---

## ⚙️ Features

- **Dynamic Environment Variables:** Automates the handling of `orderId` and `url` to maintain flexibility across environments.
- **Automated CI/CD Workflow:** Integrated with **GitHub Actions** to run tests on every push to the `main` branch.
- **Detailed HTML Reports:** Automated HTML reports generated via **Newman** and deployed to GitHub Pages.
- **Chained Requests:** Dynamic usage of API responses in subsequent tests for end-to-end coverage.
- **Error Handling:** Graceful handling of test failures with comprehensive logs.

---

## 🛠️ Technologies Used

- **Postman:** API testing and collection management
- **Newman:** Command-line execution of Postman collections
- **GitHub Actions:** CI/CD integration
- **HTML Reporting:** Exporting detailed test results
- **GitHub Pages:** Hosting and sharing test reports

---

## 📂 Project Structure

```
📦 petstore-api
├── 🗂️ newman/                 # Directory for HTML reports
├── 🗂️ .github/workflows/      # CI/CD workflow file
├── petstore-api.json          # Postman collection
├── petstore-api-env.json      # Postman environment variables
├── README.md                  # Project documentation
```

---

## 🚀 Getting Started

### Prerequisites
- **Node.js** (v16 or above)
- **Newman CLI** (`npm install -g newman`)
- GitHub account with access to this repository

### Run Locally
1. Clone the repository:
   ```bash
   git clone https://github.com/janahbeatriz/petstore-api.git
   cd petstore-api
   ```

2. Install dependencies:
   ```bash
   npm install -g newman newman-reporter-html
   ```

3. Run the tests:
   ```bash
   newman run petstore-api.json -e petstore-api-env.json -r cli,html
   ```

4. Open the report:
   - Navigate to the `newman/` directory and open `index.html`.

---

## 💻 CI/CD Integration

### GitHub Actions Workflow
The CI/CD pipeline automatically:
1. Executes the Postman collection using **Newman**.
2. Generates HTML test reports.
3. Deploys the reports to **GitHub Pages**.

### Workflow File: `.github/workflows/run-newman-api-tests.yml`
```yaml
name: Run Newman API Tests

on:
  push:
    branches:
      - main

jobs:
  run-newman-tests:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v3

      - name: Set up Node.js
        uses: actions/setup-node@v3
        with:
          node-version: '18'

      - name: Install Newman
        run: npm install -g newman newman-reporter-html

      - name: Run Postman tests and generate HTML report
        run: |
          newman run petstore-api.json -e petstore-api-env.json -r html,cli --reporter-html-export newman/index.html || true

      - name: Deploy to GitHub Pages
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: newman
```

---

## 🧪 Test Scenarios

### 1. Place an Order (POST `/store/order`)
- Validates the order placement.
- Captures the `orderId` for subsequent tests.

### 2. Retrieve Order (GET `/store/order/{orderId}`)
- Verifies order details using the captured `orderId`.

### 3. Delete an Order (DELETE `/store/order/{orderId}`)
- Deletes the order and validates the response message.

---

## 🌐 View Test Reports

Test reports are automatically deployed to **GitHub Pages** and can be accessed [HERE](https://janahbeatriz.github.io/petstore-api/).

---

## 📈 Future Enhancements

- **Data-Driven Testing:** Use external files (CSV/JSON) for dynamic data sets.
- **Performance Testing:** Integrate with tools like **k6** or **JMeter**.
- **Additional Test Scenarios:** Add tests for invalid inputs, authentication, and boundary conditions.
- **Schema Validation:** Validate API responses against predefined JSON schemas.
- **Slack/Email Notifications:** Notify on test failures.

---

## 🤝 Contributing

Contributions are welcome! Please fork the repository and submit a pull request.

---

## 📜 License

This project is licensed under the [MIT License](LICENSE).
