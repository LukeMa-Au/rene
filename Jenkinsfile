node {
   // ...
   withAwsCli( 
         credentialsId: 'aws-key', 
         defaultRegion: 'ap-southeast-2c') { 

        sh ''' 
           # COPY CREATED WAR FILE TO AWS S3
           aws s3 cp target/petclinic.war s3://cloudbees-aws-demo/petclinic.war
           # CREATE A NEW BEANSTALK APPLICATION VERSION BASED ON THE WAR FILE LOCATED ON S3
           aws elasticbeanstalk create-application-version \
              --application-name petclinic \
              --version-label "jenkins$BUILD_DISPLAY_NAME" \
              --description "Created by $BUILD_TAG" \
              --source-bundle=S3Bucket=cloudbees-aws-demo,S3Key=petclinic.war
           # UPDATE THE BEANSTALK ENVIRONMENT TO CREATE THE NEW APPLICATION VERSION
           aws elasticbeanstalk update-environment \
              --environment-name=petclinic-qa-env \
              --version-label "jenkins$BUILD_DISPLAY_NAME"
        '''
   }
}
