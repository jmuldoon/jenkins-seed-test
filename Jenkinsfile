import javaposse.jobdsl.dsl.DslScriptLoader
import javaposse.jobdsl.plugin.JenkinsJobManagement

def jobDslScript = new File("#{node['jenkins']['master']['home']}/seed-github.groovy")
def workspace = new File('.')

def jobManagement = new JenkinsJobManagement(System.out, [:], workspace)

new DslScriptLoader(jobManagement).runScript(jobDslScript.text)