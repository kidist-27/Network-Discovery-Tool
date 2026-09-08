# Network-Discovery-Tool
 Python CLI tool that takes a target subnet, scans every live IP in it, and checks each one for common open TCP ports (21, 22, 80, 139, 443, 445, 1433, 3306, 3389, 8080) — mapping out what's actually reachable and exposed on a local network.
# Network Discovery Tool

A Python CLI tool that takes a target subnet, scans every live IP in it, and checks each one for common open TCP ports — mapping out what's actually reachable and exposed on a local network.

## How it works

- Uses `ipaddress` to parse the subnet and iterate through every IP in the range
- Uses `socket.connect_ex()` with `socket.setdefaulttimeout()` to test each port — a return value of `0` means the port is open
- Checks these ports on each live host: `21, 22, 80, 139, 443, 445, 1433, 3306, 3389, 8080`
- Built entirely with Python's standard library — `socket`, `ipaddress`, `argparse` — no external dependencies

## Usage

```bash
python3 file_name.py <subnet>
```

Example:
```bash
python3 file_name.py 192.168.1.0/24
```

## Why I built this

To understand how basic network reconnaissance tools like Nmap work under the hood — subnet iteration and TCP connect scanning from first principles, instead of relying on an existing library.

> ⚠️ For use only on networks you own or have explicit permission to scan.
