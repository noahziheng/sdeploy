# sdeploy-cli

A light development tool using SCP,SFTP and RSync

## Installation

```shell
# install the cli globally with yarn (Preferred Way)
yarn global add sdeploy-cli

# install the cli globally with npm (Leagcy Way)
npm install -g sdeploy-cli

# install the cli locally with yarn (Preferred Way, for single project, only can use with npm script)
yarn add sdeploy-cli

# install the cli locally with npm (Leagcy Way, for single project, only can use with npm script)
npm install sdeploy-cli
```

## Usage

```shell
# Standard CLI
sdeploy .

# Deploy current directory with local config
sdeploy . -c ./config.json

# Deploy "./dist" to local config "Aliyun" "/data/www" directory , run 'echo "Hello World!"' before upload
sdeploy ./dist Aliyun -r /data/www -c ./config.json -p "echo \"Hello World!\""
```

## Example

### Upload HTML Website to Static Server

Local Directory: ~/static
Server Address: 123.45.67.8
Server Username: noah
Server Directory: ~/static/html

```shell
$ yarn global add sdeploy-cli

$ sdeploy ~/static -n
# Use Add Config Option
Current config location: /Users/noah/Library/Preferences/sdeploy-nodejs/config.json
? What's config you want to select? Add Config
? What's config name? RemoteConfig
? What's driver you want to select? RSyncDriver
? What's remote server address? 123.45.67.8
? What's remote server user? noah
? What's remote server rootpath? ~/
? What's upload driver argument? -r -l --progress --delete --force
[Success] Added Remote Config
'
$ sdeploy ~/static RemoteConfig -r static/html
```

### Upload Vue Bundle to Static Server

Local Directory: ./dist
Server Address: 123.45.67.8
Server Username: noah
Server Directory: ~/static/html

```shell
$ yarn global add sdeploy

$ sdeploy ./dist -n
# Use Add Config Option
Current config location: /Users/noah/Library/Preferences/sdeploy-nodejs/config.json
? What's config you want to select? Add Config
? What's config name? RemoteConfig
? What's driver you want to select? RSyncDriver
? What's remote server address? 123.45.67.8
? What's remote server user? noah
? What's remote server rootpath? ~/
? What's upload driver argument? -r -l --progress --delete --force
[Success] Added Remote Config
'

$ sdeploy ./dist RemoteConfig -r static/html
```

You can use local installation instead of globally:

```shell
yarn add sdeploy-cli
./node_modules/.bin/sdeploy ./dist -c ./config.json -n # Add config on project dir
```

And edit package.json "script" to:

```JSON
...
  {
    "scripts": {
      "deploy": "sdeploy ./dist -c ./config.json -p \"node build/build.js\"",
      "deploy:nobuild": "sdeploy ./dist -c ./config.json"
    }
  }
...
```

## License

GPLv3
