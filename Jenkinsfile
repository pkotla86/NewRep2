node('built-in') {
    
    stage('ContinuousDownload') {
        git 'https://github.com/intelliqittrainings/maven.git'
    }
    
    stage('ContinuousBuild') {
        sh 'mvn package'
    }

    stage('ContinuousDeployment') {
        deploy adapters: [tomcat9(credentialsId: '33576e2b-827b-4f54-ae25-19bfa3dfeab3', path: '', url: 'http://43.204.141.154:8080')], contextPath: 'TestApp', war: '**/*.war'
    }

    stage('ContinuousTesting') {
        git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
        sh 'java -jar /home/ubuntu/.jenkins/workspace/ScriptedPipeline/testing.jar'
    }

    stage('ContinuousDelivery') {
        deploy adapters: [tomcat9(credentialsId: '33576e2b-827b-4f54-ae25-19bfa3dfeab3', path: '', url: 'http://172.31.0.184:8080')], contextPath: 'ProdApp', war: '**/*.war'
    }
    
}
