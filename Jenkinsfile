pipeline {
  agent linux-agent
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
          steps{
            echo 'Running test on Windows'
          }
        }
        stage('Test On Linux'){
          steps{
            echo "Running test on Linux"
          }
        }
      }
    }
    stage('Confirm Deploy to staging'){
      steps{
        timeout(time: 60, unit: 'SECONDS'){
          input(message: 'Okay to Deploy?', ok: 'Let\'s Do it!')
        }
      }
    }
    stage('Deploy to staging'){
      steps{
        echo "Deploying to staging..."
      }
    }
    stage('Confirm Deploy to production'){
      steps{
        timeout(time: 60, unit: 'SECONDS'){
          input(message: 'Okay to Deploy?', ok: 'Let\'s Do it!')
        }
      }
    }
    stage('Deploy to production'){
      steps{
        echo "Deploying to production..."
      }
    }
  }
  post{
    success{
      //notification on success
      echo 'build succeeded'
    }
    failure{
      // notification on failure
      echo 'Build failed'
    }
  }
}
