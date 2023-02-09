import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

# Installation

## Javascript SDK

You no longer need to manually install binaries.

All binaries for development and testing are provided with the packages:

* [Choose your Javascript SDK](/develop/smart-contracts/sdk/javascript)


## Precompiled binaries

### Prerequisites

For the local development of TON smart contracts _without Javascript_, you need to prepare binaries of `func`, `fift`, and `lite client` on your device.

You can download and set them up below, or read this article from TON Society:
* [Setting up TON Development Environment](https://blog.ton.org/setting-up-a-ton-development-environment)

### 1. Download
 
Download the binaries from the table below.  Make sure to select the correct version for your operating system and to install any additional dependencies:

| OS          | fift                                                                                            | func                                                                                           | lite-client | Additional dependencies                                                              |
|-------------|-------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|-------------|--------------------------------------------------------------------------------------|
| MacOS M1    | [download](https://github.com/ton-defi-org/ton-binaries/releases/download/macos-m1-0.3.0/fift)  | [download](https://github.com/ton-defi-org/ton-binaries/releases/download/macos-m1-0.3.0/func)       | [download](https://github.com/ton-defi-org/ton-binaries/releases/download/macos-m1-0.3.0/lite-client) | `brew install openssl`                                                               |
| MacOS Intel | [download](https://github.com/ton-defi-org/ton-binaries/releases/download/macos-intel/fift)     | [download](https://github.com/ton-defi-org/ton-binaries/releases/download/macos-intel/func)    | [download](https://github.com/ton-defi-org/ton-binaries/releases/download/macos-intel/lite-client) | `brew install openssl`<br/>`brew reinstall readline`                                 |
| Windows 64  | [download](https://github.com/ton-defi-org/ton-binaries/releases/download/windows-64/fift.exe)  | [download](https://github.com/ton-defi-org/ton-binaries/releases/download/windows-64/func.exe) | [download](https://github.com/ton-defi-org/ton-binaries/releases/download/windows-64/lite-client.exe) | Install [OpenSSL 1.1.1](/ton-binaries/windows/Win64OpenSSL_Light-1_1_1q.msi) |
| Ubuntu 22   | [download](https://ton.org/docs/ton-binaries/ubuntu-22-04/fift)                                 | [download](https://ton.org/docs/ton-binaries/ubuntu-22-04/func)      | [download](https://ton.org/docs/ton-binaries/ubuntu-22-04/lite-client) | `sudo apt install libatomic1 libssl-dev`                                             |
| Ubuntu 20   | [download](https://ton.org/docs/ton-binaries/ubuntu-20-04/fift)                                                     | [download](https://ton.org/docs/ton-binaries/ubuntu-20-04/func)      | [download](https://ton.org/docs/ton-binaries/ubuntu-20-04/lite-client) | `sudo apt install libssl-dev`                                                        |
| Ubuntu 18   | [download](https://github.com/ton-defi-org/ton-binaries/releases/download/ubuntu-18-0.3.0/fift) | [download](https://github.com/ton-defi-org/ton-binaries/releases/download/ubuntu-18-0.3.0/func)      | [download](https://github.com/ton-defi-org/ton-binaries/releases/download/ubuntu-18-0.3.0/lite-client) | `sudo apt install libssl-dev libreadline-dev`                                        |
| Ubuntu 16   | [download](https://github.com/ton-defi-org/ton-binaries/releases/download/ubuntu-16/fift)       | [download](https://github.com/ton-defi-org/ton-binaries/releases/download/ubuntu-16/func)      | [download](https://github.com/ton-defi-org/ton-binaries/releases/download/ubuntu-16/lite-client) | `sudo apt install libssl-dev libreadline-dev`                                        |
| Debian 10   | [download](https://github.com/ton-defi-org/ton-binaries/releases/download/debian-10/fift)       | [download](https://github.com/ton-defi-org/ton-binaries/releases/download/debian-10/func)      | [lite-client](https://github.com/ton-defi-org/ton-binaries/releases/download/debian-10/lite-client) | `sudo apt install libssl-dev libreadline-dev`                                                       |

### 2. Setup your binaries

export const Highlight = ({children, color}) => (
<span
style={{
backgroundColor: color,
borderRadius: '2px',
color: '#fff',
padding: '0.2rem',
}}>
{children}
</span>
);

<Tabs groupId="operating-systems">
  <TabItem value="win" label="Windows">

  1. After downloading, you need to `create` a new folder. For example: **`C:/Users/%USERNAME%/ton/bin`** and move the installed files there.

  2. To open the Windows environment variables, press the <Highlight color="#1877F2">Win + R</Highlight> buttons on the keyboard, type `sysdm.cpl`, and press Enter.

  3. On the "_Advanced_" tab, click the <Highlight color="#1877F2">"Environment Variables..."</Highlight> button.

  4. In the _"User variables"_ section, select the "_Path_" variable and click <Highlight color="#1877F2">"Edit"</Highlight> (this is usually required).
  
  5. To add a new value `(path)` to the system variable in the next window, click the  button <Highlight color="#1877F2">"New"</Highlight>.
  In the new field, you need to specify the path to the folder where the previously installed files are stored:

  ```
  C:\Users\%USERNAME%\ton\bin\
  ```

  6. To check whether everything was installed correctly, run in terminal (_cmd.exe_):

  ```bash
  fift -V -and func -V -and lite-client -V
  ```

  7. If you plan to use fift, you need `FIFTPATH` environment variable with the necessary imports:

     1. Download [fiftlib.zip](/ton-binaries/windows/fiftlib.zip)
     2. Open the zip in some directory on your machine (like **`C:/Users/%USERNAME%/ton/lib/fiftlib`**)
     3. Create a new (click button <Highlight color="#1877F2">"New"</Highlight>) environment variable `FIFTPATH` in "_User variables_" section. 
     4. In the "_Variable value_" field, specify the path to the files: **`/%USERNAME%/ton/lib/fiftlib`** and click <Highlight color="#1877F2">OK</Highlight>. Done.


:::caution important
Instead of the `%USERNAME%` keyword, you must insert your own `username`.  
:::  

</TabItem>
<TabItem value="mac" label="Linux / MacOS">

  1. After downloading, make sure the downloaded binaries are executable by changing their permissions.
   ```bash
   chmod +x func
   chmod +x fift
   chmod +x lite-client
   ```

  2. It's also useful to add these binaries to your path (or copy them to `/usr/local/bin`) so you can access them from anywhere.
   ```bash
   cp ./func /usr/local/bin/func
   cp ./fift /usr/local/bin/fift
   cp ./lite-client /usr/local/bin/lite-client
   ```

  3. To check that everything was installed correctly, run in terminal.
   ```bash
   fift -V && func -V && lite-client -V
   ```

  4. If you plan to `use fift`, also download [fiftlib.zip](https://github.com/ton-defi-org/ton-binaries/releases/download/macos-m1-0.3.0/fiftlib.zip), open the zip in some directory on your device (like `/usr/local/lib/fiftlib`), and set the environment variable `FIFTPATH` to point to this directory.
   
   ```
   unzip fiftlib.zip
   mkdir -p /usr/local/lib/fiftlib
   cp fiftlib/* /usr/local/lib/fiftlib
   ```

:::info Hey, you're almost finished :)
Remember to set the [environment variable](https://stackoverflow.com/questions/14637979/how-to-permanently-set-path-on-linux-unix) `FIFTPATH` to point to this directory.
:::

  </TabItem>
</Tabs>




## Build from source

If you don't want to rely on pre-compiled binaries and prefer to compile the binaries yourself, you can follow the [official instructions](/develop/howto/compile).

The ready-to-use gist instructions are provided below:

### Linux (Ubuntu / Debian)

```bash
sudo apt update
sudo apt install git make cmake g++ libssl-dev zlib1g-dev wget
cd ~ && git clone https://github.com/ton-blockchain/ton.git
cd ~/ton && git submodule update --init
mkdir ~/ton/build && cd ~/ton/build && cmake .. -DCMAKE_BUILD_TYPE=Release && make -j 4
```
## Other sources for binaries

The core team provides automatic builds for several operating systems as [GitHub Actions](https://github.com/ton-blockchain/ton/actions).

Click on the link above, choose the workflow on the left relevant to your operating system, click on a recent green passing build, and download `ton-binaries` under "Artifacts".
