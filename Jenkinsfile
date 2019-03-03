node(){
	stage("Checkout SCM")
      checkout scm
	stage("Build Code"){
        def mvnHomePath = tool name: 'Maven3', type: 'maven'
		sh "${mvnHomePath}/bin/mvn clean install"  
      }
	stage("Sonar Scan"){
      def sonar = tool name: 'SonarQube', type: 'hudson.plugins.sonar.SonarRunnerInstallation'
      sonar = "${sonar}/bin/sonar-scanner"
	  sh "${sonar} -Dsonar.projectKey=ecomm.sandbox.demo -Dsonar.projectName=ECOMM-SANDBOX-DEMO -Dsonar.projectVersion=1.0 -Dsonar.sources=. -Dsonar.java.binaries=. -Dsonar.login=530811fc4f2aee680b6a85b1b00f646177cf8222 -Dsonar.host.url=https://plsandbox.pl.s2-eu.capgemini.com/sonarqube/"
	}
	/*stage("Build Docker Image"){
        def dockercmd = tool name: 'docker_test', type: 'org.jenkinsci.plugins.docker.commons.tools.DockerTool'
        sh "${dockercmd} docker build -t gauraw10/e-comm-sandbox:1.0 ."
        docker.build("sonar-sanbox")
    }
	stage("Docker Push Image"){
		withCredentials([string(credentialsId: 'dockerhub-pwd', variable: 'dockerlogin')]) {
			sh "docker login -u gauraw10 -p ${dockerlogin}"
			sh 'docker push gauraw10/e-comm-sandbox:1.0'
	}
	stage("Docker Run Image"){
        def dockercmd = tool name: 'docker_test', type: 'org.jenkinsci.plugins.docker.commons.tools.DockerTool'
        sh "${dockercmd} docker build -t sonar-sanbox -f Dockerfile ."
        docker.build("sonar-sanbox")
    }*/
	
}