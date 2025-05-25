# CI-Jenkins

## Task Overview

This project demonstrates the Jenkins setup with:

- Jenkins installed on port `8081`
- Configured slave node
- Two jobs:
    - `helloci-build`: builds Maven project from https://github.com/vitalliuss/helloci
    - `taf-tests`: runs UI automated tests from [TAF-patterns](https://github.com/marynayatskevych/TAF-patterns)

## Jenkins Setup

- Jenkins installed locally via Homebrew
- Port changed to `8081`
- Slave agent created and connected manually via `agent.jar`
- Node label: `slave1`

## Job 1: helloci-build

- Type: Freestyle project
- Git repo: `https://github.com/vitalliuss/helloci`
- Build command: `mvn -f Java/pom.xml clean install`
- Runs on: `slave1`

## Job 2: taf-tests

- Git repo: [TAF-patterns](https://github.com/marynayatskevych/TAF-patterns)
- Runs automated UI tests via `mvn clean test`
- Parameters:
    - `browser`: chrome, firefox
    - `suite`: smoke.xml, regression.xml
    - `env`: dev, prod
- Triggers:
    - Poll SCM every 5 minutes
    - Daily at midnight
- Runs on: `slave1`

## 📸 Screenshots folder includes:

- Jenkins Dashboard (with both jobs)
- Slave Node Online
- Job 1 Configuration
- Job 2 Configuration
- Console Output from each job (.txt files)

## Result

All requirements are implemented. Jenkins is fully operational with CI jobs running on a configured slave node.
