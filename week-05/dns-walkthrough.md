# DNS Walkthrough — What Happens When You Visit a Website

## What is DNS?

DNS stands for **Domain Name System**. Think of it as the internet's phonebook.

When you type a website address like `millyanne93-portfolio.netlify.app` into your browser, your computer needs to find its IP address; a series of numbers like `192.0.2.1` that computers use to find each other. DNS is the service that translates the human-readable name into the machine-readable IP address.

## What is a DNS Record?

A **DNS record** is a single instruction stored on a server called a **nameserver**. It tells the system how to answer when someone asks about a specific domain name. Different types of records do different things: some point directly to an IP address, some point to other names, and others handle mail or security.

## What is a CNAME Record?

**CNAME** stands for **Canonical Name**. It's a type of DNS record that lets one domain name act as an alias for another domain name.

Instead of pointing a domain name directly to an IP address, a CNAME points it to another domain name.

For example, my portfolio site uses a Netlify URL: `millyanne93-portfolio.netlify.app`. If I owned a custom domain like `millyanne.dev`, I could set up a CNAME record that points it to my Netlify URL. This way, someone visiting `millyanne.dev` would be directed to the same place as `millyanne93-portfolio.netlify.app`.

## How DNS Resolution Actually Works

Here's what happens when someone types a website address into their browser:

1. **The Resolver** — Your computer asks a DNS resolver (usually provided by your internet provider) for the IP address of the domain you typed.

2. **The Nameserver** — The resolver doesn't store this information itself. It asks an **authoritative nameserver** — the official source of truth for that domain — for the answer.

3. **The Record** — The nameserver looks up the DNS record for that domain. If it finds a CNAME record, it responds with the alias.

4. **The Repeat** — The resolver then repeats the lookup for that new alias, following the chain until it reaches a record that points directly to an IP address.

5. **The Final IP** — Once the resolver gets a real IP address, it sends that back to the browser, which then uses it to connect to the website's server.

**All of this happens before any HTTP request is sent.** By the time the browser connects to the server, the DNS resolution has already finished, and the CNAME is no longer visible.

## Why This Matters for My Portfolio

Netlify servers don't have a fixed IP address, they can change. Instead of pointing to an IP that might change, my site uses a stable Netlify URL. If I ever want to use a custom domain, I'll set up a CNAME record to point it to my Netlify URL, and DNS will handle the rest.
