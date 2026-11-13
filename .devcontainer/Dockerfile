ARG CUDA_VERSION=13.5.0
ARG UBUNTU_VERSION=26.04

FROM nvidia/cuda:${CUDA_VERSION}-devel-ubuntu${UBUNTU_VERSION}

RUN apt update && apt install -y \
    git \
    clangd \
    cmake \
    sccache \
    ninja-build \
    mold \
    clang \
    nano

ENV CMAKE_GENERATOR="Ninja" \
CC="clang" \
CXX="clang++" \
CUDAHOSTCXX="clang++" \
CMAKE_C_COMPILER_LAUNCHER="sccache" \
CMAKE_CXX_COMPILER_LAUNCHER="sccache" \
CMAKE_CUDA_COMPILER_LAUNCHER="sccache" \
CMAKE_EXPORT_COMPILE_COMMANDS="ON"

WORKDIR /workspaces