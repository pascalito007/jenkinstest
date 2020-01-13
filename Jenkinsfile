pipeline {
     agent any
     stages {
         stage('Build') {
             steps {
                 sh 'echo "Hello World"'
                 sh '''
                     echo "Multiline shell steps works too"
                     ls -lah
                 '''
             }
         }
         stage('Lint HTML') {
              steps {
                  sh 'tidy -q -e *.html'
              }
         }
         stage('Security Scan') {
              steps { 
                 aquaMicroscanner imageName: 'alpine:latest', notCompliesCmd: 'exit 1', onDisallowed: 'fail', outputFormat: 'json'
              }
         }
        //  stage('AWS Credentials'){
        //     steps{
        //         withCredentials([[
        //             $class: 'AmazonWebServicesCredentialsBinding',
        //             credentialsId: '828370275182',
        //             accessKeyVariable: 'AWS_ACCESS_KEY_ID',
        //             secretKeyVariable: 'AWS_SECRET_ACCESS_KEY'
        // ]])
        //         {
        //             mkdir -p ~/.aws
        //             echo '[default]' >~/.aws/credentials
        //             echo '[default]' >~/.boto
        //             echo 'AWS_ACCESS_KEY_ID=${AWS_ACCESS_KEY_ID}'>>~/.boto 
        //             echo 'AWS_SECRET_ACCESS_KEY=${AWS_SECRET_ACCESS_KEY}'>>~/.boto
        //             echo 'AWS_ACCESS_KEY_ID=${AWS_ACCESS_KEY_ID}'>> ~/.aws/credentials
        //             echo 'AWS_SECRET_ACCESS_KEY=${AWS_SECRET_ACCESS_KEY}'>>~/.aws/credentials
        //         }
        //     }
        //  }         
         /*stage('Upload to AWS') {
              steps {
                  withAWS(region:'us-east-2',credentials:'aws-static') {
                  sh 'echo "Uploading content with AWS creds"'
                      s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'static-jenkins-pipeline')
                  }
              }
         }*/
     }
}
