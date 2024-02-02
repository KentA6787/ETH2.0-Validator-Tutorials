# Restoring/Recreating your Keystore Files<br>— with Staking-Deposit-CLI

A keystore file is a JSON text file that you may have created when you created your validator in the beginning. This file contains your validator’s basic info and its private key, and the file is encrypted with a password you chose. The following process will help you restore/recreate that keystore file. If you have already completed the section in this tutorial for updating your validator withdrawal credentials, you already have the needed software downloaded, and you can skip the steps 1-4 below.
Before you start, you should have handy, your 24-word mnemonic (seed phrase) for your validator.

1. Browse to [https://github.com](https://github.com) and find the “ethereum/staking-deposit-cli” program, and click on “releases“ on the right side of the page. The last release I tested for this tutorial is v2.5.0, titled “BTEC in the specs, check”. Or navigate to [https://github.com/ethereum/staking-deposit-cli/releases](https://github.com/ethereum/staking-deposit-cli/releases).
2. Scroll down to “Assets” and download the version appropriate to your system. This tutorial is written only for Windows systems, so choose the file that ends with “.zip”.
3. In Explorer, locate the compressed zip file you just downloaded, and extract the contents. To easily extract compressed files in Windows, right click on the file and select <code>Extract All...</code>.
4. Within the new folder you just extracted the files to, navigate in until you find the “deposit.exe” file, and move that file to any folder of your choice that has a short path that has no spaces in it. You will need to type this path a couple times later, so if it’s shorter, your task will be easier.
5. If you’re on an online system, for good security practices, you should now disconnect your computer from the internet or turn off your WiFi. Even better, move the program (single executable file) to an air-gapped computer for the sensitive operations with your mnemonic seed words.
6. From your start menu, run your Command Prompt app. (Windows PowerShell app works just as well)
7. Type or copy/paste the following command changing the <code>[FolderPath]</code> to wherever you put that deposit.exe file, and then press enter:<br><code>[FolderPath]\deposit.exe existing-mnemonic</code><br>For example:<br>![example image](/../main/images/CP002.jpg)
8. Follow the prompts, pressing enter after each:
    * Type the number for your preferred language, or press enter for the default option.
    * Enter the 24-word mnemonic for the validator.
    * Enter the zero-based position index number of the first validator in the set that you wish to recreate keystore files for. If you only created one validator with the above mnemonic (including validators you created but never deposited to), enter 0 for the first validator in the set and enter 1 for the next prompt. Keystore files will be sequentially recreated, starting first with the validator position index value entered here, and encompassing a sequential range of validators as large as the number entered in the next prompt. For example, if you choose 2 here for the starting validator position index, and you choose 3 in the next prompt for the total number of validators, three keystore files will be created for validators with position indexes 2, 3, and 4, and validators with position indexes 0 and 1 will be skipped. See the Section 4 tutorial on position indexes [here](/../main/Tutorials/Understanding_Validator_Position_Indexes.md).
    * Repeat the above, to confirm.
    * Enter the total number of validators you have previously created under the same mnemonic you entered above, including validators you never deposited to. This will define the size of the set of validators you want to recreate the keystore files for.
    * Press enter for the mainnet. If your validator is on a testnet, choose the correct network name.
    * Create and enter a password of your choice. This password will only be used to encrypt the keystore files on your computer, and has no effect on the validator or the network.
    * Re-enter that password, to confirm it.
9. The program has now created your encrypted keystore JSON files (one file for each validator) and saved them in your Windows Users folder, using the filename format <code>keystore-m_12381_3600_**X**_x_x-xxxxxxxxxx.json</code>, where the bold **X** in this filename example is the validator position index of the specific validator whose info is contained inside that file. (Note: If in doubt, you can identify the Windows Users folder for your machine, by opening a File Explorer window and typing <code>%userprofile%</code> in the box)
10. You can now close the Command Prompt app. Sensitive tasks are complete, so you no longer need to be offline anymore.
11. <i>(optional step, but recommended)</i> To verify that you created a valid keystore file as expected that has the correct validator info in it, open each file in a text editor (i.e. right-click > Open With > Notepad), and check the “pubkey" field and make sure it matches the public key of the corresponding validator (the “0x” prefix is sometimes truncated). A public key for any validator is displayed in any dashboard, or on the public [beaconcha.in](https://beaconcha.in/) validator dashboard page for your validator.

![example image](/../main/images/BC001.jpg)<br><br>![example image](/../main/images/KS001.jpg)

<br>

[Back to Home](/../main/README.md)
