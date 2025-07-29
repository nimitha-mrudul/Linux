# Software installation #
      #!/bin/bash
      
      if [ -f /etc/os-release ]; then
          . /etc/os-release
          distro=$ID
      else
          echo "Distro not identified" >&2
          exit 1
      fi
      
      case "$distro" in
          debian|ubuntu)
              sudo apt update
              sudo apt install -y curl
              ;;
          rhel|centos|fedora)
              sudo yum install -y curl
              ;;
          alpine)
              sudo apk add curl
              ;;
          *)
              echo "Distro not identified" >&2
              exit 1
              ;;
      esac
      
      echo "Curl installation completed for $distro."

<img width="940" height="940" alt="image" src="https://github.com/user-attachments/assets/9f27ce5a-c17e-4791-aef6-4cb189a8e50d" />


