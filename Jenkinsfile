pipeline {
  agent any

  stages {
    stage('Clone Repo') {
      steps {
        git 'https://github.com/your-username/static-site.git' // or use your own
      }
    }

    stage('Build Docker Image') {
      steps {
        script {
          docker.build('static-site:latest')
        }
      }
    }

    stage('Run Container') {
      steps {
        script {
          // Stop and remove if container already running
          sh 'docker rm -f static_site_container || true'
          // Run the new container on port 8085
          sh 'docker run -d --name static_site_container -p 8085:80 static-site:latest'
        }
      }
    }
  }
}
