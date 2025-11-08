pipeline {
  agent any

  tools {
    nodejs 'Node18'  // from Global Tool Configuration
  }

  environment {
    DATABASE_URL = credentials('prod-db-url')
    CI = 'true'
    NODE_ENV = 'production'
  }

  options {
    timestamps()
    ansiColor('xterm')
  }

  stages {
    stage('Checkout') {
      steps { checkout scm }
    }

    stage('Install') {
      steps {
        // clean, reproducible installs
        sh 'npm ci'
      }
    }

    stage('Typecheck') {
      steps { sh 'npm run check' }
    }

    stage('Build') {
      steps {
        // builds frontend to dist/public and backend to dist/
        sh 'npm run build'
      }
    }

    stage('Archive Artifacts') {
      steps {
        archiveArtifacts artifacts: 'dist/**', fingerprint: true
      }
    }
  }

  post {
    success { echo '✅ Build complete. Artifacts archived from dist/**.' }
    failure { echo '❌ Build failed. See logs above.' }
  }
}
