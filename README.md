# Yggdrasil 0.5.14 for OpenWrt

This feed contains the OpenWrt package updated from `openwrt/packages` and the
official LuCI protocol integration from `openwrt/luci`.

## Contents

- `net/yggdrasil` — Yggdrasil 0.5.14 (`yggdrasil` and `yggdrasilctl`) with the
  netifd protocol handler.
- `protocols/luci-proto-yggdrasil` — full LuCI network protocol UI, active peer
  status via ubus/rpcd, multicast and peer sections, and Yggdrasil Jumper options.

The 0.5.14 `GroupPassword` setting is exposed as the `group_password` UCI
option and in LuCI. It is written to the generated Yggdrasil configuration as
`GroupPassword`.

## Installation in an OpenWrt buildroot

Copy `net/yggdrasil` into `package/network/yggdrasil` (or a custom feed) and
`protocols/luci-proto-yggdrasil` into `feeds/luci/protocols/`, then run:

```sh
./scripts/feeds update -a
./scripts/feeds install yggdrasil luci-proto-yggdrasil
make menuconfig
```

Select `Network → Routing and Redirection → yggdrasil` and
`LuCI → Protocols → luci-proto-yggdrasil`.

The source archive hash is pinned in the package Makefile. Yggdrasil 0.5.14
requires Go 1.25 or newer in the OpenWrt toolchain.

The CI matrix targets `rockchip/armv8` and `armvirt/64` (the latter produces
the `aarch64_generic` package architecture).
