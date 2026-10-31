FROM alpine:latest AS builder

RUN apk update && apk add --no-cache \
  build-base \
  cmake \
  ninja \
  zip \
  unzip \
  curl \
  git

ENV VCPKG_ROOT=/vcpkg
ENV VCPKG_FORCE_SYSTEM_BINARIES=1
ENV VCPKG_DEFAULT_TRIPLET=x64-linux

RUN git clone https://github.com/microsoft/vcpkg.git ${VCPKG_ROOT} && \
  cd ${VCPKG_ROOT} && \
  ./bootstrap-vcpkg.sh

WORKDIR /app

ENV CMAKE_TOOLCHAIN_FILE=${VCPKG_ROOT}/scripts/buildsystems/vcpkg.cmake

COPY vcpkg.json CMakeLists.txt ./
RUN cmake -G Ninja -B build -S . \
  -DCMAKE_TOOLCHAIN_FILE=${CMAKE_TOOLCHAIN_FILE} \
  -DVCPKG_TARGET_TRIPLET=${VCPKG_DEFAULT_TRIPLET}

# COPY . .

# RUN cmake -B build -S . -DCMAKE_TOOLCHAIN_FILE=${CMAKE_TOOLCHAIN_FILE}
# RUN cmake --build build

# WORKDIR /app

# FROM alpine:latest
