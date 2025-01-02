# Petstore API

This repository contains the Petstore API, which provides a RESTful API for managing pets in a pet store. The API allows users to perform CRUD operations on pets, including adding, updating, deleting, and retrieving pet information.

## Getting Started

These instructions will guide you on how to set up and run the Petstore API on your local machine for development and testing purposes.

### Prerequisites

- Node.js (v18 or later)
- npm (v6 or later)
- Newman (Postman CLI)

## GitHub Actions
This repository is configured with GitHub Actions to automatically run Newman tests and deploy the results to GitHub Pages.

### Workflow Configuration
The workflow file .github/workflows/run-newman-tests.yml is set up to:

- Checkout the repository
- Set up the Node.jsenvironment
- Install Newman and the HTML reporter
- Run Postman tests and generate an HTML report
- Deploy the report to GitHub Pages

**Recent Report here:** https://janahbeatriz.github.io/petstore-api/  

### Installation

1. Clone the repository:

```sh
git clone https://github.com/janahbeatriz/petstore-api.git
cd petstore-api
