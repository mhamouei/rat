## RAT: Reinforcement-Learning-Driven and Adaptive Testing for Vulnerability Discovery in Web Application Firewalls [[1]](#1)

### Abstract
Due to the increasing sophistication of web attacks, Web Application Firewalls (WAFs) have to be tested and updated regularly to resist the relentless flow of web attacks. In practice, using a brute-force attack to discover vulnerabilities is infeasible due to the wide variety of attack patterns. Thus, various black-box testing techniques have been proposed in the literature. However, these techniques suffer from low efficiency. This article presents Reinforcement-Learning-Driven and Adaptive Testing (RAT), an automated black-box testing strategy to discover injection vulnerabilities in WAFs. In particular, we focus on SQL injection and Cross-site Scripting, which have been among the top ten vulnerabilities over the past decade. More specifically, RAT clusters similar attack samples together. It then utilizes a reinforcement learning technique combined with a novel adaptive search algorithm to discover almost all bypassing attack patterns efficiently. We compare RAT with three state-of-the-art methods considering their objectives. The experiments show that RAT performs 33.53 and 63.16 percent on average better than its counterparts in discovering the most possible bypassing payloads and reducing the number of attempts before finding the first bypassing payload when testing well-configured WAFs, respectively.

### Tutorials
Each file is responsible for a step of the proposed method in [[1]](#1). To run each step you need to run the following command in terminal/cmd:

```
python filename.py <arguments>
```
For example, the following command executes the n-gram tokenizer:
```
python tokenizer.py -i dataset.npy -t tokens.npy -n 2 -o output.npy
```
Arguments of each file are described in the following table.
|File|Short option|Complete option|Description|
|:---:|:---:|:---:|:---:|
|**tokenizer.py**|`-i`|`--input`|Path to the list of attack samples stored in a numpy (.npy) file.|
|"|`-t`|`--tokens`|Path to the list of pre-defined tokens stored in a numpy (.npy) file. For example a pre-defined token for SQLi is "or".|
|"|`-n`|-|The size of n in n-gram.|
|"|`-o`|`--output`|the name of the numpy (.npy) file to store the output in it.|
|**clusterTokens.py**|`-i`|`--input`|Path to the output of the ***tokenizer.py***.|
|"|`-o`|`--output`|the name of the numpy (.npy) file to store the output in it.|
|**binaryEncoder.py**|`-i`|`--input`|Path to the list of attack samples stored in a numpy (.npy) file.|
|"|`-c`|`--cluster`|Path to the output of the ***clusterTokens.py***.|
|"|`-o`|`--output`|the name of the numpy (.npy) file to store the output in it.|
|**autoEncoder.py**|`-i`|`--input`|Path to the output of the ***binaryEncoder.py***.|
|"|`-e`|`--epochs`|The number of training epochs.|
|"|`-o`|`--output`|the name of the numpy (.npy) file to store the output in it.|
|**clusterPayloads.py**|`-i`|`--input`|Path to the list of attack samples stored in a numpy (.npy) file.|
|"|`-f`|`--features`|Path to the output of the ***autoEncoder.py***.|
|"|`-t`|`--tokens`|Path to the list of pre-defined tokens stored in a numpy (.npy) file.|
|"|`-n`|-|The size of n in n-gram.|
|"|`-k`|-|The number of clusters (the size of k in k-means).|
|"|`-d`|`--directory`|Path to the output *directory*.|
|**oracle.py**|`-i`|`--input`|Path to the *directory* that contains the outputs of ***clusterPayloads.py***.|
|"|`-u`|`--url`|The *ip*/url of the WAF.|
|"|`-c`|`--cluster`|The number of clusters (the size of k in k-means).|
|"|`-d`|`--directory`|Path to the output *directory*.|












## References
<a id="1">[1]</a> 
[M. Amouei, M. Rezvani and M. Fateh, "RAT: Reinforcement-Learning-Driven and Adaptive Testing for Vulnerability Discovery in Web Application Firewalls," in IEEE Transactions on Dependable and Secure Computing, doi: 10.1109/TDSC.2021.3095417.](https://doi.org/10.1109/TDSC.2021.3095417)

     Licensed under the Academic Free License version 3.0
