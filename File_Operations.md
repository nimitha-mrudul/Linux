## Script 1
    #!/bin/bash
    
    if [ -z "$1" ]; then
      echo "Usage: $0 <directory_path>"
      exit 1
    fi
    
    dir="$1"
    
    if [ ! -d "$dir" ]; then
      echo "Error: '$dir' is not a valid directory."
      exit 1
    fi
    
     echo "Files in '$dir':"
    find "$dir" -maxdepth 1 -type f
<img width="595" height="620" alt="image" src="https://github.com/user-attachments/assets/701344fc-d596-42fa-8bcb-5a928aee2e1a" />

## Script 2

    #!/bin/bash
    
    if [ -z "$1" ]; then
      echo "Usage: $0 <directory_path>"
      exit 1
    fi
    
    dir="$1"
    
    if [ ! -d "$dir" ]; then
      echo "Directory does not exist."
      exit 1
    fi
    
    for file in "$dir"/*.txt; do
      [ -e "$file" ] || continue
      filename=$(basename "$file")
      mv "$file" "$dir/backup_$filename"
    done
    
    echo "Renaming completed."
<img width="650" height="405" alt="image" src="https://github.com/user-attachments/assets/afd18780-6f48-4f4a-a615-22844ef4f966" />

## Script 3
    #!/bin/bash
    if [ "$#" -ne 2 ]; then
      echo "Usage: $0 file1 file2"
      exit 1
    fi
    
    file1="$1"
    file2="$2"
    if [ ! -f "$file1" ] || [ ! -f "$file2" ]; then
      echo "One or both files do not exist."
      exit 1
    fi
    
    if cmp -s "$file1" "$file2"; then
      echo "✅ The files are identical."
    else
      echo "❌ The files are different. Showing differences:"
      diff "$file1" "$file2"
    fi
<img width="720" height="747" alt="image" src="https://github.com/user-attachments/assets/bc411631-d561-410d-abb4-1832eb2b6b9f" />




