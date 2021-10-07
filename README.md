# OCI-Cloudinit-Backdoors

In this repository you will find example cloud-init script that will buildin a backdoor for your compute instance on OCI. 

More info:
- https://www.oc-blog.com/2021/10/06/direct-console-access-to-your-linux-instances-from-the-oci-console/
- https://www.oc-blog.com/2021/10/07/direct-console-access-to-your-windows-instances-from-the-oci-console/

The attached cloud-init examples will create a user called backdoor with password 1LoveOracle!!

## Linux
Serial Console access is by default already enabled, but all user must validate via SSH key pair. 

To enable console access we need to create a user that has a password configured, but not an SSH key pair. This will allow you to login with the backdoor user ONLY via serial connection and not direct via SSH session.

Be aware, that when a user has SSH access, they can switch to the backdoor user if they know that user's password.

## Windows
Windows cloud-init script does a lot more. First is enabled the instance to have commandline/powershell access via serial port. It creates the backdoor user and configures it to NOT have RDP access. It also hides the default usernames from the login screen.

The script will reboot once after being created to enable the serial console

## Usage
When creating a new instance in OCI, click on the Advanced Setting section in the bottom of the page and choise "past cloud init script". There you can paste the correct script depending on your operating system

## Credits

Thank you to Jordan Mills for providing the completed method to Disable RDP access via powershell: https://jordanmills.wordpress.com/2014/07/31/change-local-user-rights-assignment-from-powershell/

