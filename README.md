# Java Tomcat Enhance Time Deploying (Reduce waiting time for changing small codes in project to be redeployed).

This is what I've collected to decrease the time for deploying (hot-swap or hot-deploy) a Servlet based Java Web application.

+ For Tomcat (production environment only): add in  TOMCAT/conf/context.xml <Context reloadable="true"> and restart tomcat. This feature will automatically reload the changed classes (triggered by IDE when it finished compiling the changed classes from .java to .class) instead of redeploying the whole application.

http://stackoverflow.com/questions/998737/integrating-tomcat-and-eclipse-as-a-hot-deploy-environment/999257#999257

+ For Intellij IDE (or other IDE). There is a limitation that only change in method's body of class will take effect immediately when the Web Application Server (e.g: Tomcat is running in debug mode), and this feature is called "hot-swap" (i.e: making the changed classes have effect immediately, instead of having wait for deploying).

http://arhipov.blogspot.de/2016/02/hotswap-vs-hot-deploy_12.html

 I don't like it actually as if I don't want to debug then when I click on "Update" (Ctrl + F10) in Intellj, it should reflect these changes in Tomcat Server as well (if "reloadable" is not set to true as above, IntelliJ will just compiled the changed files to .class but Tomcat will not load these changes immediately).
 
 http://stackoverflow.com/questions/19596779/intellij-and-tomcat-changed-files-are-not-automatically-recognized-by-tomcat/19609115#19609115

So hot-swap will work as if Intellij run Tomcat in debug mode and it will trigger the build automatically on exploded-war either by clicking on "Reload changed classes" or implicitly updating these changes when the IDE is out of focus.

Therefore, with this process, it can reduce the waiting time for clean, build a big project, meanwhile you just change in one or few places. This is what I learnt so I think it will help you as well.
