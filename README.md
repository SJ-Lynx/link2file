  # Telegram Torrent Leecher
  
  A Telegram Torrent (and youtube-dl) Leecher based on [Pyrogram](https://github.com/pyrogram/pyrogram)
  ---
<p><a href="https://hub.docker.com/r/reaitten/tgtlg"> <img src="https://img.shields.io/docker/pulls/reaitten/tgtlg?style=for-the-badge" width="150""/></a> <a href="https://hub.docker.com/layers/reaitten/tgtlg/latest/images/sha256-2f8b28fa0b7998fcc917589e211c40d4621ac0eb4181cb96a4d18bfcb74e368c?context=explore"> <img src="https://img.shields.io/docker/image-size/reaitten/tgtlg/latest?style=for-the-badge" width="150""/></a> <a href="https://github.com/reaitten/tgtlg"> <img src="https://img.shields.io/github/repo-size/reaitten/tgtlg?style=for-the-badge" width="150"/></a> <a href="https://github.com/reaitten/tgtlg/blob/main/LICENSE"> <img src="https://img.shields.io/github/license/reaitten/tgtlg?style=for-the-badge" width="150"/></a></p> 
  
  ![GitHub Repo stars](https://img.shields.io/github/stars/reaitten/tgtlg?style=social) ![GitHub forks](https://img.shields.io/github/forks/reaitten/tgtlg?style=social)
  ---
  # Table of Contents
  
- [Benefits](#benefits)
- [To-Do](#to-do)
  * [Deployment](#deployment)
    + [Simple Way](#simple-way)
      - [Instructions](#instructions)
    + [Deploy on VPS](#deploy-on-vps)
      - [Setup `config.env`](#setup-configenv)
        * [Setup rclone](#setup-rclone)
      - [Deploying](#deploying)
    + [The Legacy Way](#the-legacy-way)
  * [Variable Explanations](#variable-explanations)
    + [Mandatory Variables](#mandatory-variables)
    + [Optional Configuration Variables](#optional-configuration-variables)
    + [Available Commands](#available-commands)
  * [How to Use?](#how-to-use)
  * [Credits](#credits-and-thanks-to)

  # Benefits
      ✓ Google Drive link cloning using gclone. (WIP)
      ✓ Telegram File mirrorring to cloud along with its unzipping, unrar and untar
      ✓ Drive/Teamdrive support/All other cloud services rclone.org supports
      ✓ Extract compatible archive
      ✓ Custom file name
      ✓ Custom commands
      ✓ Get total size of your working cloud directory
      ✓ You can also upload files downloaded from /ytdl command to gdrive using `/ytdl gdrive` command.
      ✓ You can also deploy this on your VPS
      ✓ Option to select either video will be uploaded as document or streamable
      ✓ Added /rename command to clear the downloads which are not deleted automatically.
      ✓ Added support for youtube playlist
      ✓ Renaming of Telegram files support added.
      ✓ Changing rclone destination config on fly (By using `/rclone` in private mode)
      
  # To-Do
  -   [ ] Adding mp3 files support while playlist downloading.
  -   [ ] Password support while Unarchiving the files.
  -   [ ] Selection of required files during leeching the big files using aria(/leech command)

  ## Deployment

  ### Simple Way

  #### Instructions 

  **Modified for use on Heroku, please do not heavily abuse!**

  **Join [this](https://t.me/tgleechsupport) Telegram Group if you want support, I will try to help you as much as I can.**

  <p><a href="https://heroku.com/deploy?template=https://github.com/reaitten/tgtlg"> <img src="https://img.shields.io/badge/Deploy%20To%20Heroku-blueviolet?style=for-the-badge&logo=heroku" width="200""/></a></p>

  ## Deploy on VPS

  - Clone this repo:
  ```
  git clone -b main https://github.com/reaitten/tgtlg tgtlg
  cd tgtlg
  ```

  - Install requirements
  For Debian based distros
  ```
  sudo snap install docker
  ```
  Install Docker by following the [official docker docs](https://docs.docker.com/engine/install/debian/)

  ### Setup `config.env`
  ```
  cp sample_config.env config.env
  ```
  After this step you will see a new file named ```config.env``` in root directory.

  Fill those compulsory variables.

  If you need more explanation about any variable then read [app.json](https://github.com/reaitten/tgtlg/blob/deploy-main/app.json)

  ### Setup rclone

  1. Set rclone locally by following the official repo: https://rclone.org/docs/
  2. Get your `rclone.conf` file will look something like this:
  
  ```
  [NAME]
  type = 
  scope =
  token =
  client_id = 
  client_secret = 
  ```
  
  3. Copy `rclone.conf` file in the root directory (Where `Dockerfile` exists).

  4. Your config can contains multiple drive entries. (Default: First one and change using `/rclone` command)

  ### Deploying

  - Start Docker Daemon (skip if already running):
  ```
  sudo dockerd
  ```
  - Build Docker Image:
  ```
  sudo docker build . -t torrentleech-gdrive
  ```
  - Run the image:
  ```
  sudo docker run torrentleech-gdrive
  ```
  Follow this [Video Tutorial](https://youtu.be/J3tMbngA9DE)
  ### The Legacy Way
  Simply clone the repository and run the main file:

  ```
  git clone -b 4forks https://github.com/reaitten/tgtlg
  cd TorrentLeech-Gdrive
  python3 -m venv venv
  . ./venv/bin/activate
  pip install -r requirements.txt
  # Create config.py appropriately
  python3 -m tgtlg
  ```
  ## Variable Explanations

  ### Mandatory Variables

  - `TG_BOT_TOKEN`: Create a bot using [@BotFather](https://telegram.dog/BotFather), and get the Telegram API token.

  - `APP_ID`
  
  - `API_HASH`: Get these two values from [my.telegram.org/apps](https://my.telegram.org/apps).
    * N.B.: if Telegram is blocked by your ISP, try our [Telegram bot](https://telegram.dog/UseTGXBot) to get the IDs.

  - `AUTH_CHANNEL`: Create a Super Group in Telegram, add `@GoogleIMGBot` to the group, and send /id in the chat, to get this value.

  - `OWNER_ID`: ID of the bot owner, He/she can be abled to access bot in bot only mode too(private mode).

  ### Optional Configuration Variables

<details>
      <summary><b>Click Here for more Details</b></summary>


  - `DOWNLOAD_LOCATION`: 
  The location you would like the bot to download to locally.

  - `BOT_CMD_POSTFIX`:   
  If you want the bot to respond to you when you send a command along with the bot username. 
  Usage Example: /command@botusername
  Example Value: @mybotsusername
  Defualt Value is "".
  
  - `LEECH_COMMAND`:
  Change the /leech command.
  Defualt Value is "leech"
  - `LEECH_UNZIP_COMMAND`:
   Change the /extract command.
  Defualt Value is "extract"
  - `LEECH_ZIP_COMMAND`:
  Change the /archive command.
  Defualt Value is "archive" 
  - `YTDL_COMMAND`:
  Change the /ytdl command.
  Defualt Value is "ytdl"
  - `GYTDL_COMMAND`:
  Change the /gytdl command.
  Defualt Value is "gytdl"
  - `PYTDL_COMMAND`:
  Change the /pytdl command.
  Defualt Value is "pytdl"
  - `GLEECH_COMMAND`:
  Change the /gleech command.
  Defualt Value is "gleech"
  - `TELEGRAM_LEECH_COMMAND`:
  Change the /tleech command.
  Defualt Value is "tleech"
  - `TELEGRAM_LEECH_UNZIP_COMMAND`:
  Change the /textract command.
  Defualt Value is "textract"
  - `CLONE_COMMAND_G`:
  Change the /gclone command.
  Defualt Value is "gclone"
  - `UPLOAD_COMMAND`:
  Change the /upload command.
  Defualt Value is "upload"
  - `RENEWME_COMMAND`:
  Change the /leech command.
  Defualt Value is "leech"
  - `SAVE_THUMBNAIL`:
  Change the /savethumb command.
  Defualt Value is "savethumb"
  - `CLEAR_THUMBNAIL`:
  Change the /clearthumb command.
  Defualt Value is "clearthumb"
  - `GET_SIZE_G`:
  Change the /clearthumb command.
  Defualt Value is "clearthumb"
  - `TOGGLE_VID`:
  Change the /togglevid command.
  Defualt Value is "togglevid"
  - `TOGGLE_DOC`:
  Change the /toggledoc command.
  Defualt Value is "toggledoc"
  - `RENAME_COMMAND`:
  Change the /rename command.
  Defualt Value is "rename"
  - `CANCEL_COMMAND_G`:
  Change the /cancel command.
  Defualt Value is "cancel"

  - `MAX_FILE_SIZE`:
  - `TG_MAX_FILE_SIZE`:
  - `FREE_USER_MAX_FILE_SIZE`
  - `MAX_TG_SPLIT_FILE_SIZE`:
  - `CHUNK_SIZE`:
  - `MAX_MESSAGE_LENGTH`:
  - `PROCESS_MAX_TIMEOUT`:
  - `ARIA_TWO_STARTED_PORT`:
  - `EDIT_SLEEP_TIME_OUT`:
  - `MAX_TIME_TO_WAIT_FOR_TORRENTS_TO_START`:
  - `FINISHED_PROGRESS_STR`:
  - `UN_FINISHED_PROGRESS_STR`:
  - `TG_OFFENSIVE_API`:
  - `CUSTOM_FILE_NAME`:

  - `UPLOAD_AS_DOC`: Takes two option True or False. If True file will be uploaded as document. This is for people who wants video files as document instead of streamable.

  - `INDEX_LINK`: (Without `/` at last of the link, otherwise u will get error) During creating index, plz fill `Default Root ID` with the id of your `DESTINATION_FOLDER` after creating. Otherwise index will not work properly.

  - `DESTINATION_FOLDER`: Name of your folder in your respective drive where you want to upload the files using the bot.

</details>

  ### Available Commands

  - `/rclone`: Это изменит конфигурацию вашего диска на лету. (Первый будет по умолчанию)
  - `/gclone`: Эта команда используется для клонирования файлов или папок gdrive с помощью gclone.

  - `/help`: Чтобы получить список команд

  - `/leech`: Эта команда должна использоваться в качестве ответа на магнитную ссылку, торрент-ссылку или прямую ссылку. [эта команда отправит чат в спам и отправит загруженные отдельные файлы, если в указанном торрент-файле более одного файла]
  - `/archive`: Эта команда должна использоваться в качестве ответа на магнитную ссылку, торрент-ссылку или прямую ссылку. [Эта команда создаст .tar.gz файл выходного каталога и отправьте файлы в чат, разделенные на ЧАСТИ по 1024 Мбайт каждая, из-за ограничений Telegram]
  - `/extract`: Это приведет к разархивированию файла и загрузке в telegram.

  - `/gleech`: Эта команда должна использоваться в качестве ответа на магнитную ссылку, торрент-ссылку или прямую ссылку. И это позволит загрузить файлы по данной ссылке или через торрент и загрузить в облако с помощью rclone.
  - `/garchive`: Эта команда сожмет папку / файл и загрузит его в ваше облако.
  - `/gextract`: Это приведет к разархивированию файла и его загрузке в облако.
  - `/gclone`: Эта команда используется для клонирования файлов или папок gdrive с помощью gclone.

Syntax: `[Идентификатор файла или папки][один пробел] [только имя вашей папки (если идентификатор файла, ничего не ставьте)]` а затем ответьте на него /gclone.

  - `/tleech`: Это приведет к зеркальному отображению файлов telegram в вашем соответствующем облаке.
  - `/textract`: Это приведет к разархивированию файла telegram и загрузке его в облако.

  - `/ytdl`: Эту команду следует использовать в качестве ответа на поддерживаемую ссылку 
  - `/pytdl`: Эта команда загрузит видео со ссылки на плейлист YouTube и загрузит в telegram.
  - `/gytdl`: Это будет загружено и загружено в ваше облако.
  - `/gpytdl`: Это позволяет загрузить плейлист YouTube и загрузить его в свое облако.
  - `/getsize`: Это даст вам общий размер вашей целевой папки в облаке.
  - `/renewme`: Это очистит остатки загрузок, которые не удаляются после загрузки файла или после команды /cancel.
  - `/rename`: Чтобы переименовать файлы telegram.

  - `/rclone`: Это изменит конфигурацию вашего диска на лету. (Первый будет по умолчанию)
  - `/log`: Это отправит вам текстовый файл журналов.

Пока работает только с прямой ссылкой и ссылкой на YouTube.
Вы можете добавить собственное имя в качестве префикса к файлу. Пример: если gk.txt загружено будет то, что вы добавите в CUSTOM_FILE_NAME + gk.txt

  Вы можете добавить пользовательское имя в качестве префикса исходного имени файла.
  e.g: if file is `gk.txt` uploaded will be what you added in ``CUSTOM_FILE_NAME`` + ``gk.txt``
  It is like you can add custom name as prefix of the original file name.
  Like if your file name is `gk.txt` uploaded will be what u add in `CUSTOM_FILE_NAME` + `gk.txt`
