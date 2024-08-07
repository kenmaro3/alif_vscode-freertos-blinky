# alif_vscode_freertos_blinky
An example FreeRTOS based cmsis-pack project implemented in VSCode environment using ARM GNU Embedded toolchain.
Example is built on VSCode Getting Started Template [alif_vscode-template](https://github.com/alifsemi/alif_vscode-template)
The default hardware is Gen 2 Ensemble DevKit.

This project introduces you to the following aspects of FreeRTOS and VSCode,
- download the correct CMSIS pack for FreeRTOS using cpackget,
- configure the csolution.yaml & cproject.yaml files,
- configure FreeRTOS in the FreeRTOSConfig.h header file,
- create a thread,
- schedule the thread.

# Introduction 

Building the basic FreeRTOS LED blinky project in visual studio code using CMSIS-Toolbox, cmsis-csolution. The tools of the CMSIS-Toolbox provide a command-line interface for creating application projects that are based on software packs.
ARM cmsis-csolution is a VSCode extension which provides GUI for building and configuring the project.

# Tools: 

    Visual Studio Code.  

    Arm GNU Toolchain.  

    CMSIS Toolbox. 

    Ozone IDE. 

Please refer to the template project's [Getting started guide](https://github.com/alifsemi/alif_vscode-template/blob/master/doc/getting_started.md)

# Steps for building FreeRTOS LED Blinky app in VSCODE(GCC) 

    $ git clone https://github.com/alifsemi/alif_vscode-freertos-blinky.git --recursive
    $ cd alif_vscode_freertos_blinky
    $ git submodule init
    $ git submodule update
    
**If you do the step for "First time pack installation" as described in the User Guide, you don't need to do the following manually.**

    $ cpackget add ARM.CMSIS.6.0.0 
    $ cpackget add ARM.CMSIS-FreeRTOS.10.5.1
    $ cpackget add ~/Downloads\AlifSemiconductor.Ensemble.1.2.1.pack    

# Build
- Press the build (hammer) icon in cmsis csolution extension.
- Or Press CTRL+SHIFT+B
- or F1->Tasks:Run Task->cmsis.csolution.build

The generated binary cproject.elf can be found in the 'out' directory.
Run .elf file in Ozone using Jlink debugger.

# Description

**LED_Blinky_testapp.c**:   
>This file contains main() function which initializes and starts the FreeRTOS kernel.
We also create a single thread using a call to *xTaskCreate(led_demo_Thread, ...)* which binds the function "*led_demo_thread()*" to the thread.
Once the thread is successfully created, we start the scheduler using a call to *vTaskStartScheduler()*.  
  
**board.h**:  
>Selects the target development kit for this example. viz (Gen2 DevKit).   

**gcc_M55_HP.ld, gcc_M55_HE.ld**:   
>Standard Linker files for M55_HP, HE cores.   
