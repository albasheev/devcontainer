ARG CUDA_VERSION=13.5.0
ARG UBUNTU_VERSION=26.04

FROM nvidia/cuda:${CUDA_VERSION}-devel-ubuntu${UBUNTU_VERSION}

RUN apt-get update && apt-get install -y \
    git \
    clangd-22 \
    cmake \
    ccache \
    ninja-build \
    mold \
    clang-22 \
    nano && \
    update-alternatives --install /usr/bin/clang clang /usr/bin/clang-22 100 && \
    update-alternatives --install /usr/bin/clang++ clang++ /usr/bin/clang++-22 100 && \
    update-alternatives --install /usr/bin/clangd clangd /usr/bin/clangd-22 100

ENV CMAKE_GENERATOR="Ninja" \
    CC="clang" \
    CXX="clang++" \
    CUDAHOSTCXX="clang++" \
    CMAKE_C_COMPILER_LAUNCHER="ccache" \
    CMAKE_CXX_COMPILER_LAUNCHER="ccache" \
    CMAKE_CUDA_COMPILER_LAUNCHER="ccache" \
    CMAKE_EXPORT_COMPILE_COMMANDS="ON" \
    LDFLAGS="-fuse-ld=mold"

WORKDIR /workspaces
