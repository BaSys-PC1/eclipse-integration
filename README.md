# Prerequisites

You need to have Git, Java, and Maven set up before installing the BaSys 4.2 workbench or just working with the code base. 

#### Git ####
 - Download and install [git](https://git-scm.com/download).
 - Configure git with [your identity](https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup) and [your ssh key](https://git-scm.com/book/en/v2/Git-on-the-Server-Generating-Your-SSH-Public-Key).
 - Once you have an account for our internal GitLab instance, [add you public ssh key to this account](https://docs.gitlab.com/ee/ssh/README.html#adding-an-ssh-key-to-your-gitlab-account) (i.e. do not navigate to gitlab.com as described in step 2 on the linked web page). 

#### Java ####
 - The BaSys source code is compliant to Java 8. However, if you want to develop with the latest Eclipse IDE (2020-09), Java 11 is required.
 - So, download and install [OpenJDK 11](https://adoptopenjdk.net/index.html?variant=openjdk11&jvmVariant=hotspot). The installer can set the `JAVA_HOME` system environment variable for you if you check the option in the installation wizard. But you can also [set it manually](https://javatutorial.net/set-java-home-windows-10) afterwards.

#### Maven ####
 - Download [Maven as binary zip archive](https://maven.apache.org/download.cgi) and follow the [installation instructions](https://maven.apache.org/install.html).
 - Since we use our own maven repository for snapshot artifacts that are built with our CI chain, you have to tell maven the repo location. For this, create a directory `.m2` in your user folder and inside that folder create a file `settings.xml` with the following contents:

```
<?xml version="1.0"?>
<settings>
	<profiles>
		<profile>
			<id>basys_nexus_profile</id>
			<repositories>
				<repository>
					<id>DFKI BaSys Nexus</id>
					<url>https://nexus.basys.dfki.dev/repository/maven-public/</url>
				</repository>
			</repositories>
		</profile>
	</profiles>
	<activeProfiles>
		<activeProfile>basys_nexus_profile</activeProfile>
	</activeProfiles>
</settings>
```


# Install the BaSys 4.2 workbench including the BaSys 4.2 source code via Eclipse Installer

 1. Download the [Eclipse Installer](https://wiki.eclipse.org/Eclipse_Installer).
 2. Execute the downloaded package, click on the menu button the the top right corner, and switch to the advanced mode. This requires the Eclipse Installer to get installed on the hard disk.
    
    <img src='/docs/installer/eclipse-installer-1.png?raw=true' width='50%' height='50%'>
 
 3. Select 'Eclipse IDE for Java Developers' and click 'next'.

    <img src='/docs/installer/eclipse-installer-2.png?raw=true' width='50%' height='50%'>
 
 4. Add a new user project by clicking on the green plus sign. 

    <img src='/docs/installer/eclipse-installer-3.png?raw=true' width='50%' height='50%'>
 
 5. Copy the following URL into the 'Resource URIs' field and click 'OK'.

    `http://basys.dfki.dev/setup/BaSys40Workbench.setup`
    
    <img src='/docs/installer/eclipse-installer-4.png?raw=true' width='50%' height='50%'>
 
 6. Select the added user project 'BaSys 4.0 Workbench' and optionally select a stream. Then click 'next'. The Github master branch stream is publicly available and will pull the full source code while the two develop branch streams are only internally available. The P4P demonstrator stream will pull only the demonstrator-specific source code.

    <img src='/docs/installer/eclipse-installer-5.png?raw=true' width='50%' height='50%'>
 
 7. You can change the installation path composed of the 'Root install folder' and the 'Installation folder name'. Leave the rest as is and click 'next'.

    <img src='/docs/installer/eclipse-installer-6.png?raw=true' width='50%' height='50%'>
 
 8. Click 'Finish' to start the installation. This will install a new Eclipse IDE.

    <img src='/docs/installer/eclipse-installer-7.png?raw=true' width='50%' height='50%'>
    
 9. Wait for the installation to finish and click 'Finish' again.
 
    <img src='/docs/installer/eclipse-installer-8.png?raw=true' width='50%' height='50%'>  
    
 9. The Eclipse IDE opens up and automatically starts an Eclipse Update Wizard that pull the git repos, imports the contained projects into the Eclipse workspace, and sorts them into working sets. Click 'Finish' again, when the wizard completed.
 
    <img src='/docs/installer/eclipse-installer-9.png?raw=true' width='50%' height='50%'>  

    
# Post-installation steps

 1. Navigate to the newly created workspace folder ('Root install folder'/'Installation folder name'/ws) in a console window.
 2. Run a `mvn clean install -DskipTests` command in the sub-folders `pom`, `common`, `asset-administration-shell`, `controlcomponent`, `platform`, and `p4p-demonstrator`.
 3. In Eclipse, select all projects (`[Ctrl]+[A]`) and perform a Clean (via the respective Project menu item) and a Maven Update Project (`[ALT]+[F5]`).