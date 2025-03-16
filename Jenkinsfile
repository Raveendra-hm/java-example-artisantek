pipeline {
  agent {
       label 'maven'
   }
  environment {
    DB_USERNAME="root"
    DB_PASSWORD="root"
  }
  parameters {
  string defaultValue: 'dev', name: 'git_tag', trim: true
  booleanParam defaultValue: true, name: 'status'
  choice choices: ['dev', 'test', 'preprod'], name: 'branch'
  }
stages {
  stage('git_checkout') {
    steps {
      git branch: 'main', url: 'https://github.com/Raveendra-hm/java-example-artisantek.git'  
    }
  }

  stage('test_stage') {
    environment { 
      DB_HOST="172.30.26.35"
      DB_NAME="mysql"
    }
    steps {
      echo "this is just for testing purpose !! !"
      echo "$PATH"
      echo "$DB_HOST, $DB_NAME, $DB_USERNAME, $DB_PASSWORD "
      echo "this is the jenkins URL:${env.JENKINS_URL}" 
    }
  }

  stage('build_stage') {
    steps {
      sh 'mvn clean package'

    }
  }

  stage('deploy_stage') {
    steps {
      sh 'sudo cp target/*.war /opt/tomcat/apache-tomcat-9.0.68/webapps/'
      echo "this is the latest change to trigger through github webhook"
    }
  }

 }
}

