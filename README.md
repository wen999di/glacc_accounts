## 加密账号文件

### Windows (命令提示符 CMD)
```cmd
for %f in (accounts\*.dat) do openssl smime -encrypt -binary -aes-256-cbc -in "%f" -out "%f.enc" -outform DER public.pem
```

### Windows (PowerShell)
```powershell
Get-ChildItem -Path accounts -Filter *.dat | ForEach-Object { openssl smime -encrypt -binary -aes-256-cbc -in $_.FullName -out "$($_.FullName).enc" -outform DER public.pem }
```

### Linux / macOS
```bash
for file in accounts/*.dat; do openssl smime -encrypt -binary -aes-256-cbc -in "$file" -out "$file.enc" -outform DER public.pem; done
```

> **⚠️ 注意**：
> 加密完成后，你只需将 `.dat.enc` 推送到 GitHub。
> 请**绝对不要**推送原始的明文 `.dat` 文件！