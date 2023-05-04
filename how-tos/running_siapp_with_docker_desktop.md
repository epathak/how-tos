# Running SIAPP with docker desktop
There is a new way to build the SIAPPs don't follow this... instead follow whats written [here](https://github.com/siemens/siapp-sdk)
1. Download docker [destop](https://desktop.docker.com/win/main/amd64/Docker%20Desktop%20Installer.exe?utm_source=docker&utm_medium=webreferral&utm_campaign=dd-smartbutton&utm_location=header)

   Install it with default configurations. Run the docker desktop.
2. Download the SIAPP SDK
Go to **https://github.com/siemens/siapp-sdk > Download the Zip file of this repo > Extract it**
3. Open Power Shell in the location where you extracted the zip
4. Run 
   ```
   .\build.bat DemoProject 
   ```
   The output should look like this
   ![image](https://user-images.githubusercontent.com/31771892/145667962-4a8b3c01-a3c4-44f2-8af7-07c0275d8fa5.png)
5. Run 
   ```
   .\run.bat DemoProject
   ```
   The output should look like this
![image](https://user-images.githubusercontent.com/31771892/145668001-3570e4da-2fa9-41bf-be15-f8845d86955f.png)
_Note down the port number printed on second last line. Port number may change every time you run this command._
6. These 2 windows will open up
![image](https://user-images.githubusercontent.com/31771892/145668053-710f415f-09f7-40a6-8c80-e5e7947e7cc9.png)
7. Open a browser and type in search box localhost:port_number. This window should appear after you click on the **Events** button from the LHS pane. 
![image](https://user-images.githubusercontent.com/31771892/145668088-2f60829e-eba2-4a64-86f0-84ce245d16a5.png)


