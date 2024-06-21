# Making a AD group and adding a security policy

1. On domain controller open Active Directory Users and Computers a. right click on domain b. go to NEW > GROUP&#x20;

<figure><img src="../../.gitbook/assets/image (90).png" alt=""><figcaption></figcaption></figure>

2. Name your group i am making one that member computers will never auto update a. under group scope - Domain local = only users or computers on this domain - Global = two or more domains - Universal = two or more seprate bisnesses b. group type - security policies = for security - Distribution = for everything else Making a OU with a security policy

<figure><img src="../../.gitbook/assets/image (94).png" alt=""><figcaption></figcaption></figure>

## Making a OU with a security policy

1. On domain controller open Active Directory Users and Computers a. right click on domain b. go to NEW > OU

<figure><img src="../../.gitbook/assets/image (92).png" alt=""><figcaption></figcaption></figure>

2. Name the group

<figure><img src="../../.gitbook/assets/image (93).png" alt=""><figcaption></figcaption></figure>

3. Open Group policy Management a. Forest > Domains > cyberpunk.local b. find your OU that you made c. right click select the first option

<figure><img src="../../.gitbook/assets/image (95).png" alt=""><figcaption></figcaption></figure>

4. Give the new gpo a name

<figure><img src="../../.gitbook/assets/image (96).png" alt=""><figcaption></figcaption></figure>

5. Once made right click on newly made gpo and select

<figure><img src="../../.gitbook/assets/image (97).png" alt=""><figcaption></figcaption></figure>

6.  To find the never auto update gpo setting:

    A. under computer config&#x20;

    B. policies&#x20;

    C Administrative templates d. windows components

    D. windows components

<figure><img src="../../.gitbook/assets/image (98).png" alt=""><figcaption></figcaption></figure>

7.  Select Windows update:

    A. find and click on Config Auto updates&#x20;

    B. hit disable

    C. hit OK button

<figure><img src="../../.gitbook/assets/image (99).png" alt=""><figcaption></figcaption></figure>

8.  On client computer or where you want the policy to apply&#x20;

    A. open a admin powershell&#x20;

    B. run

`gpupdate /force c. to check if the policy has applied to the machine run`

`gpresult /r /scope:computer`&#x20;



You should see your policy under Applied Group Policy Objects

<figure><img src="../../.gitbook/assets/image (100).png" alt=""><figcaption></figcaption></figure>

