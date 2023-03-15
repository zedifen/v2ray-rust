FROM mcr.microsoft.com/devcontainers/rust:latest

# Get protobuf

RUN apt-get update

# Install CMake
RUN apt-get install cmake

# Install Clang
RUN apt-get install clang

# GitHub latest relase information API
ENV LATEST_RELEASE_API="https://api.github.com/repos/protocolbuffers/protobuf/releases/latest"

# Install jq
# RUN apt-get install jq

# Download with `jq` & `curl`
# RUN curl -LO $(curl -L $LATEST_RELEASE_API | jq '.assets[] | select(.name|match("linux-x86_64")) | .browser_download_url')

# Get download URL without `jq`
# Get latest relase information
# RUN export $JSON_FILENAME='protobuf-github-latest-release.json'
# RUN curl -L $LATEST_RELEASE_API > $JSON_FILENAME
# Latest release tagname
# RUN export LATEST_RELEASE_TAG=$(grep '"tag_name":' $JSON_FILENAME | sed -E 's/.*"([^"]+)".*/\1/')
# Latest browser download URL
# RUN export LATEST_RELEASE_URL=$(grep "download/$LATEST_RELEASE_TAG/protoc-$(echo $LATEST_RELEASE_TAG | cut -d v -f 2)-linux-x86_64" $JSON_FILENAME | sed -E 's/.*"([^"]+)".*/\1/')

RUN curl -LO $(curl -L $LATEST_RELEASE_API | grep -Eo "https://github.com/protocolbuffers/protobuf/releases/download/v[0-9]+\.[0-9]+/protoc-[0-9]+\.[0-9]+-linux-x86_64.zip")

# Install unzip
RUN apt-get install unzip
RUN mkdir protobuf
RUN unzip *.zip -d protobuf
RUN cp -r ./protobuf/include/* /usr/include/
RUN cp -r ./protobuf/bin/*     /usr/bin/
