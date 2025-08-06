# heishamon-dev-image
A devcontainer image with preinstalled arduino-cli and libraries

An example `.devcontainer/devcontainer.json` file (with platform.io support):

```json
{
  "name": "arduino-pio",
  "image": "ghcr.io/the78mole/heishamon-pio:v0.0.8",
  "postCreateCommand": "./.devcontainer/postCreate.sh",
  "features": {
    "ghcr.io/devcontainers/features/common-utils:2": {
      "installZsh": false,
      "username": "ubuntu"
    }
  },
  "remoteUser": "ubuntu",
  "updateRemoteUserUID": true,
  "privileged": true,
  "customizations": {
    "vscode": {
      "extensions": [
        "vsciot-vscode.vscode-arduino",
        "ms-vscode.cpptools",
        "ms-python.python",
        "ms-python.vscode-pylance",
        "ms-python.vscode-python-envs",
        "platformio.platformio-ide"
      ]
    }
  },
  "remoteEnv": {
    "ARDUINO_BOARD_MANAGER_ADDITIONAL_URLS": "http://arduino.esp8266.com/stable/package_esp8266com_index.json https://espressif.github.io/arduino-esp32/package_esp32_dev_index.json",
    "SSH_AUTH_SOCK": "/ssh-agent"
  },
  "mounts": [
    "source=${env:SSH_AUTH_SOCK},target=/ssh-agent,type=bind",
    "source=/dev,target=/dev,type=bind"
  ]
}

```