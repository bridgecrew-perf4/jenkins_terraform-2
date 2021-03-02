pipeline {
  agent {
    kubernetes {
      yamlFile 'KubernetesPod.yaml'
      #defaultContainer 'maven'
    }
  }
  stages {
    stage('Run maven') {
      steps {
        sh 'set'
        sh 'hostname  && echo $HOSTNAME'
        sh "echo OUTSIDE_CONTAINER_ENV_VAR = ${CONTAINER_ENV_VAR}"
        container('maven') {
          sh 'echo MAVEN_CONTAINER_ENV_VAR = ${CONTAINER_ENV_VAR}'
          sh 'mvn -version'
          sh "echo Workspace dir is ${pwd()}"
          sh 'ls -l $WORKSPACE'
        }
        container('busybox') {
          sh 'echo BUSYBOX_CONTAINER_ENV_VAR = ${CONTAINER_ENV_VAR}'
         // sh '/bin/busybox'
        }
      }
    }
  }
}
