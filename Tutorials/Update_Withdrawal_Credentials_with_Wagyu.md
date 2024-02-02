# Update your Validator's Withdrawal Credentials<br>— with Wagyu Key Gen

If you prefer videos, there is a community member by the name of Remy who was so generous as to make a Youtube video for using this Wagyu Key Gen tool (only covers the withdrawal credential update part of the tool), and his video can be found [here](https://www.youtube.com/watch?v=EMQoVtxNaxo).

Before you start, you should collect the following info somewhere handy, so you can do this process offline for best security. For items C and D, browse to [https://mainnet.beaconcha.in](https://mainnet.beaconcha.in) (if your validator is on a testnet, use the appropriate site for your validator) and locate your public validator dashboard for each validator in your set.

|       | Worksheet Data: |
| ---   | :--- |
| **A** | The 24-word mnemonic for your validator, or set of validators. |
| **B** | The ETH wallet address you want your validator rewards to be sent to during the network sweep that occurs approximately every 7 days, and also where you want your 32ETH stake to be sent to when you exit the validator in the future. This can be any ETH wallet address in a wallet you control and have the keys to. |
| **C** | For each validator, the validator's public index ID (1-7 digit unique identifier for every validator, at the top of the dashboard)<br>![example image](images/BC003.jpg) |
| **D** | For each validator, the old BLS withdrawal credentials of the validator. Look for the Deposits tab, click the copy button for the 0x00-style credentials under the “Withdrawal Cred.” column as shown, and paste it on your worksheet.<br>![example image](images/BC004.jpg) |
| **E** | (not on any website) For each validator, you will need the unique validator position index which matches the above collected info. If you created more than one validator with the above mnemonic (including validators created but not deposited to), see the Section 4 tutorial on position indexes [here](Understanding_Validator_Position_Indexes.md). Otherwise, your validator position index is likely 0 by default, the first validator in any set. |

<br>

1. Browse to [https://github.com](https://github.com) and find the “stake-house/wagyu-key-gen” program, and click on “releases“ on the right side of the page. The last release I tested for this tutorial is titled “Version 1.7.0”, but newer releases should also work the same. Or navigate to [https://github.com/stake-house/wagyu-key-gen/releases/](https://github.com/stake-house/wagyu-key-gen/releases/).
2. Scroll down to “Assets” and download the version appropriate to your system. For Windows systems, choose the file that ends with “.exe”. This is a single exe file stand-alone application, so there is no install process.
3. If you're on an online system, for good security practices, you should now disconnect your computer from the internet or turn off your WiFi. Even better, move the program (single executable file) to an air-gapped computer for the sensitive operations with your mnemonic seed words.
4. Locate and run the newly downloaded Wagyu Key Gen program. You can also type “Wagyu Key Gen” in your Start menu to find it.
5. Click <code>USE EXISTING SECRET RECOVERY PHRASE</code>
6. Select your network, and click <code>OK</code>.
7. Click <code>GENERATE YOUR BLS TO EXECUTION CHANGE (ADD A WITHDRAWAL ADDRESS)</code>
8. Type the 24-word mnemonic for your validator (Worksheet Data #A), and click <code>IMPORT</code>
9. Fill in the boxes with the following information:
    * <code>[start index]</code> — Enter the validator position index of the validator, or of the first validator if you have a set (Worksheet Data #E). If you created more than one validator with the above mnemonic (including validators created but not deposited to), see the Section 4 tutorial on position indexes [here](Understanding_Validator_Position_Indexes.md).
    * <code>[indices or validator indexes]</code> — Enter the 1-7 digit validator public index ID as identified on the public blockchain (Worksheet Data #C). If you are signing for a batch of more than one validator all at once (must be consecutive without gaps), list their respective validator public index ID's in the same ascending order as their position indexes, separated by commas.
    * <code>[BLS withdrawal credentials]</code> — Enter the old BLS withdrawal credentials that your validator currently has (Worksheet Data #D). If you are signing for a batch of more than one validator all at once (must be consecutive without gaps), list their respective old BLS withdrawal credentials in the same ascending order as their position indexes, separated by commas.
    * <code>[Ethereum Withdrawal Address]</code> — Enter the ETH address you want your validator rewards to be sent to in the future. This is any ETH address in a wallet you own (Worksheet Data #B). If you are signing for a batch of more than one validator all at once, this address will be locked to all of the validators being signed for.
> [!CAUTION]
> *As this step is critical and can only be done once, make sure this ETH wallet address is one you have the keys to and have full control of. This address can NOT be changed more than once during the life of your validator. This will permanently lock the withdrawal address of your validator to this wallet address, and your rewards and your entire 32ETH stake will go there in the future when your validator exits. <ins>Do not lose control of this wallet address in the future!!</ins>*
10. Click <code>NEXT</code>.
11. Choose a folder to save your signed message, and click <code>CREATE</code>. The page will show a summary, and you can now close the program.
13. Go back online (or copy the resulting JSON file to your online computer) and navigate to [https://mainnet.beaconcha.in/tools/broadcast](https://mainnet.beaconcha.in/tools/broadcast). (if your signed message is for a testnet, navigate to a site that will publish testnet messages instead)
14. Check the file contents for accurancy, and then upload the JSON text file that you just had created, and click <code>Submit & Broadcast</code>. You can also copy and paste the text contents of the file instead. This file will have a name like: <code>“bls_to_execution_change-xxxxxxxxxx.json”</code>
15. The signed withdrawal credential update instruction will now be sent out to a network node. The update should be finalized on the network within 10 minutes. You can check the Deposits tab of your beaconcha.in validator dashboard page to see the change go into effect.<br>
![example image](images/BC005.jpg)

<br>

[Back to Home](/../main/README.md)
