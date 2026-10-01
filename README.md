# CF Proxy Worker

Worker proxy sederhana (VLESS / Trojan / Shadowsocks over WebSocket) + panel HTML statis.

## Struktur

- `src/worker.js` - logika proxy WebSocket -> TCP (`cloudflare:sockets`)
- `public/index.html` - panel web statis
- `wrangler.jsonc` - konfigurasi Wrangler (Static Assets)

## Deploy

### Opsi 1: Dari GitHub (tanpa API key)
1. Push repo ini ke GitHub
2. Dashboard Cloudflare -> Workers & Pages -> Import a repository -> pilih repo
3. Deploy (otomatis terdeteksi, build command kosong)

### Opsi 2: Dari lokal
```bash
npm install
npx wrangler login
npx wrangler deploy
```

## Catatan
- UDP tidak didukung
- VMess tidak termasuk (AEAD terlalu berat untuk CPU limit Workers)
- Path opsional `/IP:port` meng-override tujuan koneksi TCP
