node {
  node {
  job {
    using 'TMPL-test'
    name 'PROJ-unit-tests'
    scm {
      git('https://github.com/Stackato-Apps/pet-store')
    }
    triggers {
      scm('*/15 * * * *')
    }
    steps { // build step
      maven('-e clean test')
    }
  }
  
  def project = 'quidryan/aws-sdk-test'
  def branchApi = new URL("https://api.github.com/repos/${project}/branches")
  def branches = new groovy.json.JsonSlurper().parse(branchApi.newReader())
  branches.each {
    def branchName = it.name
    job {
      name "${project}-${branchName}".replaceAll('/','-')
      scm {
        git("git://github.com/${project}.git", branchName)
      }
      steps {
        maven("test -Dproject.name=${project}/${branchName}")
      }
    }
  }
  
  stage('Build') {
    echo 'Building..'    
  }
  stage('Test') {
    echo 'Testing..'
    sh 'whoami'
  }
  stage('Deploy') {
    echo 'Deploying....'
  }
}


  stage('Build') {
    echo 'Building..'    
  }
  stage('Test') {
    echo 'Testing..'
    sh 'whoami'
  }
  stage('Deploy') {
    echo 'Deploying....'
  }
}
