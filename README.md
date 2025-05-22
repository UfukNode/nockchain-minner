# ✅ Nockchain Miner Node Kurulum Rehberi:

## Sistem Gereksinimleri:

| Gereksinim       | Detaylar                   |
|------------------|----------------------------|
| RAM              | En az 16 GB (Önerilen: 32 GB)|
| CPU              | 6 Çekirdek (Önerilen: 8)   |
| Depolama         | 200 GB SSD (Önerilen: 400+) |

⚠️ Bunlar tamamen tahminidir. Açıklama geldiğinde güncelleyeceğim.

---

## 1- Sistem Güncellemesi ve Gereklilikler:
```bash
sudo apt update && sudo apt upgrade -y
sudo apt install build-essential curl git make clang llvm-dev libclang-dev -y
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

## 4- Ortam Dosyasını Kopyala:

```bash
cp .env_example .env
```

---

## 4- Derleyiciyi (Hoonc) Kur:
```bash
make install-hoonc
```

---

## 5- Projeyi Derle (Uzun Sürebilir):
```bash
make build
```

---

## 6- Cüzdan ve Node Kurulumunu Yap (Uzun Sürebilir):
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
📌 Çıkan `public key`'i, `private key`'i ve `memo`yu bir yere not al. Bu, madencilik adresindir.

---

## Cüzdanı Yedekleyip İçe Aktar:

### A- Yedekle:
```bash
nockchain-wallet export-keys
```
Bu komut ile cüzdanınız `export-keys` dosyasına kaydedilecek.

### B- İçe Aktar:
```bash
nockchain-wallet import-keys --input keys.export
```

---

## 9- .env içine public key’i ekle:
```bash
nano .env
```
📌`MINING_PUBKEY =` satırını bul ve yukarıda oluşturduğun public key'in ile değiştir. 
Kaydetmek için: `Ctrl + X`, sonra `Y`, sonra `Enter`

---

## 10- Screen Oluştur:

```bash
screen -S nock
```

---

## 11- Node’u başlat:
```bash
nockchain --mining-pubkey <senin_public_key> --mine
```
📌`senin_public_key =` satırını yukarıda oluşturduğun public key'in ile değiştir.

---

##Screen Komutları:
- `Ctrl + A`, ardından `D` ile arka plana al
- Geri dönmek için: `screen -r nock`

---
