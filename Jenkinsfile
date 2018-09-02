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
			def testIssue = [fields: 
			[ 
                project: [id: 'PT'],
                summary: 'New JIRA Created from Jenkins.',
                description: 'New JIRA Created from Jenkins.',
                customfield_1000: 'customValue',
                issuetype: [id: '3']]]
				response = jiraEditIssue idOrKey: 'TEST-01', issue: testIssue
				echo response.successful.toString()
				echo response.data.toString()
	
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
