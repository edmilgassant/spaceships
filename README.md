## Simple python script for updating system
## What is in the python script?
- This python script updates and upgrades system with sudo priviledges.
- I also added a recommendation at end of script
### Tools used:
- import os = this module allows script to function with the operating system
- import sys = this module gives the script sudo privileges (root/sudo)
- import time = this module allows a function called sleep or time.sleep to give a specific time before the next execution

### Python script
- Here is my python script. It can be ran using ./python_script.py or python3 python_script.py
- In this example, I will just add #!/usr/bin/env python3 and will allow me to just used ./ to run script

```python3
#!/usr/bin/env python3

import os
import sys # this module gives this script sudo privilege to run.
import time

def update_system():
    # Ensure the script is executed with administrative privileges (root/sudo)
    if os.geteuid() != 0:
        print ()
        time.sleep(1)
        print ("This script requires administrative privileges.")
        time.sleep(2)
        print ("Administrative privilege recognized. Please verify with password:")
        time.sleep(1)
        os.execvp("sudo", ["sudo", sys.executable] + sys.argv)
        return

    # Run the apt update command to refresh package lists
    print ()
    print ("######## Running system update... ########")
    print ()
    time.sleep(2)
    os.system("apt update")

    # Run the apt upgrade command to upgrade installed packages
    print ()
    print ("######## Running system upgrade... ########")
    print ()
    time.sleep(2)
    os.system("apt upgrade") # you can add "apt upgrade -y" to bypass if you want.
    print ()
    time.sleep(2)
    print ("System update completed successfully.")
    print ()
    time.sleep(2)
    print ("Recommend:")
    print ()
    time.sleep(1)
    print ("Updating and upgrading system often and apply needed patches")
    print ()
    time.sleep(1)

if __name__ == "__main__":
    update_system()
```
