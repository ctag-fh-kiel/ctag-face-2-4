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
| spi4                   | TBD          | P8.17 Mode 7 | spi_cs0         | GPIO0_27     |
| spi3                   | TBD          | P8.32 Mode 7 | spi_clk         | GPIO0_11     |
| spi2                   | TBD          | P8.14 Mode 7 | spi_miso        | GPIO0_26     |
| spi1                   | TBD          | P8.33 Mode 7 | spi_mosi        | GPIO0_9      |
| RESET_IN               | TBD          | P8.34 Mode 7 | gpio2[17]       | GPIO2_17     |

For details about the expansion connectors check the [BeagleBone Black System Reference Manual](https://github.com/CircuitCo/BeagleBone-Black/blob/master/BBB_SRM.pdf) p. 82 ff.

## BeagleBoard-X15 <-> CTAG face2|4 Pin Connections

| CTAG face2&#124;4 Pin Name | CTAG face2&#124;4 Pin No. | BB-X15 Pin No. | BB-X15 Pin Name | AM5728 Ball | Muxmode	| Offset | Signal	|
|:-------------------------- |:------------------------- |:-------------- |:--------------- |:----------- |:------------|:------ |:-------------|
| DLRCLK                     | 10           		 | P17.52 	  | MCASP2_FSX      | A18	  | 0		| 0x2F8	 | mcasp2_fsx	|
| DBCLK                      | 8            		 | P17.21 	  | MCASP2_ACLKX    | A19	  | 0		| 0x2F4	 | mcasp2_aclkx	|
| ALRCLK                     | 7            		 | P17.57 	  | MCASP2_FSR      | A20	  | 0		| 0x300	 | mcasp2_fsr	|
| ABCLK                      | 9            		 | P17.44 	  | MCASP2_ACLKR    | E15	  | 0		| 0x2FC	 | mcasp2_aclkr	|
| DSDATA1                    | 18           		 | P17.18 	  | MCASP2_AXR2     | C15	  | 0		| 0x30C	 | mcasp2_axr2	|
| ASDATA1                    | 3            		 | P17.54 	  | MCASP2_AXR0     | B15	  | 0		| 0x304	 | mcasp2_axr0	|
| spi4	                     | 17           		 | P16.3   	  | GPIO4_17	    | A12	  | 3		| 0x2E0	 | spi3_cs0	|
| spi3                       | 15           		 | P16.34   	  | GPIO5_10	    | B12	  | 3		| 0x2D4	 | spi3_sclk	|
| spi2                       | 13           		 | P16.33   	  | GPIO5_12	    | B13	  | 3		| 0x2DC	 | spi3_d0	|
| spi1                       | 11           		 | P16.4   	  | GPIO5_11	    | A11	  | 3		| 0x2D8	 | spi3_d1	|
| RESET_IN                   | 4            		 | P17.25   	  | GPIO5_9         | D12	  | 14		| 0x2D0	 | gpio5_9	|

For details about the expansion connectors check out the [BeagleBoard-X15 Schematic](https://github.com/beagleboard/beagleboard-x15/blob/master/BeagleBoard-X15_RevA2.pdf?raw=true)
and [AM5728 datasheet](http://www.ti.com/lit/ds/symlink/am5728.pdf).
