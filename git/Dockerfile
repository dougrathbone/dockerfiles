# DESCRIPTION:	Create Git for Windows in a container
# AUTHOR:	Doug Rathbone <doug@dougrathbone.com>
# COMMENTS:
#	This file describes how to build Git for Windows
#	in a container with all dependencies installed.
#	Tested on Windows 10.
# USAGE:
#	# Download git Dockerfile
#	wget https://raw.githubusercontent.com/dougrathbone/dockerfiles/git/Dockerfile
#
#	# Build visual studio image
#	docker build -t git .
#
# # Run docker image containing Git for Windows
#	docker run git
#

FROM microsoft/windowsservercore:latest

LABEL maintainer "Doug Rathbone <doug@dougrathbone.com>"

SHELL ["powershell"]

# Install Git (via chocolatey for simplicity sake)
RUN Set-ExecutionPolicy Bypass -Scope Process -Force; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
RUN & "choco install git -y"

# Add Git to PATH
RUN $Env:Path += 'C:\\Program Files\\Git\\cmd'

# Print the Git Version installed
RUN & "git version"

CMD ["powershell"]
