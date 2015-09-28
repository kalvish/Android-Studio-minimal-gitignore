***
### Building the project ###

There are two ways to build the project.

The project file in this git repo represent only items are essential to the app (As shown in the image).

![Alt text](https://github.com/kalvish/Android-Studio-minimal-gitignore/blob/master/docs/images/very_basic_project_files.png)



There are two ways to build the project.

* Using Android Studio

If you are using Android Studio, you can use "Import project" to successfully build the project. 


* Alternatively you can build using command line, follow [Building Android Projects with Gradle](http://spring.io/guides/gs/gradle-android/).

	* If you are building using command line,
	go to the main project folder and run;

  	`$ .\gradlew assembleRelease`

 
	* Install gradle on your computer. Make sure you can run 'gradle' from your project folder.

	![Alt text](https://github.com/kalvish/Android-Studio-minimal-gitignore/blob/master/docs/images/gradle_version.png)

	* Then run the following command on your main forder. It will create .\gradlew.sh for Unix\Mac and .\gradlew.bat.

 	```
	$ gradle wrapper
 	```  

 	* Frequently used commands:

 		1. `.\gradlew assembleDebug` - Create the debug version of the app.

 		2. `.\gradlew assembleRelease` - To create a release version of the app.

 			* This command needs signing details specified in the `app`->`build.gradle`

```
#!python		
 				android {
 					signingConfigs {
        				release {
            				storeFile file("android_key_file_name") //Key path
            				storePassword "####" //Store password
            				keyAlias "keyalias"  //Key alias
            				keyPassword "####" //Key password
        				}
    				}
 				}
```

***

* Also add `signingConfig signingConfigs.release` to the same file.


```
#!python
				android {
 					buildTypes {
        				release {
            			
            				signingConfig signingConfigs.release
        				}
    				}					
 				}
```

***

* Here I've added key to the `app` folder, so that `storeFile file("android_key_file_name")` will search for the file in the same directory.

* To avoid getting `lint` errors, please add the following to the `app`->`build.gradle` as speficied below.


```
#!python
				android {
					lintOptions {
          				abortOnError false
    				}		
				}
```

***

