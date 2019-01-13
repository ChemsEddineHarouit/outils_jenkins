pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        bat 'gradle build'
        bat 'gradle javadoc'
      }
    }
    stage('Mail-Notification') {
      steps {
        mail(subject: 'Jenkins Build', body: 'New Jenkins Pull hehe', to: 'fc_harouit@esi.dz ; fa_bouchebaba@esi.dz')
      }
    }
  }
}