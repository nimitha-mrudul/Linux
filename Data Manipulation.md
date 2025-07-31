## Script 1
    #!/bin/bash
    
    if [ "$#" -ne 2 ]; then
      echo "Usage: $0 <csv_file> <column_number>"
      echo "Example: $0 data.csv 3"
      exit 1
    fi
    
    csv_file="$1"
    column="$2"
    
    if [ ! -f "$csv_file" ]; then
      echo "File not found: $csv_file"
      exit 1
    fi
    awk -F',' -v col="$column" '
      NR > 1 { sum += $col }   # Skip header (NR > 1)
      END { print "Sum of column " col ": " sum }
    ' "$csv_file"
<img width="567" height="400" alt="image" src="https://github.com/user-attachments/assets/e28701c7-1dc7-435d-8ba2-c508454ebd18" />

## Script 2

    #!/bin/bash
    
    if [ "$#" -ne 2 ]; then
        echo "Usage: $0 <log_file> <request_threshold>"
        exit 1
    fi
    log_file=$1
    threshold=$2
    
    if [ ! -f "$log_file" ]; then
        echo "Log file '$log_file' not found!"
        exit 1
    fi
    echo "IP addresses with more than $threshold requests:"
    awk '{print $1}' "$log_file" | \
        sort | uniq -c | \
        awk -v threshold="$threshold" '$1 > threshold {print $2, "=>", $1, "requests"}'

<img width="664" height="395" alt="image" src="https://github.com/user-attachments/assets/59c52370-1f75-4aad-87d1-579d4ef17695" />

## Script 3

    #!/bin/bash
    read -p "Enter a sentence: " sentence
    echo "$sentence" | \
    tr '[:upper:]' '[:lower:]' | \
    tr -c '[:alnum:]' '[\n*]' | \
    grep -v "^$" | \
    sort | \
    uniq -c

  <img width="694" height="464" alt="image" src="https://github.com/user-attachments/assets/24355bbb-9a49-4f9b-8293-c7e744c1f71b" />

    
    
