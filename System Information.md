## script 1
    #!/bin/bash
    
    echo "------------------------------"
    echo "   System Information Script  "
    echo "------------------------------"
    
    
    echo "Operating System: $(uname -o)"
    echo "OS Release Version: $(cat /etc/os-release | grep PRETTY_NAME | cut -d= -f2 | tr -d '\"')"
    
    
    echo "Kernel Version: $(uname -r)"
    
    
    echo "CPU Info:"
    lscpu | grep -E '^Model name|^Architecture|^CPU\(s\)'
    
    
    echo "Available Memory:"
    free -h | grep Mem | awk '{print "Total: " $2 ", Used: " $3 ", Free: " $4}'
    
    echo "------------------------------"
   
<img width="883" height="531" alt="image" src="https://github.com/user-attachments/assets/baa18802-723b-416a-9a25-dd7d698ca3d7" />

## Script 2
    #!/bin/bash
    PROCESS_NAME="firefox"
    if pgrep -x "$PROCESS_NAME" > /dev/null
    then
        echo "✅ Process '$PROCESS_NAME' is already running."
    else
        echo "⚠️ Process '$PROCESS_NAME' is not running. Starting it..."
        $START_COMMAND &
    
        # Confirm it started
        if pgrep -x "$PROCESS_NAME" > /dev/null
        then
            echo "✅ Process '$PROCESS_NAME' started successfully."
        else
            echo "❌ Failed to start '$PROCESS_NAME'."
        fi
    fi
<img width="641" height="241" alt="image" src="https://github.com/user-attachments/assets/cb6c80fb-28d9-4915-ae3a-f79d15e7fb9f" />

## Script 3

    #!/bin/bash
    
    THRESHOLD=80              
    PARTITION="/dev/sda1"     
    EMAIL="your_email@example.com"  
    
   
    USAGE=$(df -h | grep "$PARTITION" | awk '{print $5}' | sed 's/%//g')
    
    
    if [ "$USAGE" -ge "$THRESHOLD" ]; then
        # Email content
        SUBJECT="Disk Space Alert on $(hostname)"
        MESSAGE="Warning: The partition $PARTITION on $(hostname) is ${USAGE}% full. Threshold is ${THRESHOLD}%."
        
       
        echo "$MESSAGE" | mail -s "$SUBJECT" "$EMAIL"
    fi


