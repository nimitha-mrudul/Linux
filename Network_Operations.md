## Sript 1
    #!/bin/bash
    servers=(
        "192.168.56.104"
    )
    
    for server in "${servers[@]}"; do
        echo "Checking SSH connectivity to $server..."
        timeout 5 bash -c "cat < /dev/null > /dev/tcp/$server/22" 2>/dev/null
    
        if [ $? -eq 0 ]; then
            echo "✅ $server is reachable over SSH."
        else
            echo "❌ $server is NOT reachable over SSH."
        fi
    done

  <img width="544" height="217" alt="image" src="https://github.com/user-attachments/assets/c1615fd8-129d-4f71-890b-ed7fd42954fd" />

  ## Sript 2
      #!/bin/bash
    
        ip_list=("8.8.8.8" "1.1.1.1" "192.168.56.104")
        for ip in "${ip_list[@]}"
        do
        echo "Pinging $ip..."
        avg_time=$(ping -c 4 "$ip" | grep 'rtt' | awk -F'/' '{print $5}')
        
        if [ -z "$avg_time" ]; then
            echo "$ip is unreachable or not responding."
        else
            echo "Average response time for $ip: $avg_time ms"
        fi
    
        echo "-----------------------------------"
    done

<img width="573" height="363" alt="image" src="https://github.com/user-attachments/assets/29894b77-b4a0-4e6a-ae08-d72d285cb3a5" />

## Script 3

    #!/bin/bash
    
    if [ -z "$1" ]; then
      echo "Usage: $0 <website_url>"
      exit 1
    fi
    
    website=$1
    
    status_code=$(curl -s -o /dev/null -w "%{http_code}" "$website")
    
    if [[ "$status_code" -ge 200 && "$status_code" -lt 400 ]]; then
      echo "✅ $website is UP (Status code: $status_code)"
    else
      echo "❌ $website might be DOWN or unreachable (Status code: $status_code)"
    fi
<img width="688" height="244" alt="image" src="https://github.com/user-attachments/assets/75043be6-8686-47dd-b3d5-579965b1be93" />



