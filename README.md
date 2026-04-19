# BitTorrent Client (Go)

A minimal BitTorrent client built from scratch in Go, implementing the core BitTorrent protocol to download files from peers over a peer-to-peer network.

## Features

- Parse `.torrent` files using Bencode
- Extract metadata (info hash, piece hashes, file info)
- Communicate with trackers to discover peers
- Establish TCP connections with peers
- Perform BitTorrent handshake protocol
- Exchange protocol messages (choke, unchoke, have, request, piece)
- Download file pieces from multiple peers concurrently
- Validate data integrity using SHA-1 hashes
- Reassemble downloaded pieces into the final file

## Architecture

- `torrentfile/` → Torrent parsing and metadata handling  
- `client/` → Peer connection and message handling  
- `peers/` → Peer discovery and parsing  
- `message/` → BitTorrent protocol messages  
- `main.go` → CLI entrypoint  

## How It Works

1. Parse `.torrent` file  
2. Contact tracker and fetch peers  
3. Connect to peers via TCP  
4. Perform handshake using infohash  
5. Exchange messages to request pieces  
6. Download and verify each piece  
7. Assemble final file  

## Usage

```bash
go run main.go <input.torrent> <output.file>
```

## Example

```bash
go run main.go debian.torrent output.iso
```

## Notes

* Implements the original BitTorrent spec (circa 2001)
* Uses a concurrent worker model for downloading pieces
* Includes pipelining for performance optimization

## License

Educational project — free to use and modify.
