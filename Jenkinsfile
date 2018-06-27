#!groovy

pipeline {
  agent none
  stages {
    stage('Maven Install') {
      agent {
        docker {
          image 'maven:3.5.0'
        }
      }
      steps {
        sh 'mvn clean install'
      }
    } 
    stage('Docker Build') {
      agent any
      steps {
        sh 'docker build -t autoopsltd/spring-petclinic:latest .'
      }
    }
    stage('Docker Push') {
      agent any
      steps {
        sh 'docker tag autoopsltd/spring-petclinic:latest localhost:5000/autoopsltd/spring-petclinic:latest'
        sh 'docker push localhost:5000/autoopsltd/spring-petclinic:latest'
      }
    }
  }
}
