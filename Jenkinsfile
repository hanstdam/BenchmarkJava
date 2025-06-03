pipeline {
    agent any
    tools {
        jdk "jdk-17.0.12"
        maven "maven-3.9.9"
    }
    environment {
        PATH = "/var/jenkins_home/tools/hudson.tasks.Maven_MavenInstallation/maven-3.9.9/bin:${env.PATH}"
    }
    stages {
        // stage('Get ScanCentral') {
        //     steps {
        //         sh 'curl -L -o scancentral.zip http://192.168.1.123:3000/Fortify_ScanCentral_Client_Latest_x64.zip'
        //         sh 'mkdir -p /tmp/scancentral/'
        //         sh 'unzip scancentral.zip -d /tmp/scancentral/'
        //         sh 'ls /tmp/scancentral/'
        //     }
        // }
        stage('Get ScanCentral') {
            steps {
                sh 'echo $PATH'
            }
        }
        stage('Scan with Fortify On Demand') {
            steps {
                fodStaticAssessment applicationName: 'SCM_Benchmark',
                    applicationType: '1',
                    assessmentType: '-1',
                    attributes: '',
                    auditPreference: '2',
                    bsiToken: '',
                    businessCriticality: '1',
                    entitlementId: '',
                    entitlementPreference: '',
                    frequencyId: '',
                    inProgressBuildResultType: 'FailBuild',
                    inProgressScanActionType: 'Queue',
                    isMicroservice: false,
                    languageLevel: '34',
                    microserviceName: '',
                    openSourceScan: 'false',
                    overrideGlobalConfig: false,
                    owner: 112645,
                    personalAccessToken: '',
                    releaseId: '',
                    releaseName: 'Jenkins',
                    remediationScanPreferenceType: 'RemediationScanIfAvailable',
                    scanCentral: 'Maven',
                    scanCentralBuildCommand: '',
                    scanCentralBuildFile: '',
                    scanCentralBuildToolVersion: '',
                    scanCentralExcludeFiles: '',
                    scanCentralIncludeTests: '',
                    scanCentralRequirementFile: '',
                    scanCentralSkipBuild: '',
                    scanCentralVirtualEnv: '',
                    sdlcStatus: '3',
                    srcLocation: '',
                    technologyStack: '7',
                    tenantId: '',
                    username: ''
            }
        }
    }
}