pipeline{
    agent{
        label "nodejs"
    }
    stages{
        stage("Install dependencies"){
            steps{
                sh "npm ci"
            }
        }

        stage("Check Style"){
            steps{
                sh "npm run lint"
            }
        }

        stage("Test"){
            steps{
                sh "npm test"
            }
        }
stage("Release"){
	steps {
	sh '''
        oc project eawiyl-greetings
	oc start-build greeting-console --follow --wait
	'''
}
} 

stage("NEWAPP"){
	steps {
	sh '''
        oc project eawiyl-greetings
	oc new-app --docker-image quay.io/redhattraining/hello-world-nginx:v1.0 --name hello
	'''
}
} 
    }
}
