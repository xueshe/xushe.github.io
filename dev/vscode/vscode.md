## launch.json

`````
{
	"version": "0.2.0",
	"configurations": [
		{
			"name": "Launch Chrome",
			"request": "launch",
			"type": "chrome",
			"runtimeExecutable": "/Applications/Microsoft Edge Dev.app/Contents/MacOS/Microsoft Edge Dev",
			"runtimeArgs": [
				"--args",
				"--disable-web-security"
				"--user-data-dir=/Users/zheric2/Library/Application Support/Microsoft Edge Dev/Default/",
			],
			"url": "http://localhost:3000/",
			"webRoot": "${workspaceFolder}",
			"preLaunchTask": "npm: dev"
		}
	],
	"compounds": [
		{
			"name": "nr dev",
			"configurations": [
				"Launch Chrome"
			],
		}
	]
}
`````

## task.json

`````
{
	"version": "2.0.0",
	"tasks": [
		{
			"type": "shell",
			"command": "nr dev",
			"problemMatcher": [],
			"label": "npm: dev",
			"detail": "vite --mode development",
			"isBackground": true
		}
	]
}
`````

