pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        bat 'gradle build'
        bat 'gradle javadoc'
        archiveArtifacts 'build/libs/*.jar'
        archiveArtifacts 'build/docs/javadoc/*.*'
      }
    }
    stage('Mail-Notification') {
      steps {
        mail(subject: 'Jenkins Build', body: 'New Jenkins Pull hehe', to: 'fa_bouchebaba@esi.dz ; fc_harouit@esi.dz')
      }
    }
    stage('CodeCheck') {
      parallel {
        stage('CodeAnalysis') {
          steps {
            echo 'analyse'
          }
        }
        stage('Test Reporting') {
          steps {
            jacoco()
          }
        }
      }
    }
    stage('Deployment') {
      when{
        branch 'master'
      }
      steps {
        bat 'gradle uploadArchives'
      }
    }
    stage('Slack-Notification') {
      when{
        branch 'master'
      }
      steps {
        slackSend(message: 'Deploiement effectué lkhawa')
      }
    }
  }
}
