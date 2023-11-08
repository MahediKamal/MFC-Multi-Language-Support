# MFC Multi Language Support

cretate [MFC app] [dialog based] project.
Follow the steps shown in 1-7 image then click finish. a project like image 8 will be created.

Right clicki [add resource] type [menue] [new] -- figure 9.

add language switching optionj in the menue bar -- figure 10.

Currentu all the resource are in english version, Now we will create the chinise version of it.


solution -> rght click -> add -> new project -> MFC DLL -> project name(CHN) -> ok

Now the solution explorer will look like this - figure 14

Remove CHN.rc and CHN.rc2 from resource file. then remove resource.h from heaeder file of CHN.(delete colptelely)

go to ....\MultiLanguage\MultiLanguage folder. copy MultiLanguage.rc and resource.h and paste inside MultiLanguage\CHN folder.

Now go to ...\MultiLanguage]\MultiLanguage\res folder and copy all the file and then paste them inside MultiLanguage\CHN\res folder.

Now add all the copied file insise CHN. right click on CHN->add->existing item 

Now opem the resource of CHN project and translate the text into chinise(I use google translate to translate) --> figure 15

Modify the properties of the CHN project [Configuration properties] -> [linker] -> [Advanced] -> "No Entry Point" is changed to "Yes(/NOENTRY)" - figure 16


Dight click on CHN -> Project only -> build only CHN ==> this will create CHN.dll inside ...\MultiLanguage\Debug\CNH.dll





