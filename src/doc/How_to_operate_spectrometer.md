# Spectormer test on mitaka enviroment
Welcome to the fun of building and testing the mitaka test enviroment.
![NAOJ logo][NAOJ logo]

## Context
We will be using Mitaka enviroment on NAOJ instalations. So, if you dont have access to it you should start thinking how to get access to it. Also, you should request root access.
Open eclipse in you local enviroment. If you dont have it, please feel free to download it [here](https://www.eclipse.org/downloads/packages/release/2023-09/r/eclipse-ide-cc-developers).

Clone into your workspace (is ok to set it up as default)the following repositories by **File--> Import --> Project from git--> Next--> Clone from URL--> set everything as default**. This process should by applied for this three repos.
>git clone ssh://**username**@alma-gpuspec.mtk.nao.ac.jp/data/git/gpuspec-proto.git

>git clone ssh:///**username**@alma-gpuspec.mtk.nao.ac.jp/data/git/gpuspec-test-driver.git

>git clone ssh:///**username**@alma-gpuspec.mtk.nao.ac.jp/data/git/gpuspec-dump-extractor.git

After cloning you can start looking the insides of these wonderful repositories. Since this is a projecto that uses automatic documentation generation you can see some Doxygen outputs. Open this HTML file with your browser and check this really nice interactive documentation.
> ./gpuspec-proto/Doc/html/index.html

Also you can find some specifications, such as documentation from the manufacturer (Elects made the DTX) or ICD (Interface Common Definitions) for the whole functioning
> ./gpuspec-proto/Reference


## Compilation
Eclipse define an UI to interact with configurations for each project, to select one from an existing project that you imported, open the project explorer window (looks like a folder icon) right click on the desired project **Build configuration--> Set active--> choose**. If you want to look at the insides of configuration, you can right click on a project **Properties--> C/C++ Build--> choose** and look the differences between configuration on:
* Build Variables
* Enviroment
* Settings
* Tool chain editor
### let's give it a try
Select the active configuration as Release and build the project by clicking on the **Build** icon (which is the build icon? _it's a hammer mate_).
Then you have to give more capabilities to the binary that you generated. In this time should be under your _/Release_, but this depends on the configurations.
> sudo setcap cap_sys_admin,cap_sys_nice=+ep **filepath**

And  run the test driver from gpuspec-test-driver repository. This will simulate the DRXP data
> java -jar GPUSpectrometerTestDriver.jar

To perform some simulated asc interaction you should do 
> ./setup.sh #inside test driver repo inside resources/

followed by the desired test
> ./t54_interferometry_control.sh

you can see the final results by looking on 
>ls /dev/shm/asm_td/rec/<dump>


[NAOJ logo]: https://www.nao.ac.jp/asset/ogp/logo-naoj.png