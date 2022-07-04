---
title: Node.js Install
date: 2022-07-04 09:26:58
tags: #node.js #En
---

## Basic Step  
1.First Install from the [Official Website](https://nodejs.org/en/)  
2.Install [Reference Install](https://blog.csdn.net/Small_Yogurt/article/details/104968169)  

## Solve WARN 
```npm WARN config global `--global`, `--local` are deprecated. Use `--location=global` instead ``` 
##### My initial version is 8.11, windows 10.  

A common solution is to edit `npm.cmd`, change `prefix -g` to `prefix --location=global`.  
However, this doesn't work well for my version. Because when I test `npm install express -g`, this problem still exists.  
The main problem is the version, the new ver has already solved it. So, what we need to do is to update.  
**But**, on windows, you cannot directly input `nmp install -g npm` on cmd.  
Below is what I did to solve this. [Reference](https://blog.csdn.net/m0_59751822/article/details/125229851?spm=1001.2014.3001.5502)  
#### Step 1. Complete the configuration of environment variables  
1.  Create two folders`node_global` and `node_cache` in your nodejs installation directory, create one folder `node_modules` under the `node_global` folder.  
2. open cmd, do what shown below.
```
npm config set prefix "创建的node_global文件夹所在路径"  
npm config set cache "创建的node_cache文件夹所在路径"  
```  

3. In Environment Variables  
3.1 In System Variables  
Create a new variable named `NODE_PATH`, the variable value  is the location of the new `node_modules` you created.
3.2 In System Variables  
Open the variable named  `path`, add two new address `Your nodejs directory\node_global` and `%NODE_PATH%`.  
3.3 In User Variable  
Open the variable named  `path`, change the address like `......\Roaming\npm` to `Your nodejs directory\node_global`  
3.4 Save your changes  
#### Step 2. Open the permission of your node.js  directory.  
#### Step 3. Main Progress  
##### 3.1  Operations on cmd  
1. Type "cmd" in the search box on the desktop taskbar and click "Run as administrator".
2. input `npm install -g npm-windows-upgrade`, you should see the **WARN**.  

##### 3.2 Operations on Windows PoweShell  
1. Still, "Run as administrator".
2. Type `set-ExecutionPolicy RemoteSigned`, Press enter and the option to change the enforcement policy will be displayed; we type `Y` and press enter; 
3. Type `npm-windows-upgrade`;then each version will be displayed, use the arrow keys ↑ ↓ to select, default is the newest version, so just press enter. Wait a few moments and the update will be completed.

##### 3.3 Test  
We type `npm -v` in the command prompt box and we can see that even if we don't change the npm.cmd file, we won't get an error