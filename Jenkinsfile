def project = 'jmuldoon/jenkins-seed-test'
def branchApi = new URL("https://api.github.com/repos/${project}/branches")
def branches = new groovy.json.JsonSlurper().parse(branchApi.newReader())
branches.each {
  def branchName = it.name
  description("Pipeline => $project; branch=> $branchName")

  pipelineJob("${project}-${branchName}".replaceAll('/','-')) {
    triggers {
      githubPush()
    }
    definition {
      cpsScm {
        scm {
          git("git://github.com/${project}.git", branchName)
        }
        script('Jenkinsfile')
      }
    }
  }
}
