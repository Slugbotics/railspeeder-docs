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
flowchart LR

    subgraph CB[Control Board]
        PICO[Raspberry Pi Pico]
        ADC[AD58688 ADC]
        CAN[Can Interface]
        FAN[Fan Array]

        ADC-->|Analog|PICO

        PICO-->CAN
        PICO-->|PWM|FAN

        PICO-->|SPI + PWM|GDA
    end

    subgraph GDA[Gate Driver Array]
        UH[Gate Driver U High Side]
        UL[Gate Driver U Low Side]
        VH[Gate Driver V High Side]
        VL[Gate Driver V Low Side]
        WH[Gate Driver W High Side]
        WL[Gate Driver W Low Side]
    end
```
