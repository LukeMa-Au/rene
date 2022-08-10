pipeline {
    agent any

    stages {
        stage('Upload to AWS') {
              steps {
                  withAWS(region:'ap-southeast-2',credentials:'luke_task') {
                     sh 'echo "Uploading content with AWS creds"'
                     sh 'aws s3 ls'
                     sh 'aws s3 cp ./website s3://renes3test/ --recursive'
                  }
              }
         }
    }
}
