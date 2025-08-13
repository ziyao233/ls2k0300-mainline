# Mainline status and reference materials for Loongson 2K0300 SoC

This repository is a summary of mainline status of Loongson 2K0300 SoC, and
contains misc reference materials for development.

## Mainline Status

### Components that require driver changes

- Clock controller: Yao Zi, under review [v3](https://lore.kernel.org/all/20250805150147.25909-1-ziyao@disroot.org/)
  on 2025.08.05
- Reset controller: Yao Zi, in progress
  - It's planned to use reset-simple
- External interrupt controllers: N/A
  - The IOCSR layout of eiointcs on 2K0300 differs from other SoCs
- GPIO controller: Yao Zi, in progress
- Watchdog: N/A
- I2C: N/A
- USB OTG: N/A
- Thermal sensor: N/A
  - Vendor driver looks scary. :-P

### Components that may require dt-binding changes only

- Basic devicetree: by Yao Zi, under review [v3](https://lore.kernel.org/all/20250523095408.25919-1-ziyao@disroot.org/)
  on 2025.05.23
- Pinctrl controller: Yao Zi, under review [v1](https://lore.kernel.org/all/20250811163749.47028-2-ziyao@disroot.org/)
  - ~~It was planned to reuse pinctrl-single driver~~ 2K0300 comes with a
    separate register for drive-strength configuration, thus it doesn't match
    pinctrl-single.
- SDIO/eMMC: Yao Zi, in progress
  - Depends on ["LoongArch: Introduce the Loongson-2K MMC host controller driver"](https://lore.kernel.org/all/cover.1750765495.git.zhoubinbin@loongson.cn/)
    that landed in v6.17
  - Compatible with the 2K2000 variant, but there seems to be some
    [unique quirk](https://gitee.com/open-loongarch/linux-6.12/blob/master/drivers/mmc/host/ls2kmci.c#L783)
- SPI controller: N/A
- GMAC: N/A
- USB Host: N/A
- Display controller: N/A
- DMA: N/A

## Reference Materials

- [Datasheet](https://loongson.cn/uploads/images/2024120211202744746.%E9%BE%99%E8%8A%AF2K0300%E5%A4%84%E7%90%86%E5%99%A8%E6%95%B0%E6%8D%AE%E6%89%8B%E5%86%8C_V1.0.pdf)
  released by Loongson: v1.0, Nov. 2024
- [User manual](https://loongson.cn/uploads/images/2023042109171499358.%E9%BE%99%E8%8A%AF2K0500%E5%A4%84%E7%90%86%E5%99%A8%E7%94%A8%E6%88%B7%E6%89%8B%E5%86%8C_v1.0.pdf)
  released by Loongson: v1.0, Nov. 2024. This plays the role of Technical
  Reference Manual (TRM) and contains technical details such as register
  definitions.
- [Downstream 6.12 kernel](https://gitee.com/open-loongarch/linux-6.12/)
- [Downstream U-Boot](https://gitee.com/open-loongarch/u-boot)

## Summaries

- [Clock definitions](/clk-summary.md)

## Available Hardwares on the Market

- CTCISZ, Forever Pi (久久派)
  - Two variants, TF-card version and WiFi version
  - 512MiB DDR4 RAM
  - On-board 8GiB eMMC storage (WiFi version only)
  - SD Card support (TF-card version only)
  - 2 USB 2.0 Ports (OTG and HOST)
  - 1 GbE Ethernet port
  - WiFi/BT support (WiFi version only)
  - Audio output through 3.5mm phone connector
  - Display output through RAW RGB interface (WiFi version only)
  - On-board SPI Flash
  - [Official collection of reference materials](https://bbs.ctcisz.com/forum.php?mod=viewthread&tid=2):
     must be logind for downloading
  - This is the primary device that I'm working on
