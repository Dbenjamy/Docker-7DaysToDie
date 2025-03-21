# Usage

Example with all parameters supported

## docker-compose

```yaml
version: '2'
services:
  7dtdserver:
    build:
      context: https://github.com/Dbenjamy/Docker-7DaysToDie.git
    container_name: 7dtdserver
    environment:
      - LINUXGSM_VERSION=v24.3.4        # Change to use another version of LinuxGSM
      - START_MODE=1                    # Change between START MODES 
      - VERSION=alpha21                 # Change between 7 days to die versions 
      - PUID=1000                       # Remember to use same as your user 
      - PGID=1000                       # Remember to use same as your user
      - TimeZone=America/New_York       # Optional - Change Timezone 
      - TEST_ALERT=NO                   # Optional - Send a test alert
      - UPDATE_MODS=NO                  # Optional - This will allow mods to be updated on start, each mod also need to have XXXX_UPDATE=YES to update on start
      - MODS_URLS=""                    # Optional - Mods URLs to install, must be ZIP or RAR.
      - ALLOC_FIXES=NO                  # Optional - Install ALLOC FIXES
      - ALLOC_FIXES_UPDATE=NO           # Optional - Update Allocs Fixes before server start
      - UNDEAD_LEGACY=NO                # Optional - Install Undead Legacy mod, if DARKNESS_FALLS is enabled, it will not install anything
      - UNDEAD_LEGACY_VERSION=stable    # Optional - Undead Legacy version
      - UNDEAD_LEGACY_UPDATE=NO         # Optional - Update Undead Legacy mod before server start
      - DARKNESS_FALLS=YES              # Optional - Install Darkness Falls mod, if UNDEAD_LEGACY is enabled, it will not install anything 
      - DARKNESS_FALLS_UPDATE=NO        # Optional - Update Darkness Falls mod before server start
      - DARKNESS_FALLS_URL=False        # Optional - Install the provided Darkness Falls URL
      - CPM=NO                          # Optional - CSMM Patron's Mod (CPM)
      - CPM_UPDATE=NO                   # Optional - Update CPM before server start
      - BEPINEX=NO                      # Optional - BepInEx
      - BEPINEX_UPDATE=NO               # Optional - Update BepInEx before server start
      - BACKUP=NO                       # Optional - Backup server
      - BACKUP_HOUR=5                   # Optional - Backup hour 0-23
      - BACKUP_MAX=7                    # Optional - Max backups to keep
      - MONITOR=NO                      # Optional - Keeps server up if crash
      - CHANGE_CONFIG_DIR_OWNERSHIP=YES # Optional - Sometimes if you're running some of your volumes on a NAS, you won't have access to change their ownership. This setting will bypass trying to change ownership, otherwise the startup will fail

    volumes:
      - /mnt/Storage1_1TB/7DaysServer/7DaysToDie:/home/sdtdserver/.local/share/7DaysToDie/     # 7 Days To Die world saves
      - /mnt/Storage1_1TB/7DaysServer/LGSM-Config:/home/sdtdserver/lgsm/config-lgsm/sdtdserver # LGSM config folder
      - /mnt/Storage1_1TB/7DaysServer/ServerFiles:/home/sdtdserver/serverfiles/                # Optional - serverfiles folder
      - /mnt/Storage1_1TB/7DaysServer/log:/home/sdtdserver/log/                                # Optional - Logs folder
      - /mnt/Storage1_1TB/7DaysServer/backups:/home/sdtdserver/lgsm/backup/                    # Optional - If BACKUP=NO, backups folder
    ports:
      - 26900:26900/tcp # Default game ports
      - 26900:26900/udp # Default game ports
      - 26901:26901/udp # Default game ports
      - 26902:26902/udp # Default game ports
    ulimits:
      nofile:
        soft: "10240"
        hard: "10240"

    restart: unless-stopped # INFO - NEVER USE WITH START_MODE=4 or START_MODE=0

```
