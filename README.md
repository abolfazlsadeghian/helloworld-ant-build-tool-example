# helloworld-ant-build-tool-example
Example of using ANT build tool with Java Hello World Program

The ant build tool was built especially for Java projects around the year 2000. 

 

The aim of Java to be a write-one-run-anywhere language needed a tool that can also be used in different environments. 

 

Although make is available on Unix machines , and Windows as well , Makefile were not always compatible. 

 

There was a small problem with the use of the tab character that some editors replaced with space, rendering Makefile unusable. 

 

The problem with make that ignited the development of Ant is that the commands are shell commands. Even if the implementation of the make program was made to be compatible on different operating systems, the used commands were many times incompatible , and that was something make itself could not change. Because make issues external commands to build  the targets. 

 

Ant is following the major principles of make. There are targets that may depend on each other and there are commands that need to be executed in appropriate sequence to create the targets one after other, following the dependency order. 

 

The description of the dependences and the commands is XML and the commands are implemented in Java . 

 

As Ant is neither part of the operating system nor the JDK , you will have to download and install it separately if you want to use it. 

 

## Installing Ant 

 

Ant can be downloaded from its official website http://ant.apache.org you can download the source or the precompiled version , the easiest way is to download the binary in a tar.gz format. 

 

Whenever you download software from the internet , is highly recommended that you can check the integrity of downloaded file. 

 

The HTTP protocol does not contain error checking , and it may happen that a network error remains hidden or a malevolent internal proxy modifies the downloaded file. 

 

Download site usually provide checksums for the downloadable files. These are usually MD5, SHA1, SHA512 , or some other checksums. 

 

After the file is downloaded , you can explode it to a subdirectory using the following command: 

 
```
> tar xfz apache-ant-1.9.7-bin.tar.gz 
```
 

The created subdirectory is the usable binary distribution of Ant. 

 

Usually it is better to be installed at root under : 

 
```
 /bin/ 
```
 

After that you should set the environment variable as ANT_HOME to point to this directory and also add bin directory of the installation to the PATH.        

 
```
> export ANT_HOME=/bin/apache-ant-1.9.7/ 

> export PATH=${ANT_HOME}bin:$PATH 
```
 

Then type ant at terminal to check to see if it is installed : 

 
```
> ant 
```
 

## Using ANT 

 

When you see a project to be build by Ant, you will see a build.xml file. 

 

It can have any other name , and you can specify the name of the file as a command-line option for Ant, but it is the default file name build.xml 

 

Example of build.xml file: 

 
```

<project name="HelloWorld" default="jar" basedir="."> 

<description> 

    This is a sample HelloWorld project build file. 

</description> 

    <property name="buildDir" value="build"/> 

    <property name="srcDir" value="src"/> 

    <property name="classesDir" value="${buildDir}/classes"/> 

    <property name="jarDir" value="${buildDir}/jar"/> 

  

<target name="dirs"> 

    <mkdir dir="${classesDir}"/> 

    <mkdir dir="${jarDir}"/> 

</target> 

  

<target name="compile" depends="dirs"> 

    <javac srcdir="${srcDir}" destdir="${classesDir}"/> 

</target> 

  

<target name="jar" depends="dirs,compile"> 

    <jar destfile="${jarDir}/HelloWorld.jar" basedir="${classesDir}"/> 

</target> 

  

</project> 

```
 

The top-level XML tag is project. Each build file describes on project, hence the name. There are three possible attributes 

 

Name : This defines the name of the project and is used by some IDEs to display it in the left panel identifying the project 

Default: This names the target to use when no target is defined on the command line starting Ant 

Basedir : This defines the initial directory used for any other directory name calculation in the build file. 

 

The build file can contain a description for the project , as well as properties in property tags. These properties can be used as variables in the attributes of the tasks between the &{and} characters and important role in the build process. 

 

The targets are define in target XML tags. 

 

Each tag should have a name that uniquely identifies the target in the build file and may have a depends tag that specifies one or more other targets that this target depends on. 

 

In case there is more than one target, the targets are comma separated in the attribute. The tasks belonging to the targets are executed in the same order as the targets dependency chain requires. 

 

You can also add a description attribute to a target that is printed by Ant when the command-line option –projecthelp is used. 

 

This helps the users of the build file to know what targets are there and which does what. 

 

Build 

 

Than in the Jar folder enter this command to run the program: 

 
```
> java -cp HelloWorld.jar HelloWorld 
```
 

 
