#!groovy

pipeline {

  agent any

  environment {
    git_commit_message = ''
    git_commit_diff = ''
    git_commit_author = ''
    git_commit_author_name = ''
    git_commit_author_email = ''
  }

  stages {

    // Build
    stage('Clone') {
      steps {
        sh "git clone https://github.com/preetambor/iperf.git"
        }
    }

    // Static Code Analysis
    stage('Configure') {
      steps {
        sh "cd iperf"
        sh "./configure"
      }
    }

    // Unit Tests
    stage('Make') {
      steps {
        sh "make"
      }
    }


  }
  post {
    success {
      sh "echo 'Send mail on success'"
      // mail to:"me@example.com", subject:"SUCCESS: ${currentBuild.fullDisplayName}", body: "Yay, we passed."
    }
    failure {
      sh "echo 'Send mail on failure'"
      // mail to:"me@example.com", subject:"FAILURE: ${currentBuild.fullDisplayName}", body: "Boo, we failed."
    }
  }
}