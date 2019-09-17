pipeline {
	agent any
	parameters {
		choice (
			name: 'ServerIP'
			choices: "192.168.20.172\n192.168.20.165"
			description: 'Server IPs to deploy' )
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
				ssh root@$ServerIP rm -rf /var/test
				ssh root@$ServerIP mkdir /var/test
				scp -r * root@$ServerIP:/var/test
				'''
			}
		}
	}
}
			