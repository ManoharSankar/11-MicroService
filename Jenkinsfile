pipeline {
    agent any

    stages {
        stage('Deploy to Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[
			caCertificate: '', 
			clusterName: 'EKS-1', 
			contextName: '', 
			credentialsId: 'k8-token', 
			namespace: 'webapps', 
			serverUrl: 'https://1D4F691F654103AC1783499A63BB0C83.gr7.ap-south-1.eks.amazonaws.com'
		]]) {
                    	sh 'kubectl apply -f deployment-service.yml' // our main branch file
                } 
            }
        }

        stage('Verify deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[
                    caCertificate: '', 
                    clusterName: 'EKS-1', 
                    contextName: '', 
                    credentialsId: 'k8-token', 
                    namespace: 'webapps', 
                    serverUrl: 'https://1D4F691F654103AC1783499A63BB0C83.gr7.ap-south-1.eks.amazonaws.com'
		]]) {
                    sh 'kubectl get svc -n webapps'
                } 
            }
        }
    }
}
