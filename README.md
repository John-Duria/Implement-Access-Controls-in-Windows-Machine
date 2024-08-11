<p align="center">
<img src="https://upload.wikimedia.org/wikipedia/commons/c/cb/Ec_Council_Logo.png">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Implement Access Controls in Windows Machine</h1>

This lab was purchased through EC- Council. Copyright © 2021 by EC-Council.

This tutorial outlines the implementation of access controls policies in a Windows Active Directory Machine.

<h2>Environments and Technologies Used</h2>

- Active Directory Domain Services
- PowerShell
- Group Policy Management
  
<h2>Operating Systems Used </h2>

- Windows Server 2022

<h2>Task</h2>

- Task 1. Examine current Administrator account properties using Powershell.
- Task 2. Create Organizational Unit and Users Active Directory.
- Task 3. Create new Groups and add accounts in Organizational Unit.
- Task 4. Add computers into Organizational Unit and create a detailed report(.TXT file) of all computer objects in the domain using powershell.
- Task 5. Modify the existing Group Policy Management (GPO) to set password requirements.
- Task 6. Generate a report of password policy settings using Powershell to update the configuration documentation.

<h2>Configuration Steps</h2>

Task 1: Examine current Administrator account properties using Powershell.

Step 1. Go to your Windows Active Directory Domain Controller and Click Start icon on the Desktop, right-click Windows PowerShell and navigate to More-->Run as administrator. 

![image](https://github.com/user-attachments/assets/b845d9e8-d9c7-4df9-a443-afbbadc0bf24)

Step 2. In the PowerShell, type whoami /user and press Enter to display the details regarding Security ID (SID) and other additional information of the current user.

![image](https://github.com/user-attachments/assets/2bc4bda2-dd1b-4eb1-a77e-ab7b946335ab)

User accounts are identified in the system by their unique numbers. In Windows, this number is the Security Identifier (SID). In Linux, it is the User Identifier (UID).

Step 3. Type get-aduser -identity administrator -properties * and press Enter to display user account information. 

![image](https://github.com/user-attachments/assets/70a762cb-617c-4a0e-bbea-a017fc97a7dd)

Task 2. Create Organizational Unit and Users Active Directory.

Step 1. Minimize the Windows PowerShell window. Click Start icon in the Desktop, click Server Manager. 

![image](https://github.com/user-attachments/assets/0604e054-9b26-4d9a-a425-7019221997c4)

Step 2. Click Tools at the top right corner of the window and select Active Directory Users and Computers option. 

![image](https://github.com/user-attachments/assets/5c4a46c8-536d-4144-a4fd-de6c69816fe6)

Step 3. Right-click CCT.com domain and navigate to New --> Organizational Unit. 

![image](https://github.com/user-attachments/assets/80b92432-0603-4040-a290-38d4b6309571)

Step 4. New Object - Organizational Unit pop-up appears, type NetworkAdmin in the Name field and click OK.

![image](https://github.com/user-attachments/assets/6635710e-bc5e-406a-83c2-9dc92de9b970)

Step 5. Right-click NetworkAdmin Organizational Unit, navigate to New --> User.

![image](https://github.com/user-attachments/assets/666bc0f8-1dd4-41fb-8497-96788fe3800d)

Step 6. The New Object - User window appears, enter the following details and click Next:
  First name: IT
  Last name: Head
  User logon name: IT_Head

![image](https://github.com/user-attachments/assets/65123b74-95f1-4ce0-99d0-9a2b1468a6c4)

Step 6. Enter test@123 in both Password and Confirm Password fields. Uncheck User must change password at next logon and check Password never expires option. Click Next.

![image](https://github.com/user-attachments/assets/e676da8c-2a35-4fd4-9503-a7185e02fc67)

In the next window, click Finish.

Task 3. Create new Groups and add accounts in Organizational Unit.

Step 1. Right-click NetworkAdmin Organizational Unit and navigate to New --> Group.

![image](https://github.com/user-attachments/assets/ebfb5464-1fea-42f0-ab40-b16854f9d7d3)

Step 2. The New Object - Group window appears, type TechSupport in the Group name, leave all the other options set to default and click OK.

![image](https://github.com/user-attachments/assets/93d3ced8-7f73-4a86-8b24-4f87342bc365)

Step 3. Now, add the IT Head account to the TechSupport group. For this, right-click on IT Head and select Add to a group…. 

![image](https://github.com/user-attachments/assets/4fc03b75-8c00-49b9-a2fe-b6b943f93a83)

Step 4. The Select Groups window appears, in the Enter the object names to select field, type Tech and click Check Names button. Then, the TechSupport name appears, click OK. 

![image](https://github.com/user-attachments/assets/51e50057-c678-471e-b397-9c3eb0e7ce7a)

Step 5. A pop-up appears, indicating the successful addition of a user to the group. Click OK. 

![image](https://github.com/user-attachments/assets/26de82c4-1945-44bc-a7b8-0f678658844e)

Task 4. Add computers into Organizational Unit and create a detailed report(.TXT file) of all computer objects in the domain using powershell.

Step 1. Now, right-click FinanceOU Organizational Unit and navigate to New --> Computer. 

![image](https://github.com/user-attachments/assets/f3707fc2-aa4e-48d3-910a-a6dedc5139d4)

Step 2. The New Object - Computer window appears, type Computer01 in the Computer Name field and click OK.

![image](https://github.com/user-attachments/assets/e2ea9ff4-7f5d-4b46-9db7-e1fba86645fd)

Step 3. Switch to the Administrator: Windows PowerShell window, type get-adcomputer -filter * | out-file C:\useraccounts.txt and press Enter to create a detailed report of all computer objects in the domain. 

![image](https://github.com/user-attachments/assets/9ebc2577-e189-494c-bb48-1e729a2aba34)

Step 4. Now, navigate to C: drive to see if the useraccounts.txt file exists. 

![image](https://github.com/user-attachments/assets/312db45e-2535-478f-b161-b6c5b435d877)

Step 5. Double-click useraccounts.txt file to see its content. You can view the newly created user account (Computer01), as shown in the screenshot. 

![image](https://github.com/user-attachments/assets/f9a46c75-93ca-4ce6-838d-9db932b9d709)

Step 6. Close all the windows, except Windows PowerShell. 

![image](https://github.com/user-attachments/assets/a0a766df-f5ef-4fb3-82ed-eb2f76496476)

Task 5. Modify the existing Group Policy Management (GPO) to set password requirements.

Step 1. To launch Group Policy Management, click Windows Start icon and navigate to Windows Administrative Tools --> Group Policy Management. 

![image](https://github.com/user-attachments/assets/9ebe807f-a84b-460c-b550-d3a2f51a2e8b)

  Step 1a. Alternatively, you can launch Group Policy Management by typing gpmc.msc in Run. To open Run, right-click on Start and click Run. 
  
  ![image](https://github.com/user-attachments/assets/b3ab96d9-11fe-4b53-b336-b913ad16a015)

Step 2. The Group Policy Management main window appears. Expand the Forest: CCT.com>Domains>CCT.com and select Default Domain Policy, as shown in the screenshot.

![image](https://github.com/user-attachments/assets/0c8bb5cf-2e90-43fd-b305-ad258161ac31)

The Default Domain Policy is a single password policy that works for all members of a specific domain, it offers no flexibility to have different password polices for different types of users. It is recommended to only use it for password management.

Step 3. Right-click Default Domain Policy node and select Edit….

![image](https://github.com/user-attachments/assets/12255568-4dba-47dd-975d-31ca7d999f5e)

Step 4. In the Group Policy Management Editor window, expand Computer Configuration --> Policies --> Windows Settings -> Security Settings --> Account Policies. Click on Password Policy; the password policies will be listed in the right pane. 

![image](https://github.com/user-attachments/assets/e7bbe014-e195-44d0-81cf-077a339e37ee)

Step 5. You can view the default password policies that are listed in the right-pane, as shown in the screenshot. 

![image](https://github.com/user-attachments/assets/c23419cd-c2a1-4fff-9231-81344a9c990d)

Step 6. We must configure the policies to match the requirements given below. To edit the policy, double-click each of them.
      Policy	                                  Setting
    Minimum Password Length	                    14 characters
    Maximum Password Age	                      90 days
    Minimum Password Age	                      1 day
    Enforce Password History	                  20 days
Store Passwords using Reversible Encryption	    Disabled

To implement the changes in the Policy, make the desired modifications, then click Apply and click OK.

![image](https://github.com/user-attachments/assets/d38f77fc-3ab7-41ee-8393-bf9feda8442c)

Task 6. Generate a report of password policy settings using Powershell to update the configuration documentation.

Step 1. Switch to Administrator: Windows PowerShell, click to type gpresult /H C:\passwords-policy-settings.html and press Enter to generate the report of password policy settings to update the configuration documentation. 

![image](https://github.com/user-attachments/assets/9ebf9591-dd65-4b71-9acf-2a0d0bc6a93f)

Step 2. Navigate to C: drive to see if the passwords-policy-settings.html file exists.

![image](https://github.com/user-attachments/assets/f25636e3-1c64-433a-8dc9-278ed5d74e5a)

Step 3. Now, double click the passwords-policy-settings.html file.

A browser window appears displaying the Group Policy Results file, as shown in the screenshot.

![image](https://github.com/user-attachments/assets/d19f2dc0-6f86-48e7-9999-79303cf7986b)

This file displays a detailed report on the implemented account policies. You can explore it further.

This concludes the demonstration of implementing access control policies in Windows machine.
