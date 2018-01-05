def project = 'jmuldoon/jenkins-seed-test'
def branchApi = new URL("https://api.github.com/repos/${project}/branches")
def branches = new groovy.json.JsonSlurper().parse(branchApi.newReader())
branches.each {
  def branchName = it.name
  pipelineJob("${project}-${branchName}".replaceAll('/','-')) {
    definition {
      cpsScm {
        scm {
          git("git://github.com/${project}.git", branchName)
        }
        script(readFileFromWorkspace('Jenkinsfile.groovy'))
      }
    }
  }
}
