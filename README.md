# Install the BaSys 4.0 workbench including the BaSys 4.0 source code via Eclipse Installer

 1. Download the [Eclipse Installer](https://wiki.eclipse.org/Eclipse_Installer)
 2. Execute the downloaded package, click on the menu button the the top right corner, and switch to the advanced mode. This requires the Eclipse Installer to get installed on the hard disk.
    
    <img src='/readme/installer/eclipse-installer-1.png?raw=true' width='50%' height='50%'>
 
 3. Select 'Eclipse Modeling Tools' and click 'next'.

    <img src='/readme/installer/eclipse-installer-2.png?raw=true' width='50%' height='50%'>
 
 4. Add a new user project by clicking on the green plus sign. 

    <img src='/readme/installer/eclipse-installer-3.png?raw=true' width='50%' height='50%'>
 
 5. Copy the following URL into the 'Resource URIs' field and click 'OK'.

    `https://raw.githubusercontent.com/BaSys-PC1/eclipse-integration/master/installer/BaSys40Workbench.setup`
    
    <img src='/readme/installer/eclipse-installer-4.png?raw=true' width='50%' height='50%'>
 
 6. Select the added user project 'BaSys 4.0 Workbench' and click 'next'.

    <img src='/readme/installer/eclipse-installer-5.png?raw=true' width='50%' height='50%'>
 
 7. You can change the installation path composed of the 'Root install folder' and the 'Installation folder name'. Leave the rest as is and click 'next'.

    <img src='/readme/installer/eclipse-installer-6.png?raw=true' width='50%' height='50%'>
 
 8. Click 'Finish' to start the installation. This will install a new Eclipse IDE, pull the BaSys 4.0 source code from GitHub, and import the contained projects into the Eclipse workspace.

    <img src='/readme/installer/eclipse-installer-7.png?raw=true' width='50%' height='50%'>
    
# Post-installation steps

 1. Navigate to the newly created workspace folder ('Root install folder'/'Installation folder name'/ws) in a console window.
 2. Navigate to the sub folders `pom`, `common`, `platform` and run a `mvn clean install -DskipTests`.
 3. Optionally, navigate to the sub folders `demonstrator` and/or `cluster40` and run the same maven command.
 4. In Eclipse, select all projects (`[Ctrl]+[A]`) and perform a Maven Update Project (`[ALT]+[F5]`).