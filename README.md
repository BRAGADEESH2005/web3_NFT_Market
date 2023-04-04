# web3_NFT_Market

This is a market place where u can mint, sell and buy the NFTS using BRAD Tokens.
TO start with clone or fork the repository
Then u need to install the following things to get it implemented locally on your system:


    Installation and Setup for Windows


For Internet Computer Web3 Application Development

Requirements
    Windows 10 or higher (version 2004 or higher). Build 19041.xxx or higher.
    64-bit machine (System type x64 based PC)
Steps
WSL
Find the Windows PowerShell in your Start menu and run it as the Administrator.

WSL is the Windows Subsystem for Linux and it will allow us to run command line commands in Windows. Here’s more info from Microsoft: ​​
https://docs.microsoft.com/en-us/windows/wsl/install


As described in the docs above, we need to paste this command into PowerShell and hit enter:
wsl --install


Once that’s done, you’ll need to restart your computer.

Upon restart you will be prompted to setup an ubuntu username and password and then you will have successfully installed WSL. (Keep a note of both of these pieces of information, you’ll need it later on).
Note: when you type your password it will not show up, just make sure you know what you’re typing!


To confirm that everything worked correctly, type the following command into PowerShell:
wsl --list --verbose


VSCode
8.  Download and install the latest version of VSCode from here:

https://code.visualstudio.com/


9.  Install the Motoko language extension in VSCode (make sure it’s from the Dfinity team, or just use the link below).

https://marketplace.visualstudio.com/items?itemName=dfinity-foundation.vscode-motoko


10.  Install the Remote WSL extension.

https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-wsl



Node
11. Search and open up Ubuntu from the Start menu.


12.  Type the following command to install homebrew (Alternatively copy it from the homebrew website https://brew.sh/):

/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

Homebrew will make it easier for us to install other tools such as node. You might already have node installed on your windows system but because we’re working with WSL, you’ll need to install it on the linux system too.


13.  When prompted enter the password for the user that you set previously in step 5.


14 .  The installer will tell you how to add brew to the PATH. Copy the  commands they list and run them one by one in Ubuntu.

e.g.




15. Also run the command under the line “Install Homebrew’s dependencies if you have sudo access”:

sudo apt-get install build-essential


16. Check that everything worked by typing the command:

brew -version

If you see a version show up then everything was installed.


17. Install node using homebrew with the following command:

brew install node@16


18. Once it’s done check that it worked with:

node -version

NOTE: If you have another version of node installed (e.g. previous version or windows version) then you need will to link the version we just installed to homebrew (use the command: brew link node@16)

DFX
19.  Open up Ubuntu from the Start menu


20.  Copy the following command and paste it into your terminal and hit enter to install DFX.


DFX_VERSION=0.9.3 sh -ci "$(curl -fsSL https://sdk.dfinity.org/install.sh)"


After DFX has installed it will tell you where it was installed. e.g.



e.g. in my case, it tells me that it has been installed in /home/angela/bin/dfx


21.  Copy the installation path you got from the last step and replace <REPLACE WITH YOUR INSTALLATION PATH> from the command below (You can use Notepad for this):


export PATH=$PATH:<REPLACE WITH YOUR INSTALLATION PATH>

E.g. in my case it would be export PATH=$PATH:/home/angela/bin/dfx


22.  Paste the formatted command from the previous step and hit enter.


23. Check that it has been added by running:

echo "${PATH//:/$'\n'}"


24. Check that dfx has been successfully installed with the following command:

dfx --version



Notes
We’re going to work with dfx 9.0.3 so that we are all on the same version and you don’t get any surprises. Even if it prompts you to upgrade dfx, don’t do it!





Open up VSCode and click on the green icon on the bottom left. It looks like this:


Select New WSL Window



Inside the new window go to your Extensions panel and select the Remote WSL extension, click on Install in WSL: Ubuntu



Now take a look through the files inside the src folder. The main.mo is the Motoko file that we’ll be writing most of our code in.

Deploy the DApp
Go to Terminal → New Terminal



In the Terminal, run the following command to start the local dfx
dfx start


Once you see the line INFO Starting server. Listening on blah blah blah, then split out another terminal using the button shown below:




In the new terminal pane, run the following command to deploy your hello project:
dfx deploy --argument='("CryptoDunks #123", principal "qcmbe-lwtyv-ba6wq-hltov-amjff-wpnsb-hpi64-ozee7-acxqf-c77ao-uae", (vec {137; 80; 78; 71; 13; 10; 26; 10; 0; 0; 0; 13; 73; 72; 68; 82; 0; 0; 0; 10; 0; 0; 0; 10; 8; 6; 0; 0; 0; 141; 50; 207; 189; 0; 0; 0; 1; 115; 82; 71; 66; 0; 174; 206; 28; 233; 0; 0; 0; 68; 101; 88; 73; 102; 77; 77; 0; 42; 0; 0; 0; 8; 0; 1; 135; 105; 0; 4; 0; 0; 0; 1; 0; 0; 0; 26; 0; 0; 0; 0; 0; 3; 160; 1; 0; 3; 0; 0; 0; 1; 0; 1; 0; 0; 160; 2; 0; 4; 0; 0; 0; 1; 0; 0; 0; 10; 160; 3; 0; 4; 0; 0; 0; 1; 0; 0; 0; 10; 0; 0; 0; 0; 59; 120; 184; 245; 0; 0; 0; 113; 73; 68; 65; 84; 24; 25; 133; 143; 203; 13; 128; 48; 12; 67; 147; 94; 97; 30; 24; 0; 198; 134; 1; 96; 30; 56; 151; 56; 212; 85; 68; 17; 88; 106; 243; 241; 235; 39; 42; 183; 114; 137; 12; 106; 73; 236; 105; 98; 227; 152; 6; 193; 42; 114; 40; 214; 126; 50; 52; 8; 74; 183; 108; 158; 159; 243; 40; 253; 186; 75; 122; 131; 64; 0; 160; 192; 168; 109; 241; 47; 244; 154; 152; 112; 237; 159; 252; 105; 64; 95; 48; 61; 12; 3; 61; 167; 244; 38; 33; 43; 148; 96; 3; 71; 8; 102; 4; 43; 140; 164; 168; 250; 23; 219; 242; 38; 84; 91; 18; 112; 63; 0; 0; 0; 0; 73; 69; 78; 68; 174; 66; 96; 130;}))'


Finally, once that’s done, run the following command:
npm start

If you find an error in the above step then try the following  command:
       Ensure you are in your project directory in your terminal

      first, type the following in your terminal and hit enter

      * npm install --save-dev webpack-cli
      then type the following and hit enter:

      * npm upgrade --save-dev webpack-cli


Now you’re ready to see the NFT PROJECT project, open up your browser and go to:
http://localhost:8080/
