
pipeline {
  agent { docker 'undera/taurus' } 

  stages {
    stage('Hello') {
      steps {
        echo 'Hello World'
      }
    }


    stage('Example Build') {
      steps {

        sh 'ls'
        sh 'bzt quick_test.yml'
      }
    }



    stage("Process JTL logs") {
      steps{
        println "Test processing logs"
        /*
         * Use the Performance Plugin to process the .jtl log file.
         */

        performanceReport compareBuildPrevious: true,
      sourceDataFiles:  'artifacts/*.jtl, artifacts/*.jtl',
      configType: 'ART',
      errorFailedThreshold: 100,
      errorUnstableResponseTimeThreshold: '',
      errorUnstableThreshold: 100,
      failBuildIfNoResultFile: false,
      modeOfThreshold: false,
      modePerformancePerTestCase: true,
      modeThroughput: true,
      nthBuildNumber: 0,
      parsers: [[$class: 'JMeterParser', glob: '**/*.jtl']]

      }
    }

    stage("Archive log files") {
      steps{
        archiveArtifacts '**/*.jtl, **/*.log'
      }
    }

    stage("Cleanup") {
      steps{
        // Wipe the workspace so we are building completely clean
        deleteDir()
      }
    }
  }

}
