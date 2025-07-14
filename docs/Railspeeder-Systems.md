---
title: Systems Overview
parent: Home
nav_order: 1
layout: default
---

# Railspeeder Systems Overview

This page details all the systems and subsystems of the Railspeeder vehicle and
how they work together.

---

<!-- Edit with https://mermaid.live/ -->

```mermaid
---
config:
  theme: neo-dark
  layout: elk
---
flowchart LR

    subgraph CB[Control Board]
        PICO[Raspberry Pi Pico]
        ADC[AD58688 ADC]
        CAN[Can Interface]
        FAN[Fan Array]

        ADC-->|Analog|PICO

        PICO-->CAN
        PICO-->|PWM|FAN        
    end

    subgraph GDA[Gate Driver Array]
        UH[Gate Driver U High Side]
        UL[Gate Driver U Low Side]
        VH[Gate Driver V High Side]
        VL[Gate Driver V Low Side]
        WH[Gate Driver W High Side]
        WL[Gate Driver W Low Side]

        PICO-->|SPI + PWM|UH
        PICO-->|SPI + PWM|UL
        PICO-->|SPI + PWM|VH
        PICO-->|SPI + PWM|VL
        PICO-->|SPI + PWM|WH
        PICO-->|SPI + PWM|WL

    end

    subgraph PBI[Power Board Infra]
        PB[Power Board]
        IV[Isolated Voltage Sensor]

        PB-->|Phase and DC Link Currentr|ADC
        IV-->|Isolated Phase and DC Link Voltage|ADC
    end

    subgraph BC[Boost Convertor]
        R3[Arduino Uno R3]
        BCC[Boost Convertor Controls]
        CAB[Can Interface]

        R3-->BCC
        R3-->CAB
    end

    subgraph HMI[Human Media Interface]
        AM[Arduino Mega]
        CAH[Can Interface]

        AM-->CAH
    end

    subgraph CP[Control Panel]
        TC[Thin Client]
        AM-->|USB|TC
    end
```
