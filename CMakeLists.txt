cmake_minimum_required(VERSION 3.15)
project(STM32L4xx_hal_driver
        VERSION 1.11.0
        DESCRIPTION "STM32L4xx HAL as a CMake package"
        LANGUAGES C ASM)

include_guard(GLOBAL)

if(DEFINED cmsis_MCU)
    message(STATUS "STM32L4::HAL : Configuring for MCU == ${cmsis_MCU}")
else()
    message(FATAL_ERROR "STM32L4::HAL : cmsis_MCU is not defined!")
endif()

add_library(STM32L4xx_HAL INTERFACE)
add_library(STM32L4::HAL ALIAS STM32L4xx_HAL)

option(STM32l4xx_USE_HAL_DRIVER "Enable the high level STM32L4 HAL" OFF)

target_include_directories(STM32L4xx_HAL INTERFACE
        Inc
        Inc/Legacy)

target_compile_definitions(STM32L4xx_HAL INTERFACE ${cmsis_MCU})

target_sources(STM32L4xx_HAL INTERFACE
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_ll_adc.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_ll_comp.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_ll_crc.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_ll_crs.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_ll_dac.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_ll_dma.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_ll_dma2d.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_ll_exti.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_ll_fmc.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_ll_gpio.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_ll_i2c.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_ll_lptim.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_ll_pka.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_ll_lpuart.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_ll_opamp.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_ll_pwr.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_ll_rcc.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_ll_rng.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_ll_rtc.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_ll_sdmmc.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_ll_spi.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_ll_swpmi.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_ll_tim.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_ll_usart.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_ll_usb.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_ll_utils.c
        )

if(STM32l4xx_USE_HAL_DRIVER)
    target_compile_definitions(STM32L4xx_HAL INTERFACE USE_HAL_DRIVER)
    target_sources(STM32L4xx_HAL INTERFACE
        ${CMAKE_CURRENT_LIST_DIR}/Src/Legacy/stm32l4xx_hal_can.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_adc.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_adc_ex.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_can.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_comp.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_cortex.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_crc.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_crc_ex.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_cryp.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_cryp_ex.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_dac.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_dac_ex.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_dcmi.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_dfsdm.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_dfsdm_ex.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_dma.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_dma_ex.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_dma2d.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_dsi.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_exti.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_firewall.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_flash.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_flash_ex.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_flash_ramfunc.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_gfxmmu.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_gpio.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_hash.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_hash_ex.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_hcd.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_i2c.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_i2c_ex.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_irda.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_iwdg.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_lcd.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_lptim.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_ltdc.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_ltdc_ex.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_mmc.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_mmc_ex.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_nand.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_nor.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_opamp.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_opamp_ex.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_ospi.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_pcd.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_pcd_ex.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_pka.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_pssi.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_pwr.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_pwr_ex.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_qspi.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_rcc.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_rcc_ex.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_rng.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_rng_ex.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_rtc.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_rtc_ex.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_sai.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_sai_ex.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_sd.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_sd_ex.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_smartcard.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_smartcard_ex.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_smbus.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_spi.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_spi_ex.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_sram.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_swpmi.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_tim.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_tim_ex.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_tsc.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_uart.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_uart_ex.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_usart.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_usart_ex.c
        ${CMAKE_CURRENT_LIST_DIR}/Src/stm32l4xx_hal_wwdg.c
        )
endif()
