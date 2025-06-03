pipeline {
    agent any
    tools {
        jdk "jdk-17.0.12"
        maven "maven-3.9.9"
    }
    stages {
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
                    personalAccessToken: '',
                    releaseId: '',
                    releaseName: 'Jenkins',
                    remediationScanPreferenceType: 'RemediationScanIfAvailable',
                    scanCentral: 'Maven',
                    scanCentralBuildCommand: '',
                    scanCentralBuildFile: 'pom.xml',
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