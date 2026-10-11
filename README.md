# Session 11 - Homework Ex4: Secrets và đăng nhập GHCR

Kế thừa Ex3, bổ sung bước đăng nhập Registry trong `.github/workflows/ci.yml:37`:

```yaml
- name: Đăng nhập vào GitHub Container Registry
  uses: docker/login-action@v3
  with:
    registry: ghcr.io
    username: ${{ github.actor }}
    password: ${{ secrets.REGISTRY_TOKEN }}
```

## Tạo Secret
1. Tạo PAT (classic) với quyền `write:packages` tại https://github.com/settings/tokens
2. Vào repo Settings → Secrets and variables → Actions → New repository secret
3. Tên: `REGISTRY_TOKEN`, dán token vừa tạo.

## Kiểm tra
Push lên `main`, mở log bước Đăng nhập Registry, xác nhận `Login Succeeded`.
