# Hortus Deliciarum

Orchestra di non-strumenti meccanizzati. Work in progress seguìto a una commissione del `To Listen To` Festival (settembre 2022). L'idea è quella di realizzare una serie di strumenti totalmente autocostruiti, sulla base della seguente catena strutturale:

```mermaid
flowchart LR

    subgraph E["Elemento Vibrante"]
    direction TD
        Material
        ESP32-->Motor
    end

    subgraph B["Microfono"]
        direction TD
        Piezoelectric
        Electret
    end

    subgraph D["DSP Processing"]
        Rock Pi S
    end

    subgraph D["Riproduzione"]
        direction TD
        Car Speaker
        Cheap Speaker
    end

    E --> B --> D --> S
```

