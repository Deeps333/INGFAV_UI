pipeline {
   agent any
	stages {
      stage('SCM Checkout') {
         steps {
            git 'https://github.com/Deeps333/INGFAV_UI.git'
		}
	}
	stage('Build') {
		steps {
			sh '''
			npm install
			npm run build
			npm audit fix
			'''
		}
	}
	stage ('Deploy') {
		steps {
			sh '''
             cp -r $WORKSPACE/build /apache-tomcat-9.0.31/webapps
             curl -u admin:admin http://15.206.160.22:8888/manager/reload?path=/build 
             '''
		}
	}
}
}
