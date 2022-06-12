## DNS



##### nslookup

`nslookup` tool allows the host running the tool to query any specified DNS server for a DNS record. 

​	The queried DNS server can be a root DNS server, a top-level-domain DNS server, an authoritative DNS server, or an intermediate DNS server

##### Basic knowledge

All DNS servers fall into one of four categories: 

​	Recursive resolvers

​	Root nameservers

​	TLD nameservers

​	authortative nameservers

In a typical DNS lookup (when there is no [caching](https://www.cloudflare.com/learning/cdn/what-is-caching/) in play), these four DNS servers work together in harmony to complete the task of delivering the [IP address](https://www.cloudflare.com/learning/dns/glossary/what-is-my-ip-address/) for a specified [domain](https://www.cloudflare.com/learning/dns/glossary/what-is-a-domain-name/) to the client 

**recursive resolver**

A recursive resolver (also known as a DNS recursor) is the first stop in a DNS query. The recursive resolver acts as a middleman between a client and a DNS nameserver. After receiving a DNS query from a web client, a recursive resolver will either respond with cached data, or send a request to a root nameserver, followed by another request to a TLD nameserver, and then one last request to an authoritative nameserver. 

After receiving a response from the authoritative name server containing the requested IP address, the recursive resolver then sends a response to the client.

During this process, the recursive resolver will cache information received from authoritative name servers. When a client requests the IP address of a domain name that was recently requested by another client, the resolver can circumvent the process of communicating with the nameservers, and just deliver the client the requested record from its cache.

Most internet users use a recursive resolver provided by their ISP, but there are other options available;



**What is a DNS root name server**

The 13 DNS root nameservers are known to every recursive resolver, and they are the first stop in a recursive resolver’s quest for DNS records. A root server accepts a recursive resolver’s query which includes a domain name, and the root nameserver responds by directing the recursive resolver to a TLD nameserver, based on the extension of that domain (.com, .net, .org, etc.). The root nameservers are overseen by a nonprofit called the Internet Corporation for Assigned Names and Numbers (ICANN).

Note that while there are 13 root nameservers, that doesn’t mean that there are only 13 machines in the root nameserver system. There are 13 types of root nameservers, but there are multiple copies of each one all over the world, which use [Anycast routing](https://www.cloudflare.com/learning/cdn/glossary/anycast-network/) to provide speedy responses. If you added up all the instances of root nameservers, you’d have 632 different servers (as of October 2016).



**What is a TLD nameserver**

A TLD nameserver maintains information for all the domain names that share a common domain extension, such as .com, .net, or whatever comes after the last dot in a url. For example, a .com TLD nameserver contains information for every website that ends in ‘.com’. If a user was searching for google.com, after receiving a response from a root nameserver, the recursive resolver would then send a query to a .com TLD nameserver, which would respond by pointing to the authoritative nameserver (see below) for that domain.

Management of TLD nameservers is handled by the Internet Assigned Numbers Authority (IANA), which is a branch of ICANN. The IANA breaks up the TLD servers into two main groups:

- Generic top-level domains: These are domains that are not country specific, some of the best-known generic TLDs include .com, .org, .net, .edu, and .gov.
- Country code top-level domains: These include any domains that are specific to a country or state. Examples include .uk, .us, .ru, and .jp.

There is actually a third category for infrastructure domains, but it is almost never used. This category was created for the .arpa domain, which was a transitional domain used in the creation of modern DNS; its significance today is mostly historical.



**What is an authoritative nameserver**

When a recursive resolver receives a response from a TLD nameserver, that response will direct the resolver to an authoritative nameserver. The authoritative nameserver is usually the resolver’s last step in the journey for an IP address. The authoritative nameserver contains information specific to the domain name it serves (e.g. google.com) and it can provide a recursive resolver with the IP address of that server found in the [DNS A record](https://www.cloudflare.com/learning/dns/dns-records/dns-a-record/), or if the domain has a [CNAME record](https://www.cloudflare.com/learning/dns/dns-records/dns-cname-record/) (alias) it will provide the recursive resolver with an alias domain, at which point the recursive resolver will have to perform a whole new DNS lookup to procure a record from an authoritative nameserver (often an A record containing an IP address). [Cloudflare DNS](https://www.cloudflare.com/dns/) distributes authoritative nameservers, which come with Anycast routing to make them more reliable.



##### Workflow

DNS resolver (designed to receive DNS queries from web browsers and other applications): it receives a hostname and is responsible for tracking down the IP address for that hostname

​	The DNS resolver might be operated by the local network, an Internet Service Provider (IP), a mobile carrier, a WIFI network, or other third party. The resolver starts by looking in its local cache or that of the operating system on the local device - if the hostname is found, it is resolved immediately.

​	If not found, the resolver contacts a **DNS Root Server** and receives details of a **TLD Name Server**. Via the TLD Name Server, it receives details of an **Authoritative Name Server**, and asks it for the IP that matches the requested hostname. When it receives the IP, the query is resolved.

**DNS Root Server**

The root server is the first step in translating human readable host names into IP addresses. The Top Level Domain (TLD) takes the TLD provided in the user’s query. for example, [www.example.**com**](http://www.example.com/) - and provides details for the **.com** TLD Name Server.

**TLD Name Server**

The TLD Name Server takes the domain name provided in the query - for example [www.example.com](http://www.example.com/) - and provides the IP of an Authoritative Name Server. This is a DNS server that contains DNS records for the specific domain.



**Authoritative Name Server**

The Authoritative Name Server is the last stop in the name server query. The Authoritative Name Server takes the domain name and subdomain, and if it has access to the DNS records, it returns the correct IP address to the DNS Resolver.

​	As the Internet grows, the original IP address standard, IPv4 (which only allowed up to 4.3 billion IP addresses) is being replaced with IPv6 (which supports as many as 3.4×10^38 IP addresses). Increasingly, DNS servers return IPs using the IPv6 format.



- **Browser DNS caching** - modern web browsers are designed to cache DNS records. This enables providing an IP address immediately in response to a user request, without needing to contact external DNS servers. When a request is made for a DNS record, the browser cache is the first location checked for the requested record.
- **Operating system DNS caching** - all operating systems come with DNS resolvers, called “stub resolvers”, which are the second place a DNS query can be resolved before it leaves the local device. When a request is made by an application, the stub resolver checks its own cache to see if it has the record. If it does not, it sends a DNS query (with a recursive flag set), to a DNS Resolver on the local network, operated the Internet service provider (ISP), etc.
- **Recursive resolver DNS caching** - as we discussed above, a DNS Resolver operated by a third part receives DNS queries, and checks its local cache to see if it already has the IP for the requested ho

**[DNS Record Types](https://ns1.com/resources/dns-types-records-servers-and-queries)**:

DNS resource records (RR) are the basic information elements of the Domain Name System. They are entries in the DNS database which provide information about hosts. The records are physically stored in the Zone Files on the DNS server.

The following are common DNS records:

- Address Mapping records (A) - records that hold a hostname and its corresponding IPv4 address.
- IP Version 6 Address records (AAAA) - records that hold a hostname and its corresponding IPv6 address.
- Canonical Name records (CNAME) - used to create aliases of domain names. Can be used to alias a domain to another domain.
- Mail exchanger record (MX) - specifies a mail exchange server for the domain name, used in the SMTP protocol to route emails to the correct email server.
- Name Server records (NS) - delegates a DNS Zone to use a specific Authoritative Name Server.
- Reverse-lookup Pointer records (PTR) - used to look up domain names based on an IP address.
- Certificate record (CERT) - stores encryption certificates such as PKIX, SPKI, PGP, etc.
- Service Location (SRV) - service location record, like MX but for other, newer protocols.



**[The DNS Protocol](https://ns1.com/resources/dns-protocol)**:

The DNS protocol uses two types of DNS messages, queries and replies. Both queries and replies consist of a header and four sections: question, answer, authority, and an additional space:

- **The header section** contains Identification, used to match responses with queries; Flags; Number of questions; Number of answers; Number of authority resource records (RRs); and Number of additional resource records.
- **The flag field** contains sections of one or four bits, indicating if the message is a query or a reply; if the present packet is a reply, a status, or a request; whether the DNS server is authoritative; whether the client wants to send a recursive query ("RD"); whether the DNS server supports recursion; whether the request was truncated ("TC"); and four bits at the end indicating status.
- **The question section** contains the domain name and type of record (A, AAAA, MX, TXT, etc.) being resolved. The domain name is broken into labels, each label prefixed by the length of that label.
- **The answer section** has the resource records of the queried name. A domain name may occur in multiple records if it has multiple IP addresses associated with it.

Protocol Transport:

​	DNS primarily uses the User Datagram Protocol (UDP) on port number 53 to serve requests. DNS queries consist of a single UDP request from the client followed by a single UDP reply from the server. The Transmission Control Protocol (TCP) is used when the response data size exceeds 512 bytes, or for zone transfers. Some DNS resolvers use TCP for all communication.

**DNS Record Format**:

Each DNS resource record is comprised of the following fields:

| **Field**                                         | **Description**                                              | **Length (**[**octets**](https://en.wikipedia.org/wiki/Octet_(computing))**)** |
| ------------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| NAME                                              | Name of the node to which this record pertains               | Variable                                                     |
| TYPE                                              | Type of RR in numeric form (e.g., 15 for MX RRs)             | 2                                                            |
| CLASS                                             | Class code                                                   | 2                                                            |
| [TTL](https://en.wikipedia.org/wiki/Time_to_live) | Count of seconds that the RR stays valid (The maximum is 231−1, which is about 68 years) | 4                                                            |
| RDLENGTH                                          | Length of RDATA field (specified in octets)                  | 2                                                            |
| RDATA                                             | Additional RR-specific data. For example, in an A record this field contains the IP address of the host. | Variable, as per RDLENGTH                                    |



. ipconfig can be used to show  your current TCP/IP information, including your address, DNS server addresses, adapter type and so on. For example, if you all this information about your host simply by entering `ifconfig \all`





```
nslookup www.mit.edu

This command is saying "please send me the IP address for the host www.mit.edu". The response from this command provides two piece of information
	1. the name and the IP address of the DNS server that provides the answer
	2. the answer itself, which is the host name and IP address of www.mit.edu
```



Locate the DNS query and response messages. Are then sent over UDP or TCP? ANSWER: They are sent over UDP







