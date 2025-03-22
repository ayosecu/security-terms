<br>

# Mitigations
- [Patching](./01_Patching.md)
- [Data Execution Prevention](./02_Data_Execution_Prevention.md)
- [Address Space Layout Randomization](./03_ASLR.md)
    - To make it harder for buffer overruns to execute privileged instructions at known addresses in memory.
- [Principle of Least Privilege](./04_PoLP.md)
    - Eg running Internet Explorer with the Administrator SID disabled in the process token. Reduces the ability of buffer overrun exploits to run as elevated user.
- [Code Signing](./05_Code_Signing.md)
    - Requiring kernel mode code to be digitally signed.
- [Compiler Security Features](./06_Compiler_Security_Features.md)
    - Use of compilers that trap buffer overruns.
- [Encryption](./07_Encryption.md)
    - Of software and/or firmware components.
- [Mandatory Access Controls](./08_MAC.md)
    - MACs
    - Access Control Lists (ACLs)
    - Operating systems with Mandatory Access Controls - eg. SELinux.
- [Insecure by Exception](./09_Insecure_by_Exception.md)
    - When to allow people to do certain things for their job, and how to improve everything else. Don't try to "fix" security, just improve it by 99%.
- [Do Not Blame the User](./10_Do_Not_Blame_the_User.md)
    - Security is about protecting people, we should build technology that people can trust, not constantly blame users.  
<br>