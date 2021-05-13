pipeline {
    agent any
    stages {
        stage('Git') {
            steps {
                git url:'https://github.com/stephko1/PipelinReact.git', branch:'main'
                node('Mac') {
                    git url:'https://github.com/stephko1/PipelinReact.git', branch:'main'
                }
            }
        }
        stage('Statische Code Analyse'){
            parallel{
                stage('Code Analyse Android'){
                    steps{
                        dir("android"){
                            //bat "gradlew.bat -D'sonar.host.url=http://localhost:9000' sonarqube"
                        }
                    }
                }
                stage('Code Analyse iOS'){
                    steps{
                        //node('Mac') {
                            dir("ios"){
                                //sh '/usr/local/bin/fastlane update'
                                //sh '/home/ec2-user/.rvm/gems/ruby-2.5.9/wrappers/fastlane test'
                            }
                        //}
                    }
                }
            }
        }
        stage('Build & Sign'){
            parallel{
                stage('Build & Sign Android'){
                    steps{
                        dir("android"){
                            //bat 'C:/Ruby25-x64/bin/fastlane build build_number:$BUILD_NUMBER'
                        }
                    }
                }
                stage('Build & Sign iOS'){
                    steps{
                        //node('Mac') {
                            dir("ios"){
                                //sh '/usr/local/bin/fastlane build'
                            }
                        //}
                    }
                }
            }
        }
		stage('Tests'){
            parallel{
                stage('Test Android'){
                    steps{
                        dir("Android"){
                            //bat """ "C:/Users/steph/AppData/Local/Google/Cloud SDK/google-cloud-sdk/bin/gcloud" firebase test android run --type robo --app "./app/release/app-release.apk" --device-ids=flame --os-version-ids=30 """
                        }
                    }
                }
                stage('Test iOS'){
                    steps{
                        //node('Mac') {
                            dir("ios"){
                                //TEST
                            }
                        //}
                    }
                }
            }
        }
		stage('Alpha Deployment'){
            parallel{
                stage('Alpha Android'){
                    steps{
                        dir("Android"){
							//bat 'C:/Ruby25-x64/bin/fastlane internal'
                            //bat 'C:/Ruby25-x64/bin/fastlane alpha'
                        }
                    }
                }
                stage('Alpha iOS'){
                    steps{
                        //node('Mac') {
                            dir("ios"){
                                //sh '/usr/local/bin/fastlane alpha'
                            }
                        //}
                    }
                }
            }
        }
		stage('Beta Deployment'){
            parallel{
                stage('Beta Android'){
                    input {
                        message "Deploy Betaversion?"
                        ok "Yes"
                    }
                    steps{
                        dir("Android"){
                            //bat 'C:/Ruby25-x64/bin/fastlane beta'
                        }
                    }
				}
				stage('Test iOS'){
                    input {
                        message "Deploy Betaversion?"
                        ok "Yes"
                    }
                    steps{
						//node('Mac') {
							dir("ios"){
								//sh 'sudo /usr/local/bin/fastlane beta'
							}
						//}
                    }
                }
            }
        }
		stage('Store Deployment'){
            parallel{
                stage('Store Android'){
                    input {
                        message "Deploy to Play Store?"
                        ok "Yes"
                    }
                    steps{
                        dir("Android"){
                            //bat 'C:/Ruby25-x64/bin/fastlane store'
                        }
                    }
				}
				stage('Store iOS'){
                    input {
                        message "Deploy to App Store?"
                        ok "Yes"
                    }
                    steps{
						//node('Mac') {
							dir("ios"){
								//sh 'sudo /usr/local/bin/fastlane store'
							}
						//}
                    }
                }
            }
        }
    }
}