## Script 1
    #!/bin/bash
    
    if [ "$EUID" -ne 0 ]; then
      echo "❌ Please run as root"
      exit 1
    fi
    read -p "Enter the username: " username
    read -p "Enter the home directory path (e.g., /home/$username): " home_dir
    read -s -p "Enter the password: " password
    echo
    useradd -m -d "$home_dir" "$username"
    if [ $? -ne 0 ]; then
      echo "❌ Failed to add user"
      exit 1
    fi
    echo "$username:$password" | chpasswd
    if [ $? -eq 0 ]; then
      echo "✅ User '$username' added successfully with home directory '$home_dir'."
    else
      echo "❌ Failed to set password."
    fi

<img width="772" height="272" alt="image" src="https://github.com/user-attachments/assets/517a2008-0e80-46c0-9201-256e1bb55464" />

## Script 2

        #!/bin/bash
        read -s -p "Enter your password: " password
        echo
        if [[ ${#password} -lt 8 ]]; then
            echo "❌ Password too short. Minimum 8 characters required."
            exit 1
        fi
        if ! [[ $password =~ [A-Z] ]]; then
            echo "❌ Password must contain at least one uppercase letter."
            exit 1
        fi
        if ! [[ $password =~ [a-z] ]]; then
            echo "❌ Password must contain at least one lowercase letter."
            exit 1
        fi
        if ! [[ $password =~ [0-9] ]]; then
            echo "❌ Password must contain at least one digit."
            exit 1
        fi
        if ! [[ $password =~ [\!\@\#\$\%\^\&\*\(\)\_\+\-] ]]; then
            echo "❌ Password must contain at least one special character (!@#$%^&* etc.)."
            exit 1
        fi
        
        echo "✅ Password is strong."

<img width="711" height="455" alt="image" src="https://github.com/user-attachments/assets/38211e50-2187-4ac5-9131-7b39f32ed674" />

## Script 3

        #!/bin/bash
        
        echo "List of users and their login times:"
        echo "--------------------------------------"
        last | awk '{print $1, $4, $5, $6}' | sort | uniq

<img width="523" height="484" alt="image" src="https://github.com/user-attachments/assets/002067d7-e44d-4488-9712-d6938c23ff80" />


  
