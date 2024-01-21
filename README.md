# actions-mkarchiso
Build an archiso on github actions

> Note that this can only be used in an archlinux container with the `--privileged` flag

```yaml
on:
  push:
    branches: [main]

name: Build ISO

jobs:
  build:
    runs-on: ubuntu-latest
    container: 
      image: archlinux
      options: --privileged
    steps: 
      - name: Checkout
        uses: actions/checkout@v4
      - name: Build ISO
        uses: coderadu/actions-mkarchiso@v1
      - name: Upload ISO
        uses: actions/upload-artifact@v4
        with:
          name: archlinux-iso
          path: out/
```