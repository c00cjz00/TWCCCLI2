# TWCC-CLI Project

> we cook twcc-cli


:::info

NOTE:

Please update your TWCC-CLI constantly to make sure all functionalities works up-to-date, thanks! 

any questions: please check on https://www.twcc.ai/doc?page=deploy_env_cli or email to isupport@narlabs.org.tw THANKS!

:::

INDEX: 
1. [S3](doc/S3_tutorial.md)
1. [Customized Image](doc/Customed_Img_Tutorial.md)


UPDATED:
- Please follow instructions in [TWCC MANUAL](https://www.twcc.ai/doc?page=deploy_env_cli), thanks!


A. 下載 twcc cli 

 1. git clone https://github.com/c00cjz00/TWCCCLI2.git
 2. cd TWCCCLI2/
 3. bash tools/twcc_env.sh
 4. pipenv install
 5. pipenv run python src/test/gpu_cntr.py
 6. Enter your key @ twcc.ai
 7. select your project
 8. 建立開發型容器
 pipenv run python src/test/gpu_cntr.py create-cntr [-cntr Container name] [-gpu Number of GPU] [-sol Solution Name] [-img Image Name] [-wait T/True or F/False <Wait for CNTR to ready or not>]
 9. 檢視所有映像檔類型
 pipenv run python src/test/gpu_cntr.py list-sol 
 10. 檢視所有映像檔
 pipenv run python src/test/gpu_cntr.py list-all-img
 11. 檢視容器資訊	
 pipenv run python src/test/gpu_cntr.py list-cntr -site 93072 -table False
 pipenv run python src/test/gpu_cntr.py list-cntr -all
 12. 刪除容器
 pipenv run python src/test/gpu_cntr.py del-cntr 93072

B. 自動連線
 1. cd ~/
 2. ssh-keygen
 2. create a container
 3. ssh-copy-id -i ~/.ssh/id_rsa.pub c00cjz00@203.145.219.140 -p 57031 
 4. ssh -p  57031 c00cjz00@203.145.219.140 

C. PHP code 連線
 1. cd php
 2. 編輯configure file
 joe 00-containerFunc.php
 $twccCliBinPath="/home/ubuntu/git/TWCC-CLI";
 3. 建立容器
 php 01-createContainer.php mytensorflow 1 TensorFlow 'tensorflow-19.11-tf2-py3:latest'
 4. 列出啟動內容
 php 02-listContainer.php
 5. ssh 連線派送指令
 php 03-ssh2Container.php 766468 'pwd;date;ls;pwd;'
 6. 上傳檔案至container
  php 04-scpUploadToContainer.php 766594 '/home/c00cjz00/pythonCode' '/tmp/'
 7. 從container下載檔案
 php 05-scpDownloadFromContainer.php 767011 '/tmp/model01.pkl' '/home/ubuntu/git/TWCC-CLI/php/model'
 8. 刪除容器
 php 04-delContainer.php 766468
 9. 總和指令
 php demo.php mytorch 1 TensorFlow 'tensorflow-19.11-tf2-py3:latest' \
 'sudo -i pip install --upgrade pip; sleep 2; sudo -i pip install fastai; sleep 3; ipython ~/fastaiDemo/00-firstClass-TrainingSimple.ipynb;' \
 '/tmp/model01.pkl' \
 '/home/ubuntu/git/TWCC-CLI/php/model/'
