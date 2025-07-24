node {
    def app
        stage('Clone') {
            checkout scm
        }
        stage('Build image') {
            app = docker.build("xavi/nginx")
        }
        stage('Test image') {
            docker.image('xaviki/nginix').withRun('-p 80:80') { c ->
                sh 'docker ps'
                sh 'curl localhost'
            }
        }
}
