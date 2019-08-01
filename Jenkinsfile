pipeline {
  agent slave_1
  stages {
    stage('Build') {
     steps {
       echo "Running build automation"
       sh "./gradlew build --no-daemon"
       archiveArtifacts artifacts: 'dist/trainSchedule.zip'
     }
    }
  }
}
