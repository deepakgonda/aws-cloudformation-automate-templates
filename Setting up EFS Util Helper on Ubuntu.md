### Run Following Commands to install amazon-efs-utils
```console
cd /mnt/
mkdir efs
cd /mnt/
sudo mkdir efs
sudo chmod 777 -R efs
sudo apt-get -y install git binutils
git clone https://github.com/aws/efs-utils
cd ./efs-utils
./build-deb.sh
sudo apt-get -y install ./build/amazon-efs-utils*deb
```

2. Create New Security Group for EFS Drive and open NFS Port 2049
3. Now Go to your AWS Account, Create One EFS Drive By Using Customize Option and assign the Security Groups created to each subnet.
4. Create Access point by just giving a name to it and keep other options default
5. Click on Attach and copy the command similar to below

```console
sudo mount -t efs -o tls,accesspoint=fsap-0c3182c15477957e2 fs-e8a215a8:/ /mnt/efs
```

6. Run following command to confirm if you have mounted successfully
```console
df -h
```
7. You should see listing similar to below:
....
....
127.0.0.1:/     8.0E     0  8.0E   0% /mnt/efs


8. Now try adding one test file
```console
sudo chmod 777 -R /mnt/efs/
cd /mnt/efs/
touch abc.txt
```

