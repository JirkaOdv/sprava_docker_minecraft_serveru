# CraftControl - Minecraft Server Management Panel

Modern web-based control panel for Minecraft servers with RCON and SSH integration.

## 🚀 Quick Start

### Using Docker Run

```bash
docker run -d \
  --name craftcontrol \
  -p 5050:5000 \
  -v ./data:/app/data \
  -e SECRET_KEY=your_random_secret_key_here \
  -e RCON_PASSWORD=your_rcon_password \
  -e RCON_HOST=your_minecraft_server_ip \
  -e RCON_PORT=25575 \
  jiriodv/craftcontrol:latest
```

### Using Docker Compose

```yaml
version: '3.8'

services:
  craftcontrol:
    image: jiriodv/craftcontrol:latest
    container_name: craftcontrol
    restart: unless-stopped
    ports:
      - "5050:5000"
    volumes:
      - ./data:/app/data
    environment:
      - SECRET_KEY=change_this_to_random_32_char_string
      - RCON_PASSWORD=your_rcon_password
      - RCON_HOST=minecraft_server  # or IP address
      - RCON_PORT=25575
      - MC_CONTAINER_NAME=minecraft_server  # optional, for Docker control
```

Then run:
```bash
docker-compose up -d
```

## 🌐 Access

Open your browser and navigate to:
```
http://localhost:5050
```

**Default login:**
- Username: `admin`
- Password: `admin`

⚠️ **Change the password immediately after first login!**

## ⚙️ Environment Variables

### Required
- `SECRET_KEY` - Flask secret key (generate random 32+ character string)
- `RCON_PASSWORD` - Your Minecraft server RCON password
- `RCON_HOST` - Minecraft server hostname or IP

### Optional
- `RCON_PORT` - RCON port (default: 25575)
- `MC_CONTAINER_NAME` - Docker container name for server control
- `SSH_HOST` - SSH server IP (for remote servers)
- `SSH_USER` - SSH username
- `SSH_PASSWORD` - SSH password
- `MC_LOG_PATH` - Path to Minecraft logs
- `MC_SERVER_PATH` - Path to Minecraft server data
- `BLUEMAP_URL` - BlueMap web interface URL

## 🎮 Features

- **Real-time Monitoring** - CPU, RAM, TPS, player count, uptime
- **RCON Console** - Execute commands directly
- **Player Management** - Track sessions, playtime, manage players
- **Plugin Support** - EssentialsX, WorldEdit, BlueMap, AuthMe
- **Smart Autocomplete** - Context-aware command suggestions
- **Wiki & Commands** - Built-in command reference
- **Docker Integration** - Start/stop/restart server containers
- **SSH Support** - Manage remote servers

## 📋 Minecraft Server Setup

Your Minecraft server must have RCON enabled. Add to `server.properties`:

```properties
enable-rcon=true
rcon.password=your_secure_password
rcon.port=25575
```

Restart your Minecraft server after making changes.

## 🔧 Example: Complete Setup with Minecraft Server

```yaml
version: '3.8'

services:
  minecraft:
    image: itzg/minecraft-server:latest
    container_name: minecraft_server
    ports:
      - "25565:25565"
      - "25575:25575"
    environment:
      EULA: "TRUE"
      ENABLE_RCON: "TRUE"
      RCON_PASSWORD: "your_password"
      MEMORY: "4G"
      TYPE: "PAPER"
    volumes:
      - ./minecraft-data:/data
    networks:
      - mc-network

  craftcontrol:
    image: jiriodv/craftcontrol:latest
    container_name: craftcontrol
    ports:
      - "5050:5000"
    volumes:
      - ./panel-data:/app/data
    environment:
      - SECRET_KEY=generate_random_string_here
      - RCON_PASSWORD=your_password
      - RCON_HOST=minecraft_server
      - RCON_PORT=25575
      - MC_CONTAINER_NAME=minecraft_server
    networks:
      - mc-network
    depends_on:
      - minecraft

networks:
  mc-network:
    driver: bridge
```

## 🔒 Security Recommendations

1. **Change default password** immediately after first login
2. **Use strong passwords** for RCON and admin account
3. **Set unique SECRET_KEY** (minimum 32 characters)
4. **Use HTTPS** in production (Nginx reverse proxy recommended)
5. **Restrict access** with firewall rules
6. **Keep updated** - pull latest image regularly

## 📚 Documentation

- **GitHub Repository**: https://github.com/jiriodv/craftcontrol
- **Full Documentation**: See README.md in repository
- **Installation Guides**: INSTALL_LINUX.md, INSTALL_SERVER.md
- **Issues & Support**: https://github.com/jiriodv/craftcontrol/issues

## 🔄 Updates

Pull the latest version:
```bash
docker pull jiriodv/craftcontrol:latest
docker-compose pull
docker-compose up -d
```

## 📝 License

MIT License - See LICENSE file in repository

## 🤝 Contributing

Contributions welcome! Please visit the GitHub repository.

---

**Made with ❤️ for the Minecraft community**
