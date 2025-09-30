pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
         sh 'chmod a+x run_build_script.sh'
         sh './run_build_script.sh'
      }
    }
    stage('Test') {
      parallel{
        stage('Test On Windows'){
          echo 'Running test on Windows'
        }
        stage('Test On Linux'){
          steps{
            echo "Running test on Linux"
          }
        }
      }
    }
  }
}
