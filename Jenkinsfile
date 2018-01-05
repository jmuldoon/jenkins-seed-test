import javaposse.jobdsl.dsl.DslScriptLoader
import javaposse.jobdsl.plugin.JenkinsJobManagement

def jenkinsHome = '/var/lib/jenkins'
def jobDslScript = new File(jenkinsHome+"/seed-github.groovy")
def workspace = new File('.')

def jobManagement = new JenkinsJobManagement(System.out, [:], workspace)

new DslScriptLoader(jobManagement).runScript(jobDslScript.text)