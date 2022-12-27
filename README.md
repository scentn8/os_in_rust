docker container run -it --volume /Users/nakamura/rust/os_in_rust:/os_in_rust --name rust ubuntu:20.04 /bin/bash
docker container start rust
docker container exec -it rust /bin/bash


apt update
apt install curl
apt install build-essential
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source $HOME/.cargo/env
rustup override set nightly
(rustup component add rust-src --toolchain nightly-aarch64-unknown-linux-gnu)
cargo build
cargo install bootimage
rustup component add llvm-tools-preview
cargo bootimage

qemu-system-x86_64 -drive format=raw,file=target/target/debug/bootimage-os_in_rust.bin