# Hortus Deliciarum

Orchestra di non-strumenti meccanizzati. Work in progress seguìto a una commissione del `To Listen To` Festival (settembre 2022). L'idea è quella di realizzare una serie di strumenti totalmente autocostruiti, sulla base della seguente catena strutturale:

```mermaid
flowchart LR

    subgraph E["Elemento Vibrante"]
        Material
        ESP32-->Motor
    end

    subgraph B["Microfono"]
        direction TB
        Piezoelectric
        Electret
    end

    subgraph D["DSP Processing"]
        direction TB
        R["Rock Pi S"]
    end

    subgraph S["Riproduzione"]
        direction TB
        CA["Car Speaker"]
        CH["Cheap Speaker"]
    end

    E --> B --> D --> S
```

```mermaid
flowchart LR

A["Elemento Vibrante"]-->B["Microfono"]-->C["DSP Processing"]-->D["Riproduzione"]
```

## strumenti

1. player
2. symphonia
3. fan-ball
4. fan-ironball
5. table
6. guitar
7. rotor
8. mask

### player

```mermaid
flowchart TB

classDef pow fill:#FF0000

subgraph S["speaker"]
    direction LR
    amplifier --> speaker
    _pow2_["power 9-12V"]:::pow-.-o amplifier
end

subgraph play["player"]
    direction LR
    _pow1_["power 5V/USB"]:::pow-.-oESP32 --> I2S
    wifi-->ESP32
end

I2S-->amplifier
```

### symphonia

```mermaid
flowchart LR

classDef ppp fill:#FF0000
classDef sp fill:#009900

subgraph symphonia[<div><b>symphonia</b></div><div>stocazzo</div>]
    direction LR
    subgraph sound["sound production"]
        direction TB
        p(["power 5v"]):::ppp --> ESP32
        ESP32 --> motor_1 --- string_1
        ESP32 --> motor_2 --- string_2
        ESP32 --> motor_3 --- string_3
    end

    subgraph S["speaker"]
        direction TB
        amplifier --> speaker
    end

    subgraph dsp["rock"]
        direction TB
        r1([rotrock]) --- |OR| r2([potrock])
    end

    string_1-.-o piezo1((piezo))-->dsp-->S
    string_2-.-o piezo2((piezo))-->dsp
    string_3-.-o piezo3((piezo))-->dsp
end

sound:::sp
```

### fan-ball

```mermaid
flowchart LR

subgraph S["speaker"]
    direction TB
    amplifier --> speaker
end

fanball-->electret-->amplifier
```

### fan-iron-ball

```mermaid
flowchart LR

subgraph S["speaker"]
    direction TB
    amplifier --> speaker
end

fanIronBall-->piezo-->amplifier
```

### table

### guitar

```mermaid
flowchart LR

subgraph S["speaker"]
    direction TB
    amplifier --> speaker
end

subgraph dsp["rock"]
    direction TB
    r1([rotrock]) --- |OR| r2([potrock])
end

strings-->pickup-->dsp:::someclass-->amplifier
speaker-->pickup

classDef someclass fill:#f96;
```

### rotor

```mermaid
flowchart LR

subgraph Spe["speaker"]
    direction TB
    amplifier --> speaker
end

subgraph Rot["rotor"]
    direction TB
    motor -.- piezo((piezo))
    power(["power 12V"]) --o motor
end

subgraph dsp["rock"]
    direction TB
    r1([rotrock]) --- |OR| r2([potrock])
end


piezo-->dsp-->Spe
```

### mask

```mermaid
flowchart LR

subgraph prod["sound production"]
    direction TB
    breath -.-o electret((electret))
end

bat([battery 9V]) --> electret

subgraph S["speaker"]
    direction TB
    amplifier --> speaker
end

electret-->amplifier
bat-->amplifier
```



