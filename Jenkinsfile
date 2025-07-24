node {
    def registryProjet='ghcr.io/sanaoumoh/presentations-jenkins'
    def IMAGE="${registryProjet}:version-${env.BUILD_ID}"
	
	echo "IMAGE = $IMAGE"
	
    stage('Clone') {
        checkout scm
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
}
