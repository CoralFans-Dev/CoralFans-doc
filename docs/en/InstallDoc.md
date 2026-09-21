# CoralFans Installation

## 0. Read and agree to the disclaimer

As a user, you should first be aware that using the features provided by CoralFans means assuming the risks brought by third-party software. To avoid unnecessary trouble for the developers, please read the following disclaimer. Using CoralFans means you automatically agree to this statement.

> ### Disclaimer
>
> CoralFans (hereinafter referred to as CF) is a Minecraft Bedrock Edition assistant plugin developed based on LeviLamina. It provides amazing convenience for players and creates convenience for technical-survival players. In addition, CF itself is open source and free, contains no malicious code, and in principle will not cause any damage to your save.
>
> However, considering the particularity of this kind of software, the developers cannot fully guarantee that no damage will be caused to users' saves. In case of an accident, the developers will not, and are not able to, take responsibility for users' losses.
>
> If you continue to use the CF plugin, it means you agree to this statement (in other words, the user agreement). If you do not want to bear such risks, please stop using the CF plugin.

## 1. Install LeviLamina

The CoralFans plugin depends on the LeviLamina loader, so before using this plugin, you need to install LeviLamina.

+ For Windows installation, refer to the [LeviLamina installation tutorial](https://levilamina.liteldev.com/install/)

### Notes

+ **Avoid paths containing non-ASCII characters (e.g. Chinese)**
  + This may cause unexpected behavior.
+ **Disable cmd QuickEdit**
  + Windows enables QuickEdit mode in cmd windows by default, which will most likely cause your BDS process to block. Right-click the window title bar, select **Properties**, and disable **QuickEdit Mode**.

## 2. Download and install the prerequisite

1. Install with lip: `lip install github.com/OEOTYAN/BedrockServerClientInterface`

## 3. Download and install the plugin itself

+ Install with lip: `lip install github.com/CoralFans-Dev/CoralFans`
+ Or install manually
  1. Go to the [CoralFans download page](https://github.com/CoralFans-Dev/CoralFans/releases) to download the release file
  2. Put the extracted plugin into the `plugins` folder under the server root directory

### Client edition

+ Since 26.10, CoralFans also provides a client edition, which works with the client edition of LeviLamina
+ Install with leviLauncher: find CoralFans on the Bedrinth page in leviLauncher and install it
+ Install with lip: `lip install github.com/CoralFans-Dev/CoralFans#client`
+ For manual installation, extract the client-edition archive into the client `mods` folder

## 4. Configure the configuration file

You may need to disable some features (such as `tick`, hopper counter, etc.) according to your needs.

## 5. Start the server

For a local server, fill in `127.0.0.1` or `localhost` in the **ip** field.

For a cloud server, fill in its public IP (ask your provider if you don't know it). The port follows the server configuration file; the default is `19132`.
