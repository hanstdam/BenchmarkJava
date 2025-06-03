pipeline {
    agent any
    tools {
        jdk "jdk-17.0.12"
        maven "maven-3.9.9"
    }
    stages {
        stage('Get ScanCentral') {
            steps {
                script {
                    if (!fileExists('/tmp/scancentral/bin/scancentral')) {
                        sh 'curl -L -o scancentral.zip http://192.168.1.123:3000/Fortify_ScanCentral_Client_Latest_x64.zip'
                        sh 'mkdir -p /tmp/scancentral/'
                        sh 'unzip scancentral.zip -d /tmp/scancentral/'
                        sh 'ls /tmp/scancentral/'
                    }
                }
            }
        }
        stage('Environment Variables') {
            steps {
                sh 'echo $PATH'
                sh 'echo $M2'
                sh 'echo $M2_HOME'
                sh 'echo $MAVEN_HOME'
                sh 'echo $JAVA_HOME'
            }
        }
        stage('Scan with Fortify On Demand') {
            steps {
                fodStaticAssessment applicationName: 'SCM_Benchmark',
                    applicationType: '1',
                    assessmentType: '-1',
                    // attributes: '',
                    auditPreference: '2',
                    // bsiToken: '',
                    businessCriticality: '1',
                    // entitlementId: '',
                    // entitlementPreference: '',
                    // frequencyId: '',
                    inProgressBuildResultType: 'FailBuild',
                    inProgressScanActionType: 'Queue',
                    isMicroservice: false,
                    languageLevel: '34',
                    // microserviceName: '',
                    openSourceScan: 'false',
                    overrideGlobalConfig: false,
                    owner: 112645,
                    // personalAccessToken: '',
                    // releaseId: '',
                    releaseName: 'Jenkins',
                    remediationScanPreferenceType: 'RemediationScanIfAvailable',
                    scanCentral: 'Maven',
                    // scanCentralBuildCommand: '',
                    // scanCentralBuildFile: '',
                    // scanCentralBuildToolVersion: '',
                    // scanCentralExcludeFiles: '',
                    // scanCentralIncludeTests: '',
                    // scanCentralRequirementFile: '',
                    // scanCentralSkipBuild: '',
                    // scanCentralVirtualEnv: '',
                    sdlcStatus: '3',
                    srcLocation: '',
                    technologyStack: '7'
                    // tenantId: '',
                    // username: ''
            }
        }
    }
    post {
        always {
            script {
                if (fileExists('/var/jenkins_home/.fortify/scancentral-24.4.1/log/launcher.log')) {
                    sh 'cat /var/jenkins_home/.fortify/scancentral-24.4.1/log/launcher.log'
                }
                if (fileExists('/var/jenkins_home/.fortify/scancentral-24.4.1/log/scancentral.log')) {
                    sh 'cat /var/jenkins_home/.fortify/scancentral-24.4.1/log/scancentral.log'
                }

                sh 'rm /var/jenkins_home/.fortify/scancentral-24.4.1/log/*.log'
            }
        }
    }
}