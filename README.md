# ✅ Nockchain Miner Node Kurulum Rehberi:

## 1- Sistem Güncellemesi ve Gereklilikler:
```bash
sudo apt update && sudo apt upgrade -y
sudo apt install build-essential curl git make -y
```

---

## 2- Rust Kurulumu:
```bash
curl https://sh.rustup.rs -sSf | sh -s -- -y
source $HOME/.cargo/env
```

---

## 3- Repoyu Klonla:
```bash
git clone https://github.com/zorp-corp/nockchain
cd nockchain
```

---

## 4- Derleyiciyi (Hoonc) Kur:
```bash
make install-hoonc
```

---

## 5- Projeyi Derle:
```bash
make build
```

---

## 6- Cüzdan ve Node Kurulumunu Yap (Uzun sürebilir):
```bash
make install-nockchain-wallet
make install-nockchain
```

---

## 7- PATH değişkenine target/release ekle:
```bash
export PATH="$PATH:$(pwd)/target/release"
```

---

## 8- Cüzdan oluştur (public key al):
```bash
nockchain-wallet keygen
```
> Çıkan **public key**'i ve **private key**'i bir yere not al. Bu, madencilik adresindir.

---

## 9- Makefile içine public key’i elle ekle:
```bash
nano Makefile
```
> `MINING_PUBKEY =` satırını bul ve yukarıda oluşturduğun public key'in ile değiştir.
> Kaydetmek için: `Ctrl + X`, sonra `Y`, sonra `Enter`

---

## 10- Screen Oluştur:

```bash
screen -S nock
```

---

## 11- Node’u başlat:
```bash
make run-nockchain
```
> `Ctrl + A`, ardından `D` ile arka plana al
> Geri dönmek için: `screen -r nock`

---

## ✅ Hepsi bu kadar. Artık node’un çalışıyor.
