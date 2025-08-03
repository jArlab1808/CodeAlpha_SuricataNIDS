# Suricata Setup Guide on Kali

## 1. Install Suricata
```bash
sudo apt update
sudo apt install suricata -y
```

## 2. Identify Network Interface
```bash
ip a
```

## 3. Edit /etc/suricata/suricata.yaml
Set `HOME_NET`:
```yaml
HOME_NET: "[192.168.191.0/24]"
```

Set af-packet:
```yaml
af-packet:
  - interface: eth0
    cluster-id: 99
    cluster-type: cluster_flow
    defrag: yes
```

## 4. Test Config
```bash
sudo suricata -T -c /etc/suricata/suricata.yaml -v
```

## 5. Start Suricata
```bash
sudo suricata -c /etc/suricata/suricata.yaml -i eth0
```

## 6. Monitor Logs
```bash
sudo tail -f /var/log/suricata/fast.log
```
