# network credentials

```bash
ssid: HORTUS
password: francesco
gateway: 192.168.0.1
netmask: 255.255.255.0
```

# network addresses

```mermaid
flowchart LR
    
    subgraph FAN
        fanip(["IP: 192.168.0.20"])
    end

    subgraph ROTOR
        rotorip(["IP: 192.168.0.30"])
    end

    subgraph SYMPHONIA
        symphoniaip(["IP: 192.168.0.40"])
    end

    subgraph PC
        pcip(["IP: 192.168.10"])
    end

    subgraph ROTROCK
        rotip(["IP: 192.168.0.x"])
    end

    subgraph PLAYER
        playerip(["IP: 192.168.0.50"])
    end

    subgraph GUITAR
        guitarip(["IP: 192.168.0.60"])
    end

    subgraph POTROCK4
        potrock_esp32_ip(["IP: 192.168.0.65"])
    end

    rotorip o----o pcip
    fanip o----o pcip
    ROTOR o----o ROTROCK
    symphoniaip o----o pcip
    playerip o----o pcip
    guitarip o----o pcip
    GUITAR --> POTROCK4
    potrock_esp32_ip o---o pcip