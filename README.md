# docker-menue

An interactive Bash script for managing multiple Docker Compose projects from a centralized menu interface.

## Features

- 📋 Interactive menu to select and manage Docker Compose projects
- 🚀 Quick start/stop containers with simple up/down commands
- 📁 Automatic discovery of docker-compose.yml files in subdirectories
- 🔍 Display running containers using `dops` or `docker ps -a`
- ⚙️ Customizable search location and compose file names
- 🎯 Support for multiple compose projects in separate folders

## Prerequisites

- **Docker** and **Docker Compose** installed
- **tree** command (`sudo apt install tree` on Debian/Ubuntu)
- **dops** (optional, for enhanced container display)
- - https://github.com/Mikescher/better-docker-ps

## Installation

1. Clone this repository:
```bash
git clone https://github.com/yourusername/docker-menue.git
cd docker-menue
```

2. Make the script executable:
```bash
chmod +x docker-menue
```

3. (Optional) Move to a directory in your PATH:
```bash
sudo mv docker-menue /usr/local/bin/
```
4. Make docker & dops run as docker group
https://docs.docker.com/engine/install/linux-postinstall/

To create the docker group and add your user:

Create the docker group.
```bash
 sudo groupadd docker
```
Add your user to the docker group.
```bash
 sudo usermod -aG docker $USER
```
Log out and log back in so that your group membership is re-evaluated.

## Usage

### Basic Usage

Run the script:
```bash
./docker-menue
```

The script will:
1. Display currently running containers
2. Ask if you want to start (up) or stop (down) a compose project
3. Show a numbered list of available projects
4. Execute the chosen action

### Command Line Options
```bash
docker-menue [-l directory] [-n filename] [-1|-2] [-h]
```

**Options:**
- `-h` : Display help message
- `-l <directory>` : Specify custom location to search for compose files (default: `~/Desktop/containers`)
- `-n <filename>` : Specify custom compose filename (default: `docker-compose.yml`)
- `-1` : Use `dops` for displaying containers (default)
- `-2` : Use `docker ps -a` for displaying containers

### Examples
```bash
# Use custom location
./docker-menue -l /opt/containers

# Search for compose.yaml instead of docker-compose.yml
./docker-menue -n compose.yaml

# Use docker ps -a for container display
./docker-menue -2

# Combine options
./docker-menue -l /home/user/projects -n compose.yaml -2
```

## Project Structure

The script expects your Docker Compose projects organized like this:
```
folder_all_projects/
├── project1/
│   └── docker-compose.yml
├── project2/
│   └── docker-compose.yml
└── project3/
    └── docker-compose.yml
```

## Configuration

Edit the default values at the top of the script:
```bash
compose_name="docker-compose.yml"          # Default compose filename
compose_location="$HOME/docker-projects"   # Default search location
docker_display=dops                        # Default display command
```

## Troubleshooting

**"tree is not installed"**
```bash
sudo apt install tree  # Debian/Ubuntu
sudo yum install tree  # RHEL/CentOS
brew install tree      # macOS
```

**"dops is not installed"**
The script will automatically fall back to `docker ps -a` if dops is not available.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

MIT License - feel free to use and modify as needed as long as you mention Domke as initial creator.

## Author

Domke
