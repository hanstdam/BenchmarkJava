pipeline {
    agent any
    tools {
        jdk "jdk-17.0.12"
        maven "maven-3.9.9"
    }
    environment {
        FOD_TRACE = 'true'
        PATH = "$HOME/fortify/tools/bin:$PATH"
    }
    stages {
        // stage('Get ScanCentral') {
        //     steps {
        //         script {
        //             if (!fileExists('/tmp/scancentral/bin/scancentral')) {
        //                 sh 'curl -L -o scancentral.zip http://192.168.1.123:3000/Fortify_ScanCentral_Client_Latest_x64.zip'
        //                 sh 'mkdir -p /tmp/scancentral/'
        //                 sh 'unzip scancentral.zip -d /tmp/scancentral/'
        //                 sh 'ls /tmp/scancentral/'
        //                 sh 'chmod +x /tmp/scancentral/bin/scancentral'
        //             }
        //         }
        //     }
        // }
        // stage('Environment Variables') {
        //     steps {
        //         sh 'echo $PATH'
        //         sh 'echo $M2'
        //         sh 'echo $M2_HOME'
        //         sh 'echo $MAVEN_HOME'
        //         sh 'echo $JAVA_HOME'
        //     }
        // }
        stage('Install fcli and scancentral') {
            steps {
                sh """
                    curl -L https://github.com/fortify/fcli/releases/download/latest/fcli-linux.tgz | tar -xz fcli
                    ./fcli --version
                    ./fcli tool sc-client install
                    scancentral --version
                """
            }
        }
        // stage('ScanCentral package') {
        //     steps {
        //         sh """
        //             scancentral package -bt mvn -bf pom.xml -o Package.zip
        //         """
        //     }
        // }
        stage('Scan with Fortify On Demand') {
            steps {
                fodStaticAssessment applicationName: 'SCM_Benchmark',
                    applicationType: '1',
                    assessmentType: '274',
                    // attributes: '',
                    auditPreference: '2',
                    // bsiToken: '',
                    businessCriticality: '1',
                    entitlementId: '13916',
                    // entitlementPreference: '',
                    frequencyId: '2',
                    inProgressBuildResultType: 'FailBuild',
                    inProgressScanActionType: 'Queue',
                    isMicroservice: false,
                    languageLevel: '34',
                    // microserviceName: '',
                    openSourceScan: 'false',
                    overrideGlobalConfig: false,
                    owner: 112645,
                    // personalAccessToken: '',
                    releaseId: '1495949',
                    releaseName: 'Jenkins',
                    remediationScanPreferenceType: 'NonRemediationScanOnly',
                    scanCentral: 'Maven',
                    // scanCentralBuildCommand: '-debug',
                    // scanCentralBuildFile: '',
                    // scanCentralBuildToolVersion: '',
                    // scanCentralExcludeFiles: '',
                    // scanCentralIncludeTests: '',
                    // scanCentralRequirementFile: '',
                    // scanCentralSkipBuild: 'true',
                    // scanCentralVirtualEnv: '',
                    sdlcStatus: '3',
                    // srcLocation: 'Package.zip',
                    technologyStack: '7'
                    // tenantId: '',
                    // username: ''
            }
        }
        stage('Get Results From Fortify On Demand') {
            steps {
                fodPollResults bsiToken: '',
                    pollingInterval: 2,
                    releaseId: '1495949'
            }
        }
    }
    post {
        always {
            script {
                if (fileExists("$HOME/.fortify/scancentral-24.4.1/log/launcher.log")) {
                    sh "cat $HOME/.fortify/scancentral-24.4.1/log/launcher.log"
                }
                if (fileExists("$HOME/.fortify/scancentral-24.4.1/log/scancentral.log")) {
                    sh "cat $HOME/.fortify/scancentral-24.4.1/log/scancentral.log"
                }

                sh "rm $HOME/.fortify/scancentral-24.4.1/log/*.log"
            }
        }
    }
}