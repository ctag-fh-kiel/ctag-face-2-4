## BeagleBone Black/Green <-> CTAG face2|4 Pin Connections 

| CTAG face2&#124;4 Pin Name | CTAG face2&#124;4 Pin No. |BB Black/Green Pin No. | BB Black/Green Mode Name | BB Black/Green Pin Name |
| ---------------------- |:------------:|:------------:| --------------- | ------------ |
| DLRCLK                 | 10           | P9.29 Mode 0 | mcasp0_fsx      | SPI1_DO      |
| DBCLK                  | 8            | P9.31 Mode 0 | mcasp0_aclkx    | SPI1_SCLK    |
| ALRCLK                 | 7            | P9.27 Mode 0 | mcasp0_fsr      | GPIO3_19     |
| ABCLK                  | 9            | P9.12 Mode 6 | mcasp0_aclkr    | GPIO1_28     |
| DSDATA1                | 18           | P9.28 Mode 2 | mcasp0_axr2     | SPI1_CS0     |
| ASDATA1                | 3            | P9.30 Mode 0 | mcasp0_axr0     | SPI1_D1      |
| spi4                   | 17           | P9.17 Mode 0 | spi0_cs0        | I2C1_SCL     |
| spi3                   | 15           | P9.22 Mode 0 | spi0_sclk       | UART2_RXD    |
| spi2                   | 13           | P9.21 Mode 0 | spi0_d0         | UART2_TXD    |
| spi1                   | 11           | P9.18 Mode 0 | spi0_d1         | I2C1_SDA     |
| RESET_IN               | 4            | P9.15 Mode 7 | gpio1[16]       | GPIO1_16     |

## BeagleBone Black/Green <-> CTAG face2|4 SW SPI Pin Connections 

| CTAG face2&#124;4 Pin Name | CTAG face2&#124;4 Pin No. |BB Black/Green Pin No. | BB Black/Green Mode Name | BB Black/Green Pin Name |
| ---------------------- |:------------:|:------------:| --------------- | ------------ |
| DLRCLK                 | 10           | P9.29 Mode 0 | mcasp0_fsx      | SPI1_DO      |
| DBCLK                  | 8            | P9.31 Mode 0 | mcasp0_aclkx    | SPI1_SCLK    |
| ALRCLK                 | 7            | P9.27 Mode 0 | mcasp0_fsr      | GPIO3_19     |
| ABCLK                  | 9            | P9.12 Mode 6 | mcasp0_aclkr    | GPIO1_28     |
| DSDATA1                | 18           | P9.28 Mode 2 | mcasp0_axr2     | SPI1_CS0     |
| ASDATA1                | 3            | P9.30 Mode 0 | mcasp0_axr0     | SPI1_D1      |
| spi5                   | TBD          | P8.31 Mode 7 | spi_cs1         | GPIO0_10     |
| spi4                   | TDB          | P8.17 Mode 7 | spi_cs0         | GPIO0_27     |
| spi3                   | TDB          | P8.32 Mode 7 | spi_clk         | GPIO0_11     |
| spi2                   | TDB          | P8.14 Mode 7 | spi_miso        | GPIO0_26     |
| spi1                   | TDB          | P8.33 Mode 7 | spi_mosi        | GPIO0_9      |
| RESET_IN               | TDB          | P8.34 Mode 7 | gpio2[17]       | GPIO2_17     |



For details about the expansion connectors check the [BeagleBone Black System Reference Manual](https://github.com/CircuitCo/BeagleBone-Black/blob/master/BBB_SRM.pdf) p. 82 ff.
