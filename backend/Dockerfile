FROM ubuntu:24.04 AS builder

RUN apt-get update && apt-get install -y \
  build-essential \
  cmake \
  git \
  curl \
  zip \
  unzip \
  tar \
  pkg-config \
  ninja-build

ENV VCPKG_ROOT=/vcpkg
RUN git clone https://github.com/microsoft/vcpkg.git ${VCPKG_ROOT}
RUN cd ${VCPKG_ROOT} && \
  ./bootstrap-vcpkg.sh

WORKDIR /app

COPY . .

RUN cmake -G Ninja -B build -S . \
  -DCMAKE_TOOLCHAIN_FILE=${VCPKG_ROOT}/scripts/buildsystems/vcpkg.cmake

FROM ubuntu:24.04 AS runner

WORKDIR /app
COPY --from=builder /app .

CMD ["ls", "-la", "/app/build"]
