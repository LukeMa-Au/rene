pipeline {
    agent any

    stages {
        stage('Upload to AWS') {
              steps {
                  withAWS(region:'ap-southeast-2',credentials:'luke_task') {
                     sh 'echo "Uploading content with AWS creds"'
                     sh 'echo "Installing aws cli"'
                     sh 'aws s3 cp /var/lib/jenkins/workspace/s3_test/home-page.html s3://renes3test/ --recursive'
                  }
              }
         }
    }
}
