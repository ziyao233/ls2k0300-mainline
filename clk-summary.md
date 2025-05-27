# refclk

- clk_stable
  - run at fixed 120MHz
- pll_node
- pll_ddr
- pll_pix
- clk_thsens
  - divided by 120 (1MHz)

# Node PLL

- clk_node
  - for LA264, Scache and IODMA
  - divider
  - gate
  - freqscale
  - gate again
- clk_gmac
  - divider
  - gate
- clk_i2s
  - divider
  - scale
  - gate

# DDR PLL

- clk_ddr
  - divider
  - gate
- clk_net
  - divider
  - gate
- clk_dev
  - divider
  - gate

## clk_dev

- clk_usb
  - scale
  - gate
- clk_apb
  - scale
  - gate
- clk_boot
  - scale
  - gate
- clk_sdio
  - incomplete scale: really a divider
  - isn't zero-based: setting to zero has the same effect as one

# PIX PLL

- clk_pix
  - divider
  - gate
  - freqscale
  - gate again
- clk_gmacbp
  - divider
  - gate

# Additional

- clk_gmac_in
  - mux
  - possible parents: clk_gmac, clk_gmacbp
