# Day 2 Setup Instructions

![image](https://user-images.githubusercontent.com/11134288/200822829-c18ad8b7-34d6-4169-8023-5940209c8b1b.png)

## Node.js

Minimum Required Version : 12.0.0

Minimum Windows O/S Version: 10

Minimum macOS version: 10

You can skip this step if you already have a working Node.js 12.0 or greater installation. To check this, you can open a new Terminal/Windows Command Prompt (or another CLI of your choice), type the command below and press enter. For Windows users, Command Prompt can be found by pressing the Windows Start Button and searching for ‘Command Prompt’. For Mac users, the terminal can be found in Applications.

```sh
node -v
```

If you get a reported version (as per the screenshot further down), you already have Node.js installed, and can skip this section if it meets the minimum requirements. Otherwise if you get an error, it means you don’t have Node.js installed, and you should continue these steps to download and install it. If you do have a version of Node.js installed, but it’s less than 12, follow [these instructions](https://hardhat.org/tutorial/setting-up-the-environment.html#upgrading-your-node-js-installation) to upgrade it.

If you don’t have Node.js installed, download and install the latest version of the JavaScript runtime environment [Node.js and package manager NPM](https://nodejs.org/en/download/). Accept all default answers for questions.

[Installation video tutorial for Mac](https://www.youtube.com/watch?v=TQks1p7xjdI)

[Installation video tutorial for Windows](https://www.youtube.com/watch?v=GjfYHwlFI-c)

[Installation video tutorial for Linux](https://www.youtube.com/watch?v=K6QiSKy2zoM)

Once you’ve completed the installation, open a new Terminal/Windows Command Prompt (or another CLI of your choice), type the command below to ensure your installation is successful. For windows users, Command Prompt can be found by pressing the Windows Start Button and searching for ‘Command Prompt’. For Mac users, the terminal can be found in Applications.

```sh
node -v
```

![image](https://user-images.githubusercontent.com/11134288/200823181-a0d1cd8f-4605-4fb9-a88c-e875e3245e20.png)

Once you’ve verified your Node.js installation, also verify your NPM installation by entering the following command

```sh
npm -version
```

![image](https://user-images.githubusercontent.com/11134288/200823508-3a1f0062-c4a7-4c11-971e-051f19b81013.png)

---

## Git

Download and install the distributed revision control system [Git](https://git-scm.com/downloads). We will need this when installing some packages, and also to check your code into a repository when you’re finished. Accept all default values during installation. If you’re using macOS and you get prompted to install ‘command line developer tools’, accept and install them.

To test git once it’s installed, open a new Terminal/Windows Command Prompt (or another CLI of your choice), and type the command below

```sh
git --version
```

_Please read [this article](https://osxdaily.com/2015/02/04/terminal-wont-show-password-when-typed/) if you think that Terminal does not let you type your password_

[Video tutorial - How to install Git on Mac](https://www.youtube.com/watch?v=UTon_5ouqTM)

[Video tutorial - How to install Git on Windows](https://www.youtube.com/watch?v=qCKDABVedFU)

[Video tutorial - How to install Git on Linux](https://www.youtube.com/watch?v=ISPwJBE_F2g)

---

## Visual Studio Code

You’ll need a decent text/file editor for the bootcamp. We recommend Visual Studio Code, one of the most popular free, open source editors for smart contract development. Using Visual Studio Code will make it easier when you're following along with the exercise screenshots, and the integrated terminal makes it easier to switch between editing files, and running commands. If you have your own editor that you’re comfortable with, you can skip this step.

1. Go to [https://code.visualstudio.com/](https://code.visualstudio.com/), download and install the latest version of Visual Studio Code for your operating system

2. Open up Visual Studio Code. In the top menu, choose Code(File if you’re using Windows)->Preferences->Extensions

3. Search for the word ‘solidity’, then select and install the Solidity extension. This will give you syntax highlighting when developing your smart contracts

![image](https://user-images.githubusercontent.com/11134288/200823991-1af61895-62c9-437a-8f53-318081ca5551.png)

4.     Enable the terminal by selecting View -> Terminal from the top menu (or the keyboard shortcut Ctrl + `). Ensure you can run Node.js commands in your terminal window by running the following command

```sh
node -v
```

![image](https://user-images.githubusercontent.com/11134288/200824131-3eabc16e-d60e-463c-b883-0ffe2536a885.png)

If you’re using Windows and you get an error, ensure you’re using your CMD Terminal:
- In VS Code, press CTRL + SHIFT + P
- Search for ‘Terminal Select Default Profile’
- Select the ‘Command Prompt’ selection
- Restart VS Code and try running the command again in the terminal

---

## Sign-up for Alchemy Keys

We’ll be using Alchemy to connect to an Ethereum node and ‘fork the mainnet’ (don’t worry for now if you don’t understand what this means). Please complete the following steps to get your free Alchemy keys. 

1. Watch [this introductory video](https://www.youtube.com/watch?v=b0fBo9n2Qdk&t=674s) explainer about Alchemy

2. Head to [https://www.alchemy.com/](https://www.alchemy.com/), and select the ‘Get Started For Free’ button, and fill in the required details (or sign-up with a Google account). You will be required to verify your email account

3. Once logged in, create a new app, enter in the following details. Select the free-tier plan, and accept all default values.

![image](https://user-images.githubusercontent.com/11134288/200826421-137dbb94-6a6f-4178-85b0-b8befdd43c1a.png)

4. Once logged in, press the ‘View Key’ button, then copy and take note of your HTTP endpoint (save it somewhere). This is your mainnet key we’ll use for “forking mainnet” 

![image](https://user-images.githubusercontent.com/11134288/200826451-75387b96-fd5e-4282-a537-cc77b1c36fa4.png)

5. Click “Create App” in the main screen

![image](https://user-images.githubusercontent.com/11134288/200826472-652e31d5-dc51-48d3-bcbe-6adf208a63e0.png)

6. Fill out the form making sure to set **Network to Goerli**

![image](https://user-images.githubusercontent.com/11134288/200826510-8be09e2c-edf3-4abb-a763-eab01eddcc11.png)

7. Click on your newly created app and select “View Key”

![image](https://user-images.githubusercontent.com/11134288/200826579-3c0ba431-e79d-4986-a5a2-b2cd72b57338.png)

8. Copy and take note of your HTTP endpoint (save it somewhere)

![image](https://user-images.githubusercontent.com/11134288/200826614-ea5f5999-ca62-4aeb-972e-573d515b9944.png)

Congratulations, you’re now all set for the Smart Contract Developer Bootcamp!

---

## Yarn

If you get any errors installing yarn:

**Windows Users**:
- Ensure you’re running VS Code as Administrator (hold shift, right click, run as Administrator)
- Try installing it from the Command Prompt instead, ensuring you run the CMD.exe as Administrator
- Try downloading and installing it via the [msi installer](https://www.google.com/url?q=https://classic.yarnpkg.com/latest.msi&sa=D&source=editors&ust=1667999224433832&usg=AOvVaw3snpbbeOQr4gOjlitqatCr)

[Video tutorial - How to install Yarn on Windows](https://www.google.com/url?q=https://www.youtube.com/watch?v%3DHyJ89KCB7x8&sa=D&source=editors&ust=1667999224434299&usg=AOvVaw3nWiTPEgjwLrUZjM8IzQ1J)

**macOS or Linux users**:

- Try running it with sudo in front of the command

[Video tutorial - How to install Yarn on Mac](https://www.google.com/url?q=https://www.youtube.com/watch?v%3DPM5X23upvNg&sa=D&source=editors&ust=1667999224434844&usg=AOvVaw2kua-Aj_5q4b6G6LEOhcvW)

```sh
sudo npm install -g yarn
```

If you’re still stuck on installing yarn, check out some other possible installation methods on the [Yarn installation page](https://www.google.com/url?q=https://classic.yarnpkg.com/en/docs/install/&sa=D&source=editors&ust=1667999224435394&usg=AOvVaw3DN5YznH4fuijTwvZxFZ89)

---
