# Polish Notation API test in Jenkins

The tests were created using Postman and exported as a collection JSON file.

To run the test in Jenkins please follow the steps below:

## Prerequisite 
Install NodeJS and npm. Newman is written in NodeJS and we distribute the official copy through npm. Install nodejs and npm for Linux "https://docs.npmjs.com/getting-started/installing-node"

Access to Jenkin server and interface

## Steps
1. On the Jenkins machine install newman using "npm install -g newman"
2. Copy the "Test.postman_collection.json" to a directory and remember this for later

Note: You Run this collection inside newman, using the command "newman run Test.postman_collection.json" to see if everything is set up correctly

3. In Jenkins, create a new job by clicking on the “New Item” link on the left sidebar > Select a “Freestyle Project” from the options > Name your project.

4. Add a build step in the project. The build step executes a Shell command (for linux and Mac OS) and execute Windows batch command (for windows).

5. The command is 
```
export PATH=/usr/local/bin/
newman run /DIRECTORY/Test.postman_collection.json
```
Replacing DIRECTORY with the directory path to the json file

6. Click the save button to finish creating the project.

7. Run this build test manually by clicking on the “Build Now” link in the sidebar.

Jenkins indicates that the build has failed with a red dot in the title. We can check why with the console output from newman.

There are two tests that fails

- Division is not possible on the API
- Addition results is return if there's no operator defined
