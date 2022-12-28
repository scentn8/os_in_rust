docker container run -it --volume /Users/nakamura/rust/os_in_rust:/os_in_rust --name rust ubuntu:20.04 /bin/bash<br>
docker container start rust<br>
docker container exec -it rust /bin/bash<br>


apt update<br>
apt install curl<br>
apt install build-essential<br>
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh<br>
source $HOME/.cargo/env<br>
rustup override set nightly<br>
(rustup component add rust-src --toolchain nightly-aarch64-unknown-linux-gnu)<br>
cargo build<br>
cargo install bootimage<br>
rustup component add llvm-tools-preview<br>
cargo bootimage<br>

qemu-system-x86_64 -drive format=raw,file=target/target/debug/bootimage-os_in_rust.bin<br>