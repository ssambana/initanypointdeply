pipeline {

  agent any
  environment {
    //adding a comment for the commit test
    //DEPLOY_CREDS = credentials('deploy-anypoint-user')
    MULE_VERSION = '4.4.0'
    BG = "university of Westminister"
    WORKER = "Micro"
	USERNAME = "ssambana180391"
	PASSWORD = "Whish@2021"
  }
  stages {
    stage('Build') {
      steps {
            sh 'mvn -B -U -e -V clean -DskipTests package'
      }
    }

    stage('Test') {
      steps {
          sh "mvn test"
      }
    }

     stage('Deploy Development') {
      environment {
        ENVIRONMENT = 'Sandbox'
        APP_NAME = 'sampledeployment'
      }
      steps {
            sh 'mvn -U -V -e -B -DskipTests deploy -DmuleDeploy -Dmule.version="%MULE_VERSION%" -Dusername="%USERNAME%" -Dpassword="%PASSWORD%" -Danypoint.username="%DEPLOY_CREDS_USR%" -Dcloudhub.app="%APP_NAME%" -Dcloudhub.environment="%ENVIRONMENT%" -Dcloudhub.bg="%BG%" -Dcloudhub.worker="%WORKER%"'
      }
    }
  }
}