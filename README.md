docker container run -it --volume /Users/nakamura/rust/os_in_rust:/os_in_rust --name rust ubuntu:20.04 /bin/bash<br>
docker container start rust<br>
docker container exec -it rust /bin/bash<br>


apt update<br>
apt install curl<br>
apt install git<br>
apt install build-essential<br>
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh<br>
source $HOME/.cargo/env<br>
<!-- 開発時に便利なツールをコンポーネントとして追加 -->
rustup component add rls rust-src rust-analysis
rustup override set nightly<br>
rustup component add rust-src --toolchain nightly-aarch64-unknown-linux-gnu<br>
cargo build<br>
cargo install bootimage<br>
rustup component add llvm-tools-preview<br>
cargo bootimage<br>

qemu-system-x86_64 -drive format=raw,file=target/target/debug/bootimage-os_in_rust.bin<br>

https://qiita.com/notakaos/items/9f3ee8a3f3a0caf39f7b
cargo install cargo-edit
cargo add <パッケージ名>
cargo upgrade <パッケージ名>
cargo rm <パッケージ名>
rustup component add rustfmt
cargo fmt

https://os.phil-opp.com/ja/vga-text-mode/