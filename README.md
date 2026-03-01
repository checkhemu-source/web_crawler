# Web Crawler Tool (WCT) v2.0

> **Module:** ST4017CMD — Introduction to Programming  
> **Student:** Shishir Ghimire (240732)  
> **College:** Softwarica College of IT & E-Commerce  
> **Lecturer:** Er. Suman Shrestha

---

## Overview

The **Web Crawler Tool (WCT)** is a Python-based cybersecurity reconnaissance framework developed as an academic project for the Introduction to Programming module. It performs automated web asset discovery using a Breadth-First Search (BFS) algorithm, powered entirely by **custom-built data structures** — a Linked-List Queue and a Chained Hash Table — replacing Python's built-in equivalents.

## Features

### Web Crawler Core
| Feature | Description |
|---------|-------------|
| **BFS Web Crawling** | Systematic depth-limited URL discovery across target domains |
| **Email Extraction** | Regex-based email address interception from HTML content |
| **Form Detection** | Identifies HTML forms (SQL injection/XSS attack surfaces) |
| **Server Fingerprinting** | Extracts server technology from HTTP response headers |
| **Rich CLI Interface** | Real-time live scanning table with colour-coded output |

### Cybersecurity Toolkit (NEW)
| Tool | Description |
|------|-------------|
| **Password Generator** | Secure password generation with customizable length |
| **Message Crypto** | Base64 message encryption and decryption |
| **Port Scanner** | Basic TCP port scanner for footprinting targets |
| **Network Mapper** | Ping-sweep subnet discovery for local network mapping |
| **Password Manager** | Credential vault using local JSON storage and basic encoding |
| **Brute Forcer** | Educational simulated dictionary attack sequence |
| **Keylogger** | Educational concept implementation prototype |

### Technical Capabilities
| Feature | Description |
|---------|-------------|
| **Custom Queue** | Singly Linked List FIFO queue (O(1) enqueue/dequeue) |
| **Custom Hash Table** | Polynomial rolling hash with chaining (O(1) avg lookup) |
| **Interactive Menu** | Full interactive CLI with data structure info and about screens |
| **Ethical Compliance** | Custom User-Agent header, rate limiting, and domain restriction |

## Installation

```bash
# Clone the repository
git clone <repository-url>
cd programing

# Install dependencies
pip install -r requirements.txt
```

## Usage

### Interactive Mode (Menu-driven)
```bash
python web_crawler.py
```

### Command-Line Mode
```bash
python web_crawler.py <target_url> -d <depth> -m <max_urls>

# Example: Scan testphp.vulnweb.com with depth 2 and max 30 URLs
python web_crawler.py http://testphp.vulnweb.com -d 2 -m 30
```

### CLI Arguments
| Argument | Description | Default |
|----------|-------------|---------|
| `url` | Target URL (omit for interactive mode) | — |
| `-d`, `--depth` | Maximum crawl depth | 2 |
| `-m`, `--max` | Maximum URLs to scan | 50 |
| `-h`, `--help` | Show help message | — |

## Project Structure

```
programing/
├── web_crawler.py          # Main tool source code
├── test_web_crawler.py     # Unit test suite (23 tests)
├── generate_assignment.py  # Assignment document generator
├── requirements.txt        # Python dependencies
├── README.md               # This file
└── Web_Crawler_Assignment.docx  # Generated assignment document
```

## Custom Data Structures

### CustomQueue (Singly Linked List)
- **Purpose:** BFS frontier — manages URL processing order
- **Operations:** `enqueue()` O(1), `dequeue()` O(1), `is_empty()` O(1), `size()` O(1)
- **Replaces:** `collections.deque`

### CustomHashTable (Chaining)
- **Purpose:** Visited URL tracking — prevents cycle revisits
- **Operations:** `add()` O(1) avg, `contains()` O(1) avg, `to_list()` O(n)
- **Hash Function:** Polynomial rolling hash with prime multiplier 31
- **Capacity:** 2048 buckets with collision chaining
- **Replaces:** Python built-in `set()`

### CrawlNode (Data Object)
- **Purpose:** Stores URL metadata — url, depth, HTTP status, title, emails, forms, tech

## Testing

```bash
# Run all 23 unit tests
python test_web_crawler.py
```

Test classes:
- `TestListNode` — Node creation and linking
- `TestCustomQueue` — Enqueue, dequeue, FIFO order, empty handling, size tracking
- `TestCustomHashTable` — Hash consistency, range, add/contains, collisions, to_list
- `TestCrawlNode` — Default initialisation and mutability
- `TestIntegration` — Queue + CrawlNode, HashTable + URL strings

## Ethical Disclaimer

This tool is developed **solely for authorised security assessments and academic purposes**. All testing was conducted against:
- Locally hosted test servers
- **testphp.vulnweb.com** — Acunetix's authorised vulnerable test application

Unauthorised use of this tool against systems without explicit permission is **illegal** under the Computer Misuse Act 1990 and equivalent legislation.

## Technologies Used

- **Python 3.12** — Core language
- **requests** — HTTP session management
- **BeautifulSoup4** + **lxml** — HTML parsing
- **Rich** — Terminal UI (tables, panels, live display)
- **argparse** — Command-line argument parsing
- **re** — Regular expression email extraction

## License

Academic project — Softwarica College of IT & E-Commerce © 2025
