
#
#   Copyright 2018-2025 Hugo López-Fernández, Pedro M. Ferreira,
#   Miguel Reboiro-Jato, Cristina P. Vieira, and Jorge Vieira
#
#   Licensed under the Apache License, Version 2.0 (the "License");
#   you may not use this file except in compliance with the License.
#   You may obtain a copy of the License at
#
#       http://www.apache.org/licenses/LICENSE-2.0
#
#   Unless required by applicable law or agreed to in writing, software
#   distributed under the License is distributed on an "AS IS" BASIS,
#   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
#   See the License for the specific language governing permissions and
#   limitations under the License.
#

# LABEL contributor="pegi3s"

FROM debian:stable-slim

# Update commands and install dependencies
RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        build-essential \
        wget \
        ca-certificates \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /opt/muscle

# Download and extract MUSCLE
RUN wget -q https://www.drive5.com/muscle/downloads3.8.31/muscle3.8.31_src.tar.gz \
    && tar -xzf muscle3.8.31_src.tar.gz \
    && rm muscle3.8.31_src.tar.gz

# Compile MUSCLE
RUN cd muscle3.8.31/src \
    && make CXXFLAGS='-Wno-c++11-narrowing' -j$(nproc) \
    && mv muscle /usr/local/bin \
    && cd ../.. \
    && rm -r muscle3.8.31

# General clear
RUN apt-get remove --purge -y build-essential wget \
    && apt-get autoremove -y \
    && apt-get clean

# Default command for the docker image
ENTRYPOINT ["muscle"]

