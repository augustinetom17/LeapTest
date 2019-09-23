pipeline {
	agent any
	parameters {
		string(defaultValue: "TEST", description: 'Enter the IP: ?', name: 'ServerIP')
		}
	stages {
		stage ('Clean Workspace') {
			steps {
				cleanWs()
			}
		}
		stage ('GitDownload') {
			steps {
				git 'https://github.com/augustinetom17/LeapTest.git'
			}
		}
		stage ('Deploy') {
			steps {
				sh '''
				ssh root@${ServerIP} rm -rf /var/test
				ssh root@${ServerIP} mkdir /var/test
				scp -r * root@${ServerIP}:/var/test
				'''
			}
		}
	}
}