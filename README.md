# FOS Simulator
##### Fire Operation Simulation
![FOS Map Sample](./Docs/MapPreview.png)

### 1. How to Run FOS Simulator
There are two ways to operate the FOS simulator: `running on desktop` and `using a browser`.
###### 1-1. `Runnign on your Desktop`
> `!!Disclamer and Warning!!` Do not download those FOS Binarys on DoDIN Devices such as NIPRNET Computer. According to the Army IT User Agreement (AUP), you are not allowed to download or run any executable files on your government devices without any authorization of AO.
* Download the appropriate Binary/Executable FOS Simulator file for your operating system, from 
`Commertial`
[FOS Repository Release Tab](https://github.com/usfk-code-challenge-2023/FOS/releases), or
`DoD OneDrive`
[Digital O-Plan Sharepoint](https://armyeitaas.sharepoint-mil.us/:f:/t/DigitalO-Plan/EnqjykZrxFJOiZWOVMpqIeEBrrfoFucv0IEQZlKifhW9vw?e=qY7U0h) (requires CAC login).
* Run executable with command line argument. If the arguments are not specified, the program will attempt to receive required entries that have not been entered into the CLI interface since it was executed.
  <pre>./"FOS Simulator" --host 127.0.0.1 --port 8080</pre>
  ```python
  for index, arg in enumerate(argv):
        if arg == "help" or arg == "-help" or arg == "-h" or arg == "--help":
            print("""Usage:
            --help : to list all available
            --host [IP Address, Str] : host to connect to
            --port [Port, Int] : port to connect to
            --visualize [0/1] : visualize or not
            --logging [0/1] : enable log printing using stdout or not
            """)
            sys.exit(0)

        match (arg.startswith("--"), arg):
            case True, "--host":
                result["host"] = argv[index + 1]
            case True, "--port":
                result["port"] = int(argv[index + 1])
            case True, "--visualize":
                result["visualize"] = bool(int(argv[index + 1]))
            case True, "--logging":
                result["logging"] = bool(int(argv[index + 1]))
  ```
* Simulation log file will be automatically stored on the same directory with the simulator, named as play_log.json.

###### 1-2. `Runnign on the Browser`
* Download and save the FOS Simulator html and WASM related files in one directory from listed release repository above. And open index.html with your browser.
  > If you use the file:// protocol when running index.html, you may need to change your browser's CORS settings to load WASM files.
  > <pre>C:\"Program Files (x86)"\Microsoft\Edge\Application\msedge.exe --disable-web-security --user-data-dir="C:\Users\_YOUR_USER_NAME__\Desktop\FOSWEB"</pre>
  > or
  > 
  > Reference this: https://answers.microsoft.com/en-us/microsoftedge/forum/all/disable-cors/55c89fb6-8d72-4318-9ee3-e9cdfc6fa708.
  > 
  > Alternatively, implement a web server to access index.html using the http:// protocol instead of the file:// protocol.
  - or simply visit our example web site for FOS Simulation https://usfk-code-challenge-2023.github.io/FOS.
  
* Enter the address of the controller server to which the simulator will connect.
  
  > Since the simulator is working on your machine with WebAssembly, not the server somewhere else, you can connect with your local-hosted server(connector) unless you are on the browser.
The main purpose of the browser implementation is for some people who will work on DoDIN computers. If you need to work in a browser, implement a local TCP server for the controller or implement an external server to connect with your browser.
* You need to download your play log file from your browser after simulation is finised.

###### 1-3. `Detailed Description`
* For more information on how to use the simulator and details, please visit https://usfk-code-challenge-2023.github.io/FOS/Docs.

### 2. Implementing FOS Controller
* Yo can find out the simple example of controller at https://github.com/usfk-code-challenge-2023/FOS/blob/main/Docs/proto.ipynb.
* Turning off the visualization option on the FOS Simulator might helpful for your iteration for the AI/ML learning.

### 3. Bug Report
* For the issues about simulator's bug, please contact SGT Mun, Chaeun, USFK J5 AI/ML Planning Assistant, Digital O-Plan, via email at chaeun.mun.fm@army.mil or upload issue report to https://github.com/usfk-code-challenge-2023/FOS/issues.
* Please check the page above regularly to track additional simulator fixes due to bugs discovered since the competition started.
