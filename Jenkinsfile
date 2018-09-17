pipeline 
{
    agent any
    stages 
    {
        stage('Build') 
        {
            steps 
                {
                    echo 'Building..'
                    git url: 'https://github.com/mohanjaws/simple-java-maven-app.git'
				}
        }
		stage('Jira') 
		{
			
		}
        stage('Test') 
        {
            steps 
                {
                    echo 'Testing..'
                }
        }
        stage('Deploy') 
        {
            steps 
                {
                    echo 'Deploying....'
                    sh '/home/tomcat/tomcat9/bin/jenkinscd.sh'
                }
        }
        stage('Notify') 
        {
            steps 
                {
                    echo 'Notifying....'
                    slackSend color: 'good', message: 'Deployment is Success!', channel: '#proj-testpipe'
                }
        }
    }    
}
