# 1-to-1 RTC: A Sample Web App using Node.js with EnableX Web Toolkit

The Sample Web App demonstrates the use of APIs for EnableX platform to develop basic 1-to-1 RTC (Real Time Communication) Application. The main motivation behind this application is to demonstrate usage of APIs and allow developers to ramp up on app by hosting on their own devices instead of directly using servers.

RTC Applications hosted on EnableX platform run natively on supported set of web browsers without any additional plugin downloads.

This basic 1-to-1 Video Chat Application is developed using HTML, CSS, Bootstrap, JavaScript, jQuery, Node.js and EnxRtc (The EnableX Web Toolkit).

>The details of the supported set of web browsers can be found here:
https://developer.enablex.io/video/browser-compatibility-of-enablex-video/


## 1. Important!

When developing a Client Application with EnxRtc.js make sure to include the updated EnxRtc.js polyfills from https://developer.enablex.io/video-api/client-api/web-toolkit/ for RTCPeerConnection and getUserMedia. Otherwise your application will not work in web browsers.


## 2. Trial

Sign up for a free trial https://portal.enablex.io/cpaas/trial-sign-up/ or try our multiparty video chat https://try.enablex.io/


## 3. Installation

### 3.1 Pre-Requisites

#### 3.1.1 App Id and App Key

* Register with EnableX [https://portal.enablex.io/cpaas/trial-sign-up/] 
* Create your Application
* Get your App ID and App Key
* Clone this repository `git clone https://github.com/EnableX/One-to-One-Video-Chat-Sample-Web-Application.git --recursive`
### ![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+) Please note `--recursive` option. Repo should be cloned recursively to download `client` app. 

#### 3.1.2 SSL Certificates or Self-Signed Certificates

The Application needs to run on https. So, you need to use a valid SSL Certificate for your Domain and point your application to use them.

However you may use self-signed Certificate to run this application locally. There are many Web Sites to get a Self-Signed Certificate generated for you, Google it. Few among them are:

* https://letsencrypt.org/
* https://www.sslchecker.com/csr/self_signed
* https://www.akadia.com/services/ssh_test_certificate.html

The following below can also be used to create a self-signed certificate.
```javascript
  cd One-to-One-Video-Chat-Sample-Web-Application
  cd server
  mkdir certs
  sudo openssl req -x509 -newkey rsa:4096 -keyout ./certs/example.key -out ./certs/example.crt -days 10000 -nodes
  sudo chmod 755 ./certs/example.*
  cd ..
```

#### 3.1.3 Configure

Before you can run this application, configure the service. Copy the `server/example.env` as `server/.env` and update the values. Or you can set following system environment variables instead:

```javascript
  SERVICE_PORT - Node port on which your application will run. Default port set is 5000
  ENABLEX_APP_ID - Your EnableX `App ID` - It's your username for EnableX API and can be found at Dashboard > Projects https://portal.enablex.io/dashboard/
  ENABLEX_APP_KEY - Your EnableX `App Key` - - It's your password for EnableX API and can be found at Dashboard > Projects https://portal.enablex.io/dashboard/
```

For Mac and Linux, open a terminal window and type the following commands. Note - Replace all the characters after the `=` with values from your EnableX account:
```javascript
  export SERVICE_PORT=XXXX
  export ENABLEX_APP_ID=XXXXXXXXXX
  export ENABLEX_APP_KEY=XXXXXXXXX
```

On Windows, open a powershell / command window and type the following commands. Note that there is no `=`, just the key and value separated by a space:
```javascript
  setx SERVICE_PORT 'XXXX'
  setx ENABLEX_APP_ID 'XXXXXXXXX'
  setx ENABLEX_APP_KEY 'XXXXXXXXX'
```

### 3.2 Build

Run `npm install` to build the project and the build artifacts will be stored in the `./node_modules` directory.

#### 3.2.1 Run Server

Run `node server.js` inside `server` folder to start your server.
```javascript
  cd server
  node server.js
```
Server started. Listening on Port 5000


#### 3.2.2 Configure And Run the app Using BASH Script 
Prerequisite: latest version of Node js , git Installed And you have Enablex App ID and KeyI
* Downloads bash script file script.sh (https://github.com/ashutoshmishraji/One-to-One-Video-Chat-Sample-Web-Application/blob/master/script.sh)
* Make it executable in linux terminal  Using  this command "sudo chmod +x script.sh"
* And just type ./script.sh ( In same directory where your script.sh present)
* Give the information about configuration 
* That's it , You will see Localhost listening to Port
* Awesome Your application is ready to explore



#### 3.2.3 Test Video Call

* Open a browser and go to `https://yourdomain:5000/`. The browser should load the App. Go to -> Advanced -> Proceed to localhost
* Don't have a Room ID? Create here (create a new RoomID)
* Store the Room ID for future use or share
* Enter a username (e.g. test0)
* Join and allow access to camera and microphone when prompted to start your first webRTC call through EnableX
* Open another browser tab and enter `https://yourdomain:5000/`
* Enter the same roomID previously created and add a different username (test1) and click join
* Now, you should see your own video in both the tabs!



## 4. Server API

EnableX Server API is a Rest API service meant to be called from Partners' Application Server to provision video enabled
meeting rooms. API Access is given to each Application through the assigned App ID and App Key. So, the App ID and App Key
are to be used as Username and Password respectively to pass as HTTP Basic Authentication header to access Server API.

For this application, the following Server API calls are used:
* https://developer.enablex.io/video-api/server-api/rooms-route/#create-room - To create room to carry out a video session
* https://developer.enablex.io/video-api/server-api/rooms-route/#create-token - To create Token for the given Room to join a session

To know more about Server API, go to:
https://developer.enablex.io/video-api/server-api/


## 5. Client API

Client End Point Application uses Web Toolkit EnxRtc.js to communicate with EnableX Servers to initiate and manage RTC Communications.

To know more about Client API, go to:
https://developer.enablex.io/video-api/client-api/
