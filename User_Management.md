## Script
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

<img width="772" height="272" alt="image" src="https://github.com/user-attachments/assets/517a2008-0e80-46c0-9201-256e1bb55464" />

  echo "❌ Failed to set password."
fi
