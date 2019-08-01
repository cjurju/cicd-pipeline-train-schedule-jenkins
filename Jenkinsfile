pipeline {
  agent any
  stages {
    stage('Build') {
     steps {
       echo "Running build automation"
       sh "./gradlew build --no-daemon"
       archiveArtifacts artifacts: 'dist/trainSchedule.zip'
     }
    }
    stage('DeployToStaging') {
      when {
        branch 'master'
      }
      steps {
        sshPublisher(
          failOnError: true,
          continueOnError: false,
          publishers: [
            sshPublisherDesc(
              configName: 'staging',
              sshCredentials: [
                username: 'jenkins',
                Passphrase: 'jenkins'
              ]
            )
          ]
        )
      }
    }
  }
}
