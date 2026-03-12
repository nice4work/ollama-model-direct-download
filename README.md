# Ollama Model Direct Link Generator and Installer

## Overview

The Ollama Model Direct Link Generator and Installer is a utility designed to streamline the process of obtaining direct
download links for Ollama models and installing them. This tool is intended for developers, researchers, and enthusiasts
interested in Ollama models, providing a straightforward and efficient solution.
_________

## [New Tutorial & Documentation](https://amirrezadev1378.github.io/ollama-model-direct-download/)

___________
### Table of Contents

- [Introduction](#Introduction)
- [Usage](#Usage)
- [Contributing](#Contributing)
- [License](#License)

## Introduction

This command-line interface (CLI) tool generates direct download links for Ollama models and allows automatic installation for locally available model files. Written in Golang, it utilizes the Requests library to fetch the necessary links.

Key functionalities include:

- Generating direct download links for Ollama models quickly.
- Installing locally available Ollama models.

## Note

This program doesn't validate what you have downloaded. I will just copy all the files to the model folder to install it to Ollama. Its recommended that you verify checksums manually.

## Usage

- Download the binary files based on your OS and processor architecture
  from [Release page](https://github.com/amirrezaDev1378/ollama-model-direct-download/releases).
- ### Generate Direct Download Links
    - Run the binary file in your terminal Using this command `omdd get deepseek-coder-v2:latest`.
    - Wait for the tool to fetch the download link.
    - Download all the fetched files.
- ### Install Ollama Models
    - First make sure to create a backup of your current models.
      [Where are ollama models stored?](https://github.com/ollama/ollama/blob/main/docs/faq.md#where-are-models-stored)
    - Store your models and your manifest file in any folder.
      The manifest file must be named 'manifest' without any file extension.
    - Run the following command:
    - `omdd install --model=<model-name> --blobsPath=<downloaded-blobs-path>`.
    - Replace `<model-name>` with the name of your model and `<downloaded-blobs-path>` with the path to the folder where you stored model files & manifest.
    - The tool will now install the model. It may take a while. Don't worry if it seems stuck.
    - Once its finished, you can run the model from Ollama normally with command `ollama run <model-name>`

## Contributing

- Clone the repository to your local machine.
- Install the dependencies using `go mod tidy`.
- Make your changes.
- Run the tests using `go test ./...`.
- Build the binary using `make build`.


# example

step 1 get download address

example 1 (replace qwen2.5-coder:7b with your own model)
```shell
joy:bin joy$ ./omdd get qwen2.5-coder:7b
Fetching direct download link for model: qwen2.5-coder:7b
Manifest download link: https://registry.ollama.ai/v2/library/qwen2.5-coder/manifests/7b
Download links for layers:
1 - https://registry.ollama.ai/v2/library/qwen2.5-coder/blobs/sha256:60e05f2100071479f596b964f89f510f057ce397ea22f2833a0cfe029bfc2463
2 - https://registry.ollama.ai/v2/library/qwen2.5-coder/blobs/sha256:66b9ea09bd5b7099cbb4fc820f31b575c0366fa439b08245566692c6784e281e
3 - https://registry.ollama.ai/v2/library/qwen2.5-coder/blobs/sha256:1e65450c30670713aa47fe23e8b9662bdf4065e81cc8e3cbfaa98924fcc0d320
4 - https://registry.ollama.ai/v2/library/qwen2.5-coder/blobs/sha256:832dd9e00a68dd83b3c3fb9f5588dad7dcf337a0db50f7d9483f310cd292e92e
5 - https://registry.ollama.ai/v2/library/qwen2.5-coder/blobs/sha256:d9bb33f2786931fea42f50936a2424818aa2f14500638af2f01861eb2c8fb446
Generated download links for model: qwen2.5-coder:7b
Finished successfully!
```

step 2 get your manifest
get your manifest (replace qwen2.5-coder and 7b with your own model and tag)
```shell
curl -s https://registry.ollama.ai/v2/library/qwen2.5-coder/manifests/7b >  manifest
```

step 3 install download model to ollama
```shell
sudo ./omdd install --model=qwen2.5-coder:7b --blobsPath=/Users/joy/Downloads/qwen2.5-coder
```

step 4 
```shell
➜  ollama list                                                                         
NAME                       ID              SIZE      MODIFIED      
qwen2.5-coder:7b           dae161e27b0e    4.7 GB    9 minutes ago    
qwen2.5-coder:32b          b92d6a0bd47e    19 GB     18 hours ago     
qwen3-coder-next:latest    ca06e9e4087c    51 GB     8 days ago
```


## License

MIT License