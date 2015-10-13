1. Download Zip file - 
* Extract contents
* Setup SSH host keys
     * ssh-keygen.exe -t rsa -f ssh_host_rsa_key
     * ssh-keygen.exe -t dsa -f ssh_host_dsa_key
     * ssh-keygen.exe -t ecdsa -f ssh_host_ecdsa_key
     * ssh-keygen.exe -t ed25519 -f ssh_host_ed25519_key
* Install key-auth package if you need key-based authentication
     * run setup-ssh-lsa.cmd
     * reboot
* Run SSH daemon as System (See below for alternative options)
     * Download PSTools from [SysInternals](https://technet.microsoft.com/en-us/sysinternals/bb897553)
     * psexec.exe -i -s cmd.exe
     * Within cmd.exe - launch sshd.exe
* Running SSH daemon as Admin user
     * Note - SSH daemon needs to run as System to support key-based authentication
     * Give Admin user SE_ASSIGNPRIMARYTOKEN_NAME (steps below)
     * secpol.msc -> Local Policies -> UserRightsAssessment  
     * Add the Admin user to "Replace a process level token"
     * Log off and Log in.
     * In elevated cmd.exe, start sshd.exe