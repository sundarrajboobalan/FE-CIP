pipeline
{
    agent any
    environment
    {
        registry='sundarrajboobalan/niqdemo'
        dockerImage=''
        registryCredential='dockerhub-id'
    }
    stages
    {
        stage('Checkout from Github')
        {
            steps
            {
              checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/sundarrajboobalan/FE-CIP.git']])  
            }
            
        }
        stage('Build Docker Image')
        {
            steps
            {
                script
                {
                    dockerImage=docker.build registry
                }
            }
        }
        stage('Push the image in to Dockerhub')
        {
            steps
            {
                script
                {
                    docker.withRegistry('',registryCredential)
                    {
                        dockerImage.push()
                    }
                }
            }
        }
    }
}
