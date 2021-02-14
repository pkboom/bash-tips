```sh
docker info > /dev/null 2>&1

if [ $? -ne 0 ]; then
    echo "Docker is not running."

    exit 1
fi

```

`2>$1` redirects stderr to a file descriptor 1.

### file descriptors

0 Standard Input

1 Standard Output

2 Standard Error

### /dev/null

This is a black hole where any data sent will be discarded

`$?`: exit status of the last command.

`-eq`: equal to

`-ne`: not equal to

`-lt`: less than

`-le`: less than or equal to

`-gt`: greater than

`-ge`: greater than or equal to

```sh
sudo chown -R $USER: .
```

```sh
CYAN='\033[0;36m'
LIGHT_CYAN='\033[1;36m' # 1: Bold, 36: Cyan
WHITE='\033[1;37m'
NC='\033[0m' # 0: reset all attributes
```

[Bash tips: Colors and formatting](https://misc.flogisoft.com/bash/tip_colors_and_formatting)

**Format**: `<Esc>[FormatCodem`

**`<Esc>` character**:

```
\e
\033
\x1B
```

**Attributes combination**

Attributes must be separated by a semicolon (“;”).

```sh
if sudo -n true 2>/dev/null; then
    sudo chown -R $USER: .
    echo -e "${WHITE}Get started with:${NC} cd example-app && ./vendor/bin/sail up"
else
    echo -e "${WHITE}Please provide your password so we can make some final adjustments to your application's permissions.${NC}"
    echo ""
    sudo chown -R $USER: .
    echo ""
fi

```

**chown [owner]:[group]] file**

chown changes the file owner and/or the file group owner:

`chown bob file`

Changes the ownership of the file from its current owner to user bob.
chown owner:group file example:

`chown bob:users file`

Changes the ownership of the file from its current owner to user bob and changes the file group owner to group users.
chown :group file example:

`chown :admins file`

Changes the group owner to the group admins. The file owner is unchanged.

`chown bob: file`

Change the file owner from the current owner to user bob and changes the group owner to the login group of user bob.

`sudo -n command`

-n, --non-interactive

Avoid prompting the user for input of any kind. If a pass‐word is required for the command to run, sudo will display an error message and exit.

`true` and `false` are "builtins", commands interpreted directly by the shell.

`true` a program that instantly exits with a successful exit code.'do nothing, successfully'

`false` a program that exits with an unsuccessful exit code. 'do nothing, unsuccessfully'

```sh
wget -c http://geolite.maxmind.com/download/geoip/database/GeoLite2-Country.tar.gz -O - | tar -xz
```

`-c` continues an incomplete download.

`-O` specifies a file to which the documents is written, and here we use `-`, meaning it will written to standard output.

`-x` enables extraction of archive files.

`-z` decompresses.
