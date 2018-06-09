# DESCRIPTION:	  Create Visual Studio Community Edition in a container
# AUTHOR:		  Doug Rathbone <doug@dougrathbone.com>
# COMMENTS:
#	This file describes how to build Visual Studio Community edition
#	in a container with all dependencies installed.
#	Tested on Windows 10.
# USAGE:
#	# Download visual studio Dockerfile
#	wget https://raw.githubusercontent.com/dougrathbone/dockerfiles/visualstudio/Dockerfile
#
#	# Build visual studio image
#	docker build -t visualstudio .
#
# # Run docker image containing visual studio and msbuild
#	docker run visualstudio
#

FROM microsoft/windowsservercore:latest

LABEL maintainer "Doug Rathbone <doug@dougrathbone.com>"

SHELL ["powershell"]

# Download Visual Studio's binary
RUN Invoke-WebRequest "https://aka.ms/vs/15/release/vs_community.exe" -OutFile "$env:TEMP\\vs_community.exe" -UseBasicParsing

# Run the installer
# CLI args for reference: https://docs.microsoft.com/en-us/visualstudio/install/command-line-parameter-examples
RUN & "$env:TEMP\\vs_community.exe" --includeRecommended --includeOptional --quiet --wait --norestart --noUpdateInstaller | Out-Default

CMD ["powershell"]
