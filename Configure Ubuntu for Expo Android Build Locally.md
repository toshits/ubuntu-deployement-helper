
##### NOTE: Recommended to use root user while configuring and building app

## Update Ubuntu

```shell
sudo apt update -y && sudo apt upgrade -y
```

## Install Node.js

##### Change 16 in setup_16 to desired version of node (Ex:- For 18.16.1 change it to setup_18.x)

```shell
cd ~
curl -sL https://deb.nodesource.com/setup_16.x -o /tmp/nodesource_setup.sh
```

```shell
sudo bash /tmp/nodesource_setup.sh
```

```shell
sudo apt install nodejs
```

#### Verify if node.js is successfully installed by checking version

```shell
node -v
```


#### Using YARN instead of NPM is recommended

```shell
npm install --global yarn
```

## Install JAVA and Set env variables for it

```shell
sudo apt install default-jre
```

```shell
sudo apt install default-jdk
```

#### Check if both JAVA jre and jdk is successfully installed

```shell
java -version
```

```shell
javac -version
```

#### Find the folder where java jvm is installed and copy the path. It must be somewhere:
```
/usr/lib/jvm/java-1.x.x-openjdk
```
*Replace the java-1.x.x-openjdk with your folder name

```shell
export JAVA_HOME="/usr/lib/jvm/java-11-openjdk-amd64"
```

```shell
export PATH=$JAVA_HOME/bin:$PATH
```
***Environment Variables are not persisted. After system reboot you may need to add them again.*

## Install Android SDK

```shell
sudo apt install android-sdk
```

#### The location of Android SDK on Linux can be any of the following:
- `/home/AccountName/Android/Sdk`
-  `/usr/lib/android-sdk`
- `/Library/Android/sdk/`
- `/Users/[USER]/Library/Android/sdk`

## Find your android SDK path and Add the environmental variables

***My path to android SDK is /usr/lib/android-sdk. Change the below command according to yours*
```shell
export ANDROID_HOME="/usr/lib/android-sdk/"
```

```shell
export PATH="${PATH}:${ANDROID_HOME}tools/:${ANDROID_HOME}platform-tools/"
```
***Environment Variables are not persisted. After system reboot you may need to add them again.*

## Now download command line tools for android SDK

```shell
cd ~
wget https://dl.google.com/android/repository/commandlinetools-linux-9477386_latest.zip
```

```shell
sudo apt install zip unzip
```

```shell
unzip commandlinetools-linux-9477386_latest.zip
```

#### Now copy the commandline folder into android-sdk

***Make sure you put your android sdk path*
```shell
cp -r cmdline-tools/ /usr/lib/android-sdk/
```

#### CD into android-sdlk/cmdline-tools and put the bin & lib folder inside latest folder

```shell
cd /usr/lib/android-sdk/cmdline-tools
```

```shell
mkdir latest
```

```shell
mv bin/ latest/
```

```shell
mv lib/ latest/
```

### Ubuntu server is now configured for building expo android app


## Install EAS and Login into your EAS account

```shell
npm install --global eas-cli
```

```shell
eas login
```

## Go to your expo project folder and Start the build

***Command for development APK build*
```shell
eas build --profile development --platform android --local
```

***Command for production build for internal testing*

```shell
eas build -p android --non-interactive --profile preview --local
```

Now your app should have build without any errors

### NOTE: System requirements for building expo app for android 

CPU: i5 8th gen 6 cores
RAM: 16 GB
