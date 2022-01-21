# js-sdk-demo User Guide

---
##Solution #1: Recommend to use webstorm 
 1. Download and Install node
 2. Download and install webstorm, open front-end project
 3. npm install
 ![](https://camo.githubusercontent.com/abd6d85291f4089583d9dc04368dffd780adaa69/68747470733a2f2f77696b692e6368696e616e657463656e7465722e636f6d2f68746d6c2f646f632f2f32303138313131352f31353432323733373337333139696d6167652e706e67)
 
 4. npm run dev
 ![](https://camo.githubusercontent.com/30f2cf57cd4599d5da9267832924704b93bdccc1/68747470733a2f2f77696b692e6368696e616e657463656e7465722e636f6d2f68746d6c2f646f632f2f32303138313131352f31353432323733373636383331696d6167652e706e67)
 
 5. Start backend project
 6. Set proxy address and proxy backend project port to solve cross-domain problems
 ![](https://camo.githubusercontent.com/618cd65f74eb0c61ceb75b2572e9e1f825391156/68747470733a2f2f77696b692e6368696e616e657463656e7465722e636f6d2f68746d6c2f646f632f2f32303138313131352f31353432323733393638313933696d6167652e706e67)
 
 7. Enter test/demo1 testpage

##Solution 2: Use nodes directly
1. Download and install node
2. cmd enters the root directory of the front-end project
3. npm install
4. npm run dev
5. Start backend project
6. Set proxy address and proxy backend project port to solve cross-domain problems
7. Enter test/demo1 testpage

##Scenario 3: Using Tomcat, This option doesn't make package with wcs.min.js because frontend project is changed
1. Set configuration at webapp in the Front-end files 
2. Provide getUploadToken interface in java


## Scenario 4: Use nginx, This option doesn't make package with wcs.min.js because frontend project is changed
1. Use alias on the frontend
2. Use proxy_pass to proxy the getUploadToken interface on the backend


