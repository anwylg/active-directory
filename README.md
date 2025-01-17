## Configuring Active Directory with Windows
This project shows how I configured a Active Directory within Windows

## Environments and Technologies Used
* Oracle Virtualbox
* Active Directory Domain Services
* DNS
* DHCP
* PowerShell

## Operating Systems Used
* Windows 2019 Server
* Windows 10

## Deployment and Configuration Steps

### <p align="center">  Creating the DC virtual machine </p>

Create your first virtual machine with these settings here and use the Windows 2019 Server.iso: <p align="center">  ![Image](https://github.com/user-attachments/assets/930493a6-64b4-4477-8539-6566e8899d88) </p>

Now we need to add a internal network so our 2nd virtual machine can connect to this domain controller: <p align="center"> ![Image](https://github.com/user-attachments/assets/e5f5c74e-1570-4aee-ba99-139828782494) </p>

Opening up the virtual machine and going through the setup using this setting: <p align="center"> ![Image](https://github.com/user-attachments/assets/18f6e5bb-fc4e-4686-8350-ff53e6796202) </p>

###  <p align="center"> Configuring networks and Instaling Active Directory </p>

With Windows Server 2019 being installed, the home screen should pop up like this:<p align="center"> ![Image](https://github.com/user-attachments/assets/0209d342-5521-42fe-9dcd-79a5da2e7b35) </p>

We will first distinguish our actual wifi network and our private network: <p align="center"> ![Image](https://github.com/user-attachments/assets/b033749a-a135-4ea7-9d46-04f477869b97) </p> <p align="center"> ![Image](https://github.com/user-attachments/assets/d718cb5e-1833-4770-8c51-091df1937a0f) </p> <p align="center"> ![Image](https://github.com/user-attachments/assets/e43fca19-718d-4c5f-bd2e-d92015edfe9a) </p> <p align="center">  ![Image](https://github.com/user-attachments/assets/e588d69a-5cba-487e-a4b5-7608720d3921) </p>


Configuring our internal network:  <p align="center">   ![Image](https://github.com/user-attachments/assets/89eb742a-b6a3-4c6e-b915-da4907051a04) </p>

Adding Active Directory Domain Services: <p align="center"> ![Image](https://github.com/user-attachments/assets/0b8ce3dd-390e-47e9-8b04-fc38f08b0650) </p>

Set our root domain name to myitproject.com: <p align="center">![Image](https://github.com/user-attachments/assets/c5bfa1db-ea26-4097-910d-006e3f40df86) </p>

Add a organizational unit(OU) and a user named John Doe:<p align="center"> ![Image](https://github.com/user-attachments/assets/78d94fa3-cc5a-47f0-a0f4-07142de7ebb1) </p>

Set the John Doe user as a admin:<p align="center"> ![Image](https://github.com/user-attachments/assets/f669e506-906b-48d4-b7db-cefd7752cc97) </p>

Log in into the new John Doe admin account:<p align="center"> ![Image](https://github.com/user-attachments/assets/5e138c59-6737-476f-85e6-75dc76a08622) </p>

### <p align="center"> Configuring Remote Access and DHCP Server </p>

Add in Remote Access:<p align="center"> ![Image](https://github.com/user-attachments/assets/6fb1196f-1677-4af0-a4b6-45dab571d5b0) </p>

Also add in the option Routing:<p align="center"> ![Image](https://github.com/user-attachments/assets/c12eb97a-68b7-4aa3-8ea5-6b864cd95c1d) </p>

Open up the Routing and Remote Access tool and we need to configure our INTERNET network: <p align="center"> ![Image](https://github.com/user-attachments/assets/0ec0fc29-cf94-4625-b67e-aafcff17efc4) </p>
 ![Image](https://github.com/user-attachments/assets/d11b50ef-617c-436f-9d84-2fd98a085ebe) </p>
 ![Image](https://github.com/user-attachments/assets/51ab20b5-93a5-422e-b73d-3054e6e48a42) </p> 

Add in DHCP Server: <p align="center"> ![Image](https://github.com/user-attachments/assets/9de4347b-bad0-45fb-bc4d-1e8c492c4114) </p>

Open up the DHCP tool and we need to add in a new scope to authorize the server: <p align="center"> ![Image](https://github.com/user-attachments/assets/b96f0999-7004-492d-ade4-bb229d74b2d2) </p> <p align="center">  ![Image](https://github.com/user-attachments/assets/0cd937a5-a955-4ba2-9f6f-699a1838400c) </p> <p align="center">  ![Image](https://github.com/user-attachments/assets/55ffb75f-e3f0-4ed0-8ec5-e6d59d1eafd6) </p>  <p align="center">  ![Image](https://github.com/user-attachments/assets/275a9d22-e76d-4180-8123-d0f48f663196) </p>

### <p align="center"> Using PowerShell to create users </p>

Let's open up PowerShell and add in the users using these scripts from (https://github.com/joshmadakor1/AD_PS/archive/master.zip) to our DC virtual machine <p align="center">![Image](https://github.com/user-attachments/assets/b28927f7-d25b-49df-b5d2-74bb6bcf2e80) </p>

### <p align="center"> Using CLIENT 01 Virtual machine </p>

Creating a new virtual machines for our CLIENT01 to connect to. We will be using our Windows 10.iso : <p align="center"> ![Image](https://github.com/user-attachments/assets/5b534d84-afdb-40cb-9952-fc6e4ea8a154) ![Image](https://github.com/user-attachments/assets/db950e8d-6a6d-41b7-a4d5-f98c4860b4b1) </p>

After installing Windows, we need to check just in case if the virtual machine is getting internet by using the cmd to ping our private network:<p align="center"> ![Image](https://github.com/user-attachments/assets/04d84864-b497-488b-80ab-9f2baad29b66) </p>

Now let's add in our domain to this virtual machine:<p align="center"> ![Image](https://github.com/user-attachments/assets/a205086f-a821-4f61-a8f3-bef183062fb7) </p>

If we check our DC machine, we can check if CLIENT01 is actually connected to the network:<p align="center"> ![Image](https://github.com/user-attachments/assets/495738fa-52aa-41cc-9624-2793c3a9c4ad) </p> <p align="center"> ![Image](https://github.com/user-attachments/assets/967a1346-5b9a-483f-a7b8-283f3f1adbea) </p>

Now use any username that was created by the PowerShell script:<p align="center"> ![Image](https://github.com/user-attachments/assets/e1a9b199-2026-46d2-ac34-ddf5be53f720) </p>

### Resources: https://www.youtube.com/watch?v=MHsI8hJmggI&t=1486s 











