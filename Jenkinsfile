pipeline
{
    agent any
    environment
    {
        registry='sundarrajboobalan/project3'
        dockerImage=''   
         registryCredential ='dockerhub' //credential name
        }
    stages
    {
        stage('checkout')
        {
            steps
            {
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/sundarrajboobalan/FE-CIP.git']])
            }
        
            
        }
        
        stage('Build docker image')
        {
            steps
            {
                script
                {
                    dockerImage = docker.build registry
                }
            }
        }
    stage('Push docker image')
{
    steps
    {
        script
        {
            docker.withRegistry( '', registryCredential ) 
            {
            dockerImage.push()
        }
    }
}        
    }
    }
}




      
               
