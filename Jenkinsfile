pipeline {
    agent {
        node {
            label 'master'
        }
    }

    stages {
        
    

 //           sh 'git log HEAD^..HEAD --pretty="%h %an - %s" > GIT_CHANGES'
 //           def lastChanges = readFile('GIT_CHANGES')
//            slackSend color: "warning", message: "Started `${env.JOB_NAME}#${env.BUILD_NUMBER}`\n\n_The changes:_\n${lastChanges}"

        stage ('Test'){
            sh 'virtualenv env -p python3'
            sh '. env/bin/activate'
            sh 'env/bin/pip install -r requirements.txt'
            sh 'env/bin/python3 manage.py test --testrunner=djtrump.tests.test_runners.NoDbTestRunner'
        }
        stage ('Deploy'){
            sh './deployment/deploy_prod.sh'
        }
//        stage 'Publish results'
 //           slackSend color: "good", message: "Build successful: `${env.JOB_NAME}#${env.BUILD_NUMBER}` <${env.BUILD_URL}|Open in Jenkins>"
    }

}
