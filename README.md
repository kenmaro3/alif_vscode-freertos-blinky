# alif_vscode_freertos_blinky
An example FreeRTOS based project implemented in VSCode using ARM GNU Embedded toolchain.

# Introduction 

Building the basic LED blinky project in visual studio code using CMSIS-Toolbox. The tools of the CMSIS-Toolbox provide a command-line interface for creating application projects that are based on software packs. 

# Tools: 

    Visual Studio Code.  

    Arm GNU Toolchain.  

    CMSIS Toolbox. 

    Ozone IDE. 

Refer to **AUGD0012 v1.4 Getting Started with VS Code, GCC and J-Link Using CMSIS Toolbox** available at [AlifSemi.com/](https://alifsemi.com/support/application-notes-user-guides/ensemble/)
# Steps for building FreeRTOS LED Blinky app in VSCODE(GCC) 

    $ git clone git@github.com:alifsemi/alif_vscode-template.git freertos_blinky
    $ cd freertos_blinky
    $ git submodule init
    $ git submodule update
    $ cpackget add ARM.CMSIS.5.9.0 
    $ cpackget add ARM.CMSIS-FreeRTOS
    $ cpackget add ~/Downloads\AlifSemiconductor.Ensemble.1.1.1.pack    

For FreeRTOS applications, do the following changes in FreeRTOSConfig.h file: 
**Note**: path to FreeRTOSConfig.h file “path/to/new/pack-root/ARM/CMSIS-FreeRTOS/10.5.1/CMSIS/RTOS2/FreeRTOS/Config/ARMCM/FreeRTOSConfig.h” 

    change configRUN_FREERTOS_SECURE_ONLY to 1. 
    change configENABLE_TRUSTZONE to 0.

Copy the **LED_Blinky_testapp.c** into 'app' directory from '<cmsis-packs>\AlifSemiconductor\Ensemble\1.1.1\Boards\DevKit-e7\Templates\FreeRTOS directory'.

# Project Tree

![image](https://github.com/AlifSemiDev/alif_vscode_freertos_blinky/assets/118854049/bae23be4-e456-415b-905a-b28334472073)

Update the csolution.yaml and cproject.yaml files as shown below. 

csolution.yaml 

![image](https://github.com/AlifSemiDev/alif_vscode_freertos_blinky/assets/118854049/ccf7756e-7cc4-4da4-b56a-db6354ca3f2f)

cproject.yaml 

![image](https://github.com/AlifSemiDev/alif_vscode_freertos_blinky/assets/118854049/b5452cdf-e0da-479c-8767-729cce026424)
 
# Build

Press CTRL+SHIFT+B or F1->Tasks:Run Tasks->Build Project with cbuild

The generated binary cproject.elf can be found in the 'out' directory.
Run .elf file in Ozone using Jlink debugger.
