pipeline {
  agent any
  stages {
    stage('Upload to AWS') {
      steps {
        sh 'echo "Hello World"'
        sh '''
                     echo "Multiline shell steps works too"
                     ls -lah
                 '''
      }
      steps {
        withAWS(region:'us-west-2',credentials:'aws-static') {
          sh 'echo "Uploading content with AWS credentials"'
          s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'udacity-jenkins-s3-project')
        }
      }
    }
  }
}
