# How to Crete MFC Multi Language Support application


First cretate `MFC app` `dialog based` project.
Follow the steps shown in `1-7` images then click finish. 
![...](https://github.com/MahediKamal/MFC-Multi-Language-Support/blob/4f500b31316241842ae38d9fc59d929cea3e2e8c/image/1.PNG)
</br>
`                                                       fig: Image 1                                                      `
</br></br></br>
![...](https://github.com/MahediKamal/MFC-Multi-Language-Support/blob/4f500b31316241842ae38d9fc59d929cea3e2e8c/image/2.PNG)
</br>
`                                                       fig: Image 2                                                      `

</br></br></br>
![...](https://github.com/MahediKamal/MFC-Multi-Language-Support/blob/4f500b31316241842ae38d9fc59d929cea3e2e8c/image/3.PNG)
</br>
`                                                       fig: Image 2                                                      `

</br></br></br>
![...](https://github.com/MahediKamal/MFC-Multi-Language-Support/blob/4f500b31316241842ae38d9fc59d929cea3e2e8c/image/4.PNG)
</br>

`                                                       fig: Image 4                                                      `

</br></br></br>
![...](https://github.com/MahediKamal/MFC-Multi-Language-Support/blob/4f500b31316241842ae38d9fc59d929cea3e2e8c/image/5.PNG)
</br>

`                                                       fig: Image 5                                                      `

</br></br></br>
![...](https://github.com/MahediKamal/MFC-Multi-Language-Support/blob/4f500b31316241842ae38d9fc59d929cea3e2e8c/image/6.PNG)
</br>

`                                                       fig: Image 6                                                      `

</br></br></br>
![...](https://github.com/MahediKamal/MFC-Multi-Language-Support/blob/4f500b31316241842ae38d9fc59d929cea3e2e8c/image/7.PNG)
</br>

`                                                       fig: Image 7                                                      `

A project like image `figure- 8` will be created.
![...](https://github.com/MahediKamal/MFC-Multi-Language-Support/blob/4f500b31316241842ae38d9fc59d929cea3e2e8c/image/8.PNG)
</br>

`                                                       fig: Image 8                                                      `




Currently all the resource are in english version, Now we will create the chinise version of it. Do These following steps:

	solution -> rght click -> Add -> New Project -> MFC DLL -> give project name(In my case I choose CHN) -> Ok

Now the solution explorer will look like this - `figure 9`
</br>
![...](https://github.com/MahediKamal/MFC-Multi-Language-Support/blob/4f500b31316241842ae38d9fc59d929cea3e2e8c/image/14.PNG)
</br>

`                                                       fig: Image 9                                                      `

Now remove `CHN.rc` and `CHN.rc2` from `resource file`. then remove `resource.h` from `heaeder file` of CHN.(delete comptelely)

go to `x:\x\x\MultiLanguage\MultiLanguage` folder. Copy `MultiLanguage.rc` and `resource.h` and paste inside `x:\x\x\MultiLanguage\CHN` folder.

Now go to `x:\x\x\MultiLanguage\MultiLanguage\res` folder and copy all the file and then paste them inside `x:\x\x\MultiLanguage\CHN\res` folder.

Now add all the copied file insise `CHN` folder. To add right click on CHN then `add -> existing item` 

Now open the resource of CHN project and translate the text into chinise(I use google translate to translate). Figure 10 shows a resource after tranalating the text inside it.
</br>
![...](https://github.com/MahediKamal/MFC-Multi-Language-Support/blob/4f500b31316241842ae38d9fc59d929cea3e2e8c/image/15.PNG)
</br>

`                                                       fig: Image 10                                                      `

Modify the properties of the CHN project `[Configuration properties] -> [linker] -> [Advanced] -> "No Entry Point" is changed to "Yes(/NOENTRY)"` - figure 16


Right click on `CHN` Then `Project only -> build only CHN` ==> this will create CHN.dll inside `x:\x\x\MultiLanguage\Debug\CNH.dll`


Now add a HINSTANCE type variavle inside `MultiLanguage.h`

	[HINSTANCE m_hLangDll;]


then go inside MultiLanguage.cpp  and inside function `BOOL CMultiLanguageApp::InitInstance(){}` write this part of code. This part of code will load Chinise language instead of English.


	m_hLangDll = ::LoadLibraryA("CHN.dll");
	if (m_hLangDll != NULL) {
		AfxSetResourceHandle(m_hLangDll);
	}
	else {
		TRACE("\ncan't load chinise\n");
	}
 



This code will load the chinise language instead of English language. Now you can use if else condition as you want to coltroll different language. Cretete different dll for different language and add logic when to load which dll.




