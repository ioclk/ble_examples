Frequently Asked Questions
==========================

1. Q: What if I installed the TI BLE SDK to a non default location (i.e. not C:\ti\simplelink\ble\_sdk\_2\_02\_00\_31)
 - A : All projects reference files from the BLE stack using environment variables, you can change this in your IDE's project files

    **IAR**

    1. Navigate to a project within the repo (i.e. multi\_role -- examples/cc2650em/multi_role/iar) and open the `.custom_argvars` file
    2. Replace any references to C:\ti\simplelink\ble\_sdk\_2\_02\_00\_31\ with your custom install location
    3. Rinse and repeat for all project files

    **CCS**

    1. Navigate to a project within the repo (i.e. multi\_role -- examples/cc2650em/multi_role/ccs)
    2. Open the `.projectspec` file for the stack (inside the /stack folder) and change the path from c:/ti/simplelink/ble\_sdk\_2\_02\_00\_31 to your custom path as below
    ```xml
    <pathVariable name="TI_BLE_SDK_BASE" path="c:/ti/simplelink/ble_sdk_2_02_00_31" scope="project"></pathVariable>
    ```
    3. Navigate to your project's app folder and repeat step 2.
    4. Rinse and repeat for all project files

2. Q: I get an error when I am trying to run a Python script from the /tools folder
 - A: Likely your Python environment is not installed correctly. Please check the following debug steps
    1. All scripts in the tools folder use Python 2.7, ensure that you have this version installed to `C:\Python27`
    2. Python scripts can be invoked using `python <script_name>.py` this requires adding Python to your environment variables
      - Add C:\Python27 and C:\Python27\Scripts to the `PATH` variable within your Windows environment vars, see [windows env vars](https://www.java.com/en/download/help/path.xml) for more info.
    3. If you can run the script successfully but get a runtime error, you likely don't have the necessary python modules installed.
      - Python modules can be found by looking at the `import` statements at the top of the `.py` file. You can install Python modules using the Python package manager, pip.
      - Install Pip by following [these steps](http://stackoverflow.com/questions/4750806/how-do-i-install-pip-on-windows). The section "Python 2 ≤ 2.7.8 and Python 3 ≤ 3.3" will be most helpful.