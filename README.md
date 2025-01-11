<h1>Network File Share and Permissions)</h1>
This tutorial explains how to create file share folders for domain users and admins, and how to set up access permissions

<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- Windows' File Explorer

<h2>Operating Systems Used </h2>

- Windows Server 2022 (DC-1)
- Windows 10 (22H2) (Client-1) user name: box.cerula

<h2>High-Level Deployment and Configuration Steps</h2>

***Prereqs: Create an Azure VM DC-1 (Windows Server 2022) and Create an Azure VM Client-1 (Windows 10 (22H2))***

 - Step 1: Connect/log into DC-1 as your domain admin account (mydomain.com\jane_admin). Connect/log into Client-1 as a normal user (mydomain\<box.cerula>)
 - Step 2: On DC-1, on the C:\ drive, create 4 folders: “read-access”, “write-access”, “no-access”, "accounting"
 - Step 3: Set the following permissions (share the folder). Folder: “read-access”, Group: “Domain Users”, Permission: “Read”. Folder: “write-access”,  Group: “Domain Users”, 
           Permissions: “Read/Write”. Folder: “no-access”, Group: “Domain Admins”, “Permissions: “Read/Write”
 - Step 4: Access file shares as a normal user (on Client-1 VM). On Client-1, navigate to the shared folder (start, run, \\dc-1). Try to access the folders you just created.
 - Step 5: Create an “ACCOUNTANTS” Security Group in the Windows C: drive and assign permissions through the accountant's folder on explorer.
 - Step 6: Test accounting access: Log out of Client-1 (user). Configure permission access on DC-1 for Client-1 (user) to be an 'ACCOUNTANTS member. Log back into Client-1 (as 
           user).

<h2>Deployment and Configuration Steps</h2>

<p>
<p>
Step 1: Open Remote Desktop and 'Log into' the DC-1 as your domain admin account (mydomain.com\jane_admin). Also, 'Log into' Client-1 as user (mydomain.com\box.cerula)
  
![image](https://github.com/user-attachments/assets/2bab07bb-a3c6-4b81-83a0-243c9edb8abb)


![image](https://github.com/user-attachments/assets/97e7b3cb-9535-42b0-a0c5-0ce7b758f97b)

</p>

</p>
<br />

<p>

Step 2: On DC-1. Select the Windows icon, and select the 'File Explorer' file located on the 'Windows Server' panel.

![image](https://github.com/user-attachments/assets/bd0d6b12-b023-44e6-898e-17962916ef07)

       On the DC-1. Select the 'This PC' file, select the 'Windows (C:)' file, use the Right-click option in the file to create a new folder. Select 'New", then select 'folder' 

![image](https://github.com/user-attachments/assets/1b960365-13d6-44ca-8658-8ef8f1556ba7)


       create 4 folders: “read-access”, “write-access”, “no-access”, “accounting” 

![image](https://github.com/user-attachments/assets/9fb44026-1c46-4d62-902a-d37f2c4d4eed)

</p>

</p>
<br />

<p>
  
Step 3: Set the following permissions to allow user's access folders. 
       Folder: “read-access”, Group: “Domain Users”, Permission: “Read”
       Folder: “write-access”,  Group: “Domain Users”, Permissions: “Read/Write”
       Folder: “no-access”, Group: “Domain Admins”, “Permissions: “Read/Write”


***(The instructions a-d will need to be repeated for the other folders according to step 3 instructions)***

READ-ACCESS FOLDER:

      a. Select the Folder: “read-access”, by right-clicking select the 'Properties' option. 
![image](https://github.com/user-attachments/assets/6301baaa-352f-4c0d-abf6-03e6aea01bd3)

      b. Select the 'Sharing' tab. Select 'Share...'
![image](https://github.com/user-attachments/assets/46705c70-c0d8-4b1a-a840-8be92d8700c2)

      c. Type “Domain Users” on the search menu. select 'Add'.
![image](https://github.com/user-attachments/assets/64a347dd-3fab-4a55-8b9f-f700a73eaf55)

      d. On the 'Permissions Level' menu, select 'Read'. Select 'Share'. Then select 'Done' and 'Close'.
![image](https://github.com/user-attachments/assets/ecfeead9-9889-4329-8673-1fe05118379c)
      
WRITE-ACCESS FOLDER: (this image shows the final a-c steps)

     d. On the 'Permissions Level' menu, select 'Read/Write'. Select 'Share'. Then select 'Done' and 'Close'.
   ![image](https://github.com/user-attachments/assets/1ac423aa-3ff5-4a30-a0fc-c29cf2c7df58)

NO-ACCESS FOLDER: (perform steps a and b)

     c. Type “Admin Users” on the search menu. select 'Add'. 
![image](https://github.com/user-attachments/assets/d0eafa03-ba3f-4979-9f01-aa38f2c23abd)

     d. On the 'Permissions Level' menu, select 'Read/Write'. Select 'Share'. Then select 'Done' and 'Close'.
![image](https://github.com/user-attachments/assets/67f02b44-eac8-4028-816e-6583cca9f9ed)

</p>

</p>
<br />
Step 4: On Client-1, navigate to the shared folder by selecting the 'Windows icon', right-click select 'run' option, type: '\\dc-1'

![image](https://github.com/user-attachments/assets/19c2f239-7b0e-4591-a5ed-68160f4e701c)

![image](https://github.com/user-attachments/assets/68cb751d-1d5d-4ade-97d6-0b5a061872e6)

    Observe that the DC-1 files appear. Attempt to access all files. Notice the 'Network Error' pop-up window appears due to no domain user permission given. 

![image](https://github.com/user-attachments/assets/37344d97-c755-48ac-9604-4ba62137c6c3)

</p>

</p>
<br />

Step 5: In DC-1, Select 'Windows icon', select the 'Windows Administrative Tools', select the 'Active Directory Users and Computers' option. Select and Right-click on '_Group', select 'New', then select the 'Group' option.

![image](https://github.com/user-attachments/assets/9c688b0d-2501-4fbb-9c36-b04338388347)

     Type: “ACCOUNTANTS” under the  Group name. Select 'Ok'.

![image](https://github.com/user-attachments/assets/1bb79429-d893-4ccd-b444-ce9305ba0b87)

     Return back to the Windows C: drive on 'File Explorer'. Select the 'accounting' folder. On its right-click menu, select 'properties', then select 'sharing' tab and click the 'share...' option.  Type: 'accountant' on the search menu, then select 'Add'.  
     
  ![image](https://github.com/user-attachments/assets/680150bf-0c13-4178-b35f-004fd9ca0df3)

     To create permission, make sure the 'Permission Level' category selection is 'Read/Write'. Select 'Share', and 'Done' and 'Close'.
     
  ![image](https://github.com/user-attachments/assets/0a061b2e-55e2-47e8-8324-608f3b5b2113)
</p>

</p>
<br />

<p>
Step 6: Log out of Client-1 (user: box.cerula). In 'Active Directory Users and Computers', select '_GROUP' file, then double-click the 'ACCOUNTANTS' folder. Select the 'memeber' tab, then select 'Add'. Type: (user name) 'box.cerula' in the description: 'Enter the objects name to select'. Select 'Check Names', then select 'ok'. Notice that the user name: box. cerula is listed. 
 
![image](https://github.com/user-attachments/assets/ae60f0a0-f69f-4ec9-a8a7-17558c817e43)

     Log back into Client-1 (user: box.cerula). Open 'File Explorer'. on the search menu type: '\\dc-1, and enter. 

![image](https://github.com/user-attachments/assets/fc343945-b438-4e91-962f-6c4ade7636fd)

     Double-click the 'accounting' folder to access it. Notice that it has access to the accounting folder. 

![image](https://github.com/user-attachments/assets/4c3570d4-9aa2-48a6-9fd2-624ca1d81e06)


</p>

</p>
<br />
