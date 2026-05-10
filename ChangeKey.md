```bash
# 1. 生成一把新的 2048 位 RSA 私钥
# 生成后妥善保管，并以此更新 GitHub Secrets(PRIVATE_KEY)
openssl genrsa -out private.pem 2048

# 2. 从该私钥中生成自签名的 X.509 证书（作为加密使用的公钥凭证）
# 将其保存为 public.pem，并提交到本代码库中
openssl req -new -x509 -key private.pem -out public.pem -days 36500  -subj "/CN=accounts"
```