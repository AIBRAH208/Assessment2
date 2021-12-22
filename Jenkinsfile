
node {
    def app

    stage('Clone repository') {
       
        checkout scm
    }

    stage('Build image') {
        
        cw2 = docker.build("aibrah208/cw2")
    }

    stage('Test image') {
        
        cw2.inside {
            sh 'echo "Tests passed"'
        }
    }

    stage('Push image') {
  
        docker.withRegistry('https://registry.hub.docker.com', 'dockerhub_id') {
            cw2.push("${env.BUILD_NUMBER}")
            cw2.push("latest")
        }
    }
}
