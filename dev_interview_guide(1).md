# Application Developer Interview Study Guide

## Programming Fundamentals

### Object-Oriented vs Functional Programming

**Object-Oriented Programming (OOP):**
- Organizes code around objects that contain data (attributes) and methods
- Key principles: Encapsulation, Inheritance, Polymorphism, Abstraction
- Example: A `Car` class with properties like `color`, `model` and methods like `start()`, `stop()`

**Functional Programming:**
- Organizes code around functions and avoids changing state
- Emphasizes immutability and pure functions (same input always produces same output)
- Example: Using `map()`, `filter()`, `reduce()` to transform data without modifying original arrays

```javascript
// OOP approach
class Calculator {
  add(a, b) { return a + b; }
  multiply(a, b) { return a * b; }
}

// Functional approach
const add = (a, b) => a + b;
const multiply = (a, b) => a * b;
```

### Design Patterns

**Singleton Pattern:**
- Ensures only one instance of a class exists
- Use case: Database connections, logging services

```javascript
class Database {
  constructor() {
    if (Database.instance) {
      return Database.instance;
    }
    Database.instance = this;
  }
}
```

**Factory Pattern:**
- Creates objects without specifying exact classes
- Use case: Creating different types of users (Admin, Regular, Guest)

**Observer Pattern:**
- Allows objects to notify multiple other objects about state changes
- Use case: Event handling, model-view architectures

### Memory Management

**Automatic (Garbage Collected):** JavaScript, Python, Java
- Runtime automatically frees unused memory
- Developer focuses on logic, not manual memory management

**Manual:** C, C++
- Developer explicitly allocates and frees memory
- More control but higher risk of memory leaks

**Stack vs Heap:**
- Stack: Stores local variables, function calls (automatic cleanup)
- Heap: Stores dynamically allocated objects (needs garbage collection)

### Synchronous vs Asynchronous Programming

**Synchronous:**
- Code executes line by line, waiting for each operation to complete
- Blocking - if one operation is slow, everything waits

**Asynchronous:**
- Operations can run concurrently without blocking
- Non-blocking - slow operations don't halt other code

```javascript
// Synchronous
console.log("First");
console.log("Second");
console.log("Third");

// Asynchronous
console.log("First");
setTimeout(() => console.log("Second"), 1000);
console.log("Third"); // Runs immediately, doesn't wait
```

### Data Structures

**Arrays:**
- Fixed or dynamic size, indexed access
- Use when: You need fast random access by index
- Time complexity: Access O(1), Search O(n)

**Linked Lists:**
- Elements connected via pointers
- Use when: Frequent insertions/deletions, size varies greatly
- Time complexity: Access O(n), Insert/Delete O(1) if you have the node

**Hash Tables (Objects/Maps):**
- Key-value pairs with fast lookup
- Use when: You need fast lookup by key
- Time complexity: Access/Insert/Delete O(1) average case

## Problem-Solving & Algorithms

### String Reversal
```javascript
function reverseString(str) {
  return str.split('').reverse().join('');
}

// Or manual approach
function reverseManual(str) {
  let result = '';
  for (let i = str.length - 1; i >= 0; i--) {
    result += str[i];
  }
  return result;
}
```

### Binary Search
```javascript
function binarySearch(arr, target) {
  let left = 0;
  let right = arr.length - 1;
  
  while (left <= right) {
    let mid = Math.floor((left + right) / 2);
    
    if (arr[mid] === target) return mid;
    if (arr[mid] < target) left = mid + 1;
    else right = mid - 1;
  }
  return -1; // Not found
}
```

### Maximum Element
```javascript
function findMax(arr) {
  if (arr.length === 0) return null;
  
  let max = arr[0];
  for (let i = 1; i < arr.length; i++) {
    if (arr[i] > max) {
      max = arr[i];
    }
  }
  return max;
}

// Or using built-in method
function findMaxBuiltIn(arr) {
  return Math.max(...arr);
}
```

### FizzBuzz
```javascript
function fizzBuzz(n) {
  for (let i = 1; i <= n; i++) {
    if (i % 15 === 0) console.log("FizzBuzz");
    else if (i % 3 === 0) console.log("Fizz");
    else if (i % 5 === 0) console.log("Buzz");
    else console.log(i);
  }
}
```

### Palindrome Check
```javascript
function isPalindrome(str) {
  const cleaned = str.toLowerCase().replace(/[^a-z0-9]/g, '');
  return cleaned === cleaned.split('').reverse().join('');
}

// Two-pointer approach (more efficient)
function isPalindromeOptimal(str) {
  const cleaned = str.toLowerCase().replace(/[^a-z0-9]/g, '');
  let left = 0;
  let right = cleaned.length - 1;
  
  while (left < right) {
    if (cleaned[left] !== cleaned[right]) return false;
    left++;
    right--;
  }
  return true;
}
```

### Big O Notation

**Common Time Complexities:**
- O(1): Constant - accessing array element
- O(log n): Logarithmic - binary search
- O(n): Linear - searching unsorted array
- O(n log n): Log-linear - efficient sorting (merge sort)
- O(n²): Quadratic - nested loops
- O(2^n): Exponential - recursive fibonacci (naive)

**Space Complexity:** How much extra memory an algorithm uses

## Database Knowledge

### SQL Queries

**Basic SELECT:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```

**JOIN Examples:**
```sql
-- Inner Join (only matching records)
SELECT users.name, orders.total
FROM users
INNER JOIN orders ON users.id = orders.user_id;

-- Left Join (all users, even without orders)
SELECT users.name, orders.total
FROM users
LEFT JOIN orders ON users.id = orders.user_id;
```

**GROUP BY with aggregation:**
```sql
SELECT department, COUNT(*), AVG(salary)
FROM employees
GROUP BY department
HAVING AVG(salary) > 50000;
```

**Subqueries:**
```sql
SELECT name FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```

### SQL vs NoSQL

**SQL Databases (Relational):**
- Structured data with predefined schema
- ACID properties (Atomicity, Consistency, Isolation, Durability)
- Examples: PostgreSQL, MySQL, SQL Server
- Use when: Complex relationships, transactions critical

**NoSQL Databases:**
- Flexible schema, various data models
- Better horizontal scaling
- Examples: MongoDB (document), Redis (key-value), Neo4j (graph)
- Use when: Rapid development, massive scale, varied data types

### Database Normalization

**Purpose:** Reduce data redundancy and improve integrity

**1st Normal Form (1NF):**
- Eliminate repeating groups
- Each cell contains single value

**2nd Normal Form (2NF):**
- 1NF + eliminate partial dependencies
- Non-key attributes depend on entire primary key

**3rd Normal Form (3NF):**
- 2NF + eliminate transitive dependencies
- Non-key attributes don't depend on other non-key attributes

### Query Optimization

**Common techniques:**
- Add indexes on frequently queried columns
- Avoid SELECT * (specify needed columns)
- Use LIMIT for large result sets
- Optimize WHERE clauses (put most selective conditions first)
- Use EXPLAIN to analyze query execution plans

### ACID Properties

**Atomicity:** Transaction is all-or-nothing
**Consistency:** Database remains in valid state
**Isolation:** Concurrent transactions don't interfere
**Durability:** Committed transactions persist even after system failure

## Web Development

### HTTP Methods

**GET:**
- Retrieve data from server
- Idempotent (safe to repeat)
- Data in URL parameters
- Cacheable

**POST:**
- Send data to server to create/update resources
- Not idempotent
- Data in request body
- Not cacheable by default

**Other methods:** PUT (update), DELETE (remove), PATCH (partial update)

### HTTP Status Codes

**2xx Success:**
- 200 OK
- 201 Created
- 204 No Content

**4xx Client Error:**
- 400 Bad Request
- 401 Unauthorized
- 404 Not Found
- 403 Forbidden

**5xx Server Error:**
- 500 Internal Server Error
- 502 Bad Gateway
- 503 Service Unavailable

### REST API Design

**Principles:**
- Use HTTP methods appropriately
- Resource-based URLs (/users/123, not /getUser?id=123)
- Stateless (each request contains all needed info)
- Use proper status codes
- Consistent naming conventions

**Example REST endpoints:**
```
GET /users          # Get all users
GET /users/123      # Get specific user
POST /users         # Create new user
PUT /users/123      # Update entire user
PATCH /users/123    # Partial update
DELETE /users/123   # Delete user
```

### Authentication vs Authorization

**Authentication:** Verifying identity ("Who are you?")
- Methods: passwords, tokens, biometrics, OAuth

**Authorization:** Verifying permissions ("What can you do?")
- Methods: role-based access control (RBAC), permissions

### Client-Side vs Server-Side Rendering

**Client-Side Rendering (CSR):**
- JavaScript builds page in browser
- Initial load: empty HTML + JS bundle
- Pros: Interactive, reduced server load
- Cons: Slower initial load, SEO challenges

**Server-Side Rendering (SSR):**
- Server generates complete HTML
- Initial load: fully rendered page
- Pros: Faster initial load, better SEO
- Cons: More server resources, less interactive

### Storage Options

**Cookies:**
- Sent with every request
- 4KB limit
- Can be httpOnly (secure)
- Use for: authentication tokens

**Local Storage:**
- 5-10MB limit
- Persists until manually cleared
- Use for: user preferences, offline data

**Session Storage:**
- Same as localStorage but clears when tab closes
- Use for: temporary data within session

## Framework/Technology Specific

### State Management

**React - useState:**
```jsx
const [count, setCount] = useState(0);
const increment = () => setCount(count + 1);
```

**Global State (Redux, Context):**
- Centralized state for entire application
- Use when: Multiple components need same data

### Dependency Injection

**Concept:** Providing dependencies from outside rather than creating them internally

**Benefits:**
- Easier testing (can inject mocks)
- Loose coupling
- Better maintainability

```javascript
// Without DI
class UserService {
  constructor() {
    this.db = new Database(); // Tight coupling
  }
}

// With DI
class UserService {
  constructor(database) {
    this.db = database; // Dependency injected
  }
}
```

### Error Handling

**Try-Catch blocks:**
```javascript
try {
  const result = riskyOperation();
  return result;
} catch (error) {
  console.error('Operation failed:', error.message);
  throw new Error('User-friendly message');
} finally {
  // Cleanup code
}
```

**Async error handling:**
```javascript
async function fetchData() {
  try {
    const response = await fetch('/api/data');
    if (!response.ok) throw new Error('Network error');
    return await response.json();
  } catch (error) {
    console.error('Fetch failed:', error);
    return null;
  }
}
```

### Testing

**Unit Tests:** Test individual components/functions
**Integration Tests:** Test multiple components working together
**End-to-End Tests:** Test complete user workflows

**Example with Jest:**
```javascript
describe('Calculator', () => {
  test('should add two numbers correctly', () => {
    expect(add(2, 3)).toBe(5);
  });
  
  test('should handle edge cases', () => {
    expect(add(0, 0)).toBe(0);
    expect(add(-1, 1)).toBe(0);
  });
});
```

## System Design & Architecture

### Simple Web Application Design

**Components:**
1. **Frontend:** User interface (React, Angular, Vue)
2. **Backend API:** Business logic, data processing
3. **Database:** Data persistence
4. **Authentication:** User management
5. **Caching:** Improve performance (Redis)
6. **CDN:** Static asset delivery

**Basic Architecture:**
```
User → Load Balancer → Web Servers → Application Servers → Database
                    ↓
                Cache Layer
```

### Microservices vs Monolithic

**Monolithic:**
- Single deployable unit
- Shared database
- Pros: Simpler development/deployment, better performance
- Cons: Scaling challenges, technology lock-in

**Microservices:**
- Multiple independent services
- Service-specific databases
- Pros: Independent scaling, technology diversity, fault isolation
- Cons: Complexity, network overhead, data consistency challenges

### Application Security

**Common Threats & Mitigations:**

**SQL Injection:** Use parameterized queries
**XSS (Cross-Site Scripting):** Sanitize user input, use CSP headers
**CSRF (Cross-Site Request Forgery):** Use CSRF tokens
**Authentication:** Strong passwords, 2FA, secure session management
**HTTPS:** Encrypt data in transit
**Input Validation:** Validate and sanitize all user input

### Scaling Applications

**Vertical Scaling (Scale Up):**
- Add more power to existing machines
- Easier but has limits

**Horizontal Scaling (Scale Out):**
- Add more machines
- More complex but unlimited potential

**Strategies:**
- Load balancing across multiple servers
- Database replication and sharding
- Caching frequently accessed data
- CDN for static assets
- Microservices for independent scaling

### Caching

**Types:**
- **Browser Cache:** Static assets cached locally
- **CDN Cache:** Geographically distributed caching
- **Application Cache:** In-memory data (Redis, Memcached)
- **Database Cache:** Query result caching

**When to Use:**
- Frequently accessed data
- Expensive computations
- Database query results
- API responses

**Cache Strategies:**
- **Cache-Aside:** Application manages cache
- **Write-Through:** Write to cache and database simultaneously
- **Write-Behind:** Write to cache first, database later

## Practical Coding Tips

### Live Coding Best Practices

1. **Think Out Loud:** Explain your approach before coding
2. **Start Simple:** Get basic solution working first
3. **Test with Examples:** Walk through your code with sample inputs
4. **Consider Edge Cases:** Empty inputs, null values, boundary conditions
5. **Optimize if Asked:** Discuss time/space complexity improvements

### Code Review Skills

**What to Look For:**
- Logic errors and bugs
- Code readability and maintainability
- Performance issues
- Security vulnerabilities
- Adherence to coding standards
- Test coverage

### Debugging Approach

1. **Reproduce the Issue:** Understand exact conditions
2. **Isolate the Problem:** Use debugging tools, logs
3. **Form Hypothesis:** What might be causing it?
4. **Test Hypothesis:** Add logging, use debugger
5. **Fix and Verify:** Implement solution and test thoroughly

## Interview Preparation Tips

1. **Practice Coding:** Use platforms like LeetCode, HackerRank
2. **Understand Fundamentals:** Don't just memorize, understand concepts
3. **Build Projects:** Have examples of your work to discuss
4. **Study the Company:** Know their tech stack and values
5. **Prepare Questions:** Ask about team structure, development process, challenges
6. **Mock Interviews:** Practice with friends or use online platforms

## Networking Fundamentals

### HTTP Protocol Deep Dive

**HTTP (HyperText Transfer Protocol):**
- Application layer protocol for web communication
- Stateless protocol (each request is independent)
- Client-server architecture

**HTTP Request Structure:**
```
GET /api/users HTTP/1.1
Host: example.com
User-Agent: Mozilla/5.0
Accept: application/json
Authorization: Bearer token123
Content-Type: application/json

{request body for POST/PUT}
```

**HTTP Response Structure:**
```
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 1234
Cache-Control: max-age=3600
Set-Cookie: sessionId=abc123

{response body}
```

**HTTP Versions:**
- **HTTP/1.1:** Persistent connections, pipelining
- **HTTP/2:** Multiplexing, server push, binary protocol
- **HTTP/3:** Uses QUIC, improved performance over unreliable networks

### TCP/IP Fundamentals

**TCP (Transmission Control Protocol):**
- Reliable, connection-oriented protocol
- Guarantees delivery and order
- Three-way handshake: SYN → SYN-ACK → ACK
- Use cases: Web browsing, email, file transfer

**UDP (User Datagram Protocol):**
- Unreliable, connectionless protocol
- Faster but no delivery guarantee
- Use cases: Video streaming, gaming, DNS lookups

**IP (Internet Protocol):**
- Routes packets between networks
- IPv4: 32-bit addresses (192.168.1.1)
- IPv6: 128-bit addresses (2001:db8::1)

### OSI Model (7 Layers)

**7. Application Layer:** HTTP, FTP, SMTP, DNS
**6. Presentation Layer:** Encryption, compression, data formatting
**5. Session Layer:** Session management, authentication
**4. Transport Layer:** TCP, UDP - end-to-end delivery
**3. Network Layer:** IP routing, packet forwarding
**2. Data Link Layer:** Ethernet, Wi-Fi - local network communication
**1. Physical Layer:** Cables, radio waves, electrical signals

**TCP/IP Model (4 Layers):**
**4. Application:** Combines OSI layers 5-7
**3. Transport:** TCP/UDP
**2. Internet:** IP
**1. Network Interface:** Physical + Data Link

### DNS (Domain Name System)

**Purpose:** Translates domain names to IP addresses

**DNS Hierarchy:**
```
Root (.) → Top-level domain (.com) → Domain (example.com) → Subdomain (api.example.com)
```

**DNS Record Types:**
- **A Record:** Maps domain to IPv4 address
- **AAAA Record:** Maps domain to IPv6 address
- **CNAME:** Canonical name (alias for another domain)
- **MX:** Mail exchange servers
- **TXT:** Text records (often for verification)
- **NS:** Name server records

**DNS Resolution Process:**
1. Browser cache check
2. OS cache check
3. Router cache check
4. ISP DNS server
5. Root name server
6. TLD name server
7. Authoritative name server

### Network Security

**HTTPS (HTTP Secure):**
- HTTP over TLS/SSL encryption
- Protects data in transit
- Certificate validation ensures server identity

**TLS/SSL Handshake:**
1. Client Hello (supported cipher suites)
2. Server Hello (chosen cipher, certificate)
3. Certificate verification
4. Key exchange
5. Encrypted communication begins

**Common Security Headers:**
```
Strict-Transport-Security: max-age=31536000
Content-Security-Policy: default-src 'self'
X-Frame-Options: DENY
X-Content-Type-Options: nosniff
```

**Firewalls:**
- Packet filtering (IP, port, protocol)
- Stateful inspection (connection tracking)
- Application layer filtering (deep packet inspection)

### Load Balancing

**Purpose:** Distribute traffic across multiple servers

**Load Balancing Algorithms:**
- **Round Robin:** Requests distributed sequentially
- **Least Connections:** Route to server with fewest active connections
- **Weighted Round Robin:** Servers get different weights
- **IP Hash:** Route based on client IP hash
- **Least Response Time:** Route to fastest responding server

**Types:**
- **Layer 4 (Transport):** Routes based on IP and port
- **Layer 7 (Application):** Routes based on HTTP content

**Health Checks:** Monitor server availability and performance

### Content Delivery Networks (CDNs)

**Purpose:** Deliver content from geographically distributed servers

**Benefits:**
- Reduced latency (content closer to users)
- Reduced bandwidth costs
- Improved availability and redundancy
- DDoS mitigation

**How CDNs Work:**
1. User requests content
2. CDN determines closest edge server
3. If content cached: serve from edge
4. If not cached: fetch from origin, cache, serve

**CDN Strategies:**
- **Push:** Upload content to CDN manually
- **Pull:** CDN fetches content on first request

### WebSockets

**Purpose:** Real-time, bidirectional communication

**Differences from HTTP:**
- Persistent connection (not request-response)
- Both client and server can initiate communication
- Lower overhead after connection established

**WebSocket Handshake:**
```
GET /websocket HTTP/1.1
Upgrade: websocket
Connection: Upgrade
Sec-WebSocket-Key: dGhlIHNhbXBsZSBub25jZQ==

HTTP/1.1 101 Switching Protocols
Upgrade: websocket
Connection: Upgrade
```

**Use Cases:**
- Live chat applications
- Real-time gaming
- Live sports scores
- Collaborative editing
- Financial trading platforms

### API Communication Patterns

**REST (Representational State Transfer):**
- Stateless communication
- Resource-based URLs
- HTTP methods for operations
- JSON/XML data format

**GraphQL:**
- Single endpoint
- Client specifies exactly what data needed
- Strongly typed schema
- Reduces over-fetching

**gRPC:**
- High-performance RPC framework
- Protocol Buffer serialization
- HTTP/2 transport
- Bidirectional streaming

**Message Queues:**
- Asynchronous communication
- Decouples services
- Examples: RabbitMQ, Apache Kafka, AWS SQS

### Network Performance Optimization

**Latency vs Bandwidth:**
- **Latency:** Time for single packet to travel
- **Bandwidth:** Amount of data transferred per second
- **Round Trip Time (RTT):** Time for request and response

**Optimization Techniques:**
- **Connection Pooling:** Reuse TCP connections
- **HTTP/2 Multiplexing:** Multiple requests per connection
- **Compression:** Gzip, Brotli for text content
- **Minification:** Remove unnecessary characters from code
- **Image Optimization:** WebP, responsive images, lazy loading

**Caching Headers:**
```
Cache-Control: public, max-age=3600    # Cache for 1 hour
ETag: "abc123"                         # Version identifier
Last-Modified: Wed, 21 Oct 2023 07:28:00 GMT
```

### Network Troubleshooting

**Common Tools:**

**ping:** Test connectivity and measure latency
```bash
ping google.com
```

**traceroute/tracert:** Show network path to destination
```bash
traceroute google.com
```

**nslookup/dig:** DNS lookup tools
```bash
nslookup example.com
dig example.com A
```

**netstat:** Show network connections
```bash
netstat -an
```

**curl:** Test HTTP requests
```bash
curl -H "Accept: application/json" https://api.example.com/users
```

**Browser Developer Tools:**
- Network tab: Inspect HTTP requests/responses
- Performance tab: Analyze loading times
- Security tab: Check certificate details

### Common Network Issues

**Connection Timeout:**
- Server not responding
- Firewall blocking connection
- Network congestion

**DNS Resolution Failure:**
- Incorrect DNS configuration
- DNS server down
- Domain not registered

**SSL/TLS Errors:**
- Certificate expired or invalid
- Hostname mismatch
- Unsupported cipher suites

**High Latency:**
- Geographic distance
- Network congestion
- Inefficient routing

### Monitoring and Metrics

**Key Network Metrics:**
- **Response Time:** How long requests take
- **Throughput:** Requests per second
- **Error Rate:** Percentage of failed requests
- **Availability:** Uptime percentage

**Monitoring Tools:**
- Application Performance Monitoring (APM)
- Network monitoring tools
- Log aggregation systems
- Real User Monitoring (RUM)

### Interview Questions on Networking

**Common Questions:**

1. **"Explain what happens when you type a URL in the browser"**
   - DNS resolution
   - TCP connection establishment
   - HTTP request/response
   - HTML parsing and rendering

2. **"How would you troubleshoot a slow website?"**
   - Check network connectivity
   - Analyze browser developer tools
   - Test from different locations
   - Check server performance
   - Review database queries

3. **"What's the difference between TCP and UDP?"**
   - Reliability vs speed
   - Connection-oriented vs connectionless
   - Use cases for each

4. **"How does HTTPS work?"**
   - TLS/SSL encryption
   - Certificate validation
   - Handshake process

5. **"Explain how a CDN improves performance"**
   - Geographic distribution
   - Edge caching
   - Reduced latency

**Advanced Topics:**
- Network protocols (MQTT, WebRTC)
- Service mesh architecture
- API gateways
- Network security (VPNs, zero trust)
- IPv6 adoption challenges

Remember: Interviews test both technical knowledge and problem-solving approach. Show your thinking process, ask clarifying questions, and don't be afraid to say "I don't know, but here's how I'd find out."