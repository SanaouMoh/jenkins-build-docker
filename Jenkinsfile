node {
<<<<<<< HEAD
    def registryProjet='ghcr.io/sanaoumoh/presentations-jenkins'
    def IMAGE="${registryProjet}:version-${env.BUILD_ID}"
	
	echo "IMAGE = $IMAGE"
	
    stage('Clone') {
        chechout scm
    }

    def img = stage('Build') {
        docker.build("$IMAGE", '.')
    }
    
    stage('Run') {
        img.withRun("--name run-$BUILD_ID -p 80:80") { c ->
            sh 'curl 172.17.0.1:80'
        }
    }

    stage('Push') {
        docker.withRegistry('https://ghcr.io', 'github-push-pat') {
            img.push 'latest'
            img.push()
        }
    }
=======
    def app
        stage('Clone') {
            checkout scm
        }
        stage('Build image') {
            app = docker.build("xavki/nginx")
        }
        stage('Test image') {
            docker.image('xavki/nginx').withRun('-p 80:80') { c ->
                sh 'docker ps'
                sh 'curl 172.17.0.1:80'
            }
        }
>>>>>>> 702ec12ba46dc595ca54155bb3ec63500754b0d1
}
