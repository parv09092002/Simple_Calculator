pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        deleteDir() // Optional: Clear workspace
        git branch: 'main', url:'https://github.com/parv09092002/Simple_Calculator.git'
      }
    }

    stage('Install Dependencies') {
      steps {
        // Using 'sh' for Unix-based environment (macOS)
        sh 'pip3 install -r requirements.txt'
      }
    }

    stage('Build') {
      steps {
        // Build steps here
        echo 'Running calculator script...'
        sh 'python3 calculator.py 1 10 20' // Passes the operation and numbers as argument
      }
    }

    stage('Test') {
      steps {
        // Test steps here
        script {
          // Continue to the next stage even if tests fail
          catchError(buildResult: 'UNSTABLE', stageResult:'FAILURE') {
            echo 'Running unit tests...'
            sh 'pytest --maxfail=1 --disable-warnings'
          }
        }
      }
    }

    stage('Deploy') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'github-credentials', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
          sh """
            npm install -g --silent gh-pages@2.1.1
            git config user.email "ICT_Patodia.Parv@connect.np.edu.sg"
            git config user.name "parv09092002"
            gh-pages --dotfiles --message '[skip ci] Updates' --dist build
          """
        }
      }
    }
  }

  // The post block should be at the same level as 'stages'
  post {
    success {
      echo 'Build and test stages completed successfully.'
    }
    failure {
      echo 'One or more stages failed. Check the logs for details.'
    }
  }
}
