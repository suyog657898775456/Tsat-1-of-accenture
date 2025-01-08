# Tsat-3-of-accenture

pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh './gradlew assemble'
            }
        }
        stage('Test') {
            steps {
                sh './gradlew test'
            }
        }
    }
}

// 2nd

name: Jenkinsfile Runner

on:
  push:
    branches:
      - '**'

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Set up JDK
        uses: actions/setup-java@v3
        with:
          distribution: 'temurin'
          java-version: '11'

      - name: Run Jenkinsfile Runner
        uses: jenkinsci/jenkinsfile-runner-action@v2
        with:
          command: './gradlew assemble && ./gradlew test'

// 3rd

public List<Product> searchProducts(String query) {
    return Collections.emptyList();
}


git add .
git commit -m "Break tests by returning empty list"
git push origin <branch-name>

