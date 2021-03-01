# jclean 
## Disclaimer 
I made this in less than an hour, its very helpful but not perfect or to be trusted.
If you have for some reason declared a multi line string in your Jenkinsfile it WILL probbly mess it up its indentation
## Install  
To use add jclean file somewhere into your path and `chmod +x jclean` 

## Usage
say you had a crap JenkinsFile that looks like this: 
```
stage('deploy-test') {
    try {
        build 'yourJob'
  }
    catch(error) {
      echo "First build failed, let's retry if accepted"
        retry(2) {
       input "Retry the job ?"
            build 'yourJob'
   }
            }
     }
```

Simply run `jclean path_to_JenkinsFile` and like magic you will have a nicly formated file (most of the time):
```
stage('deploy-test') {
    try {
        build 'yourJob'
    }
    catch(error) {
        echo "First build failed, let's retry if accepted"
        retry(2) {
            input "Retry the job ?"
            build 'yourJob'
        }
    }
}
```
