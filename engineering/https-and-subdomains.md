# 🌐 HTTPS & Subdomains

Since we’re going to start using cross-subdomain authentication it’s pretty important that we can test both `https://app.cal.localhost` and `https://cal.localhost` locally. This is a quick guide on how can we achieve this setup locally for development purposes.

## Prerequisites

* Caddy Server
* Dnsmasq

### Install Dnsmasq

```bash
brew install dnsmasq
```

### Configure Dnsmasq to resolve \*.localhost domains

First let’s check where our brew installation config files are:

```bash
$ brew --prefix
/opt/homebrew
```

In my case it lives at `/opt/homebrew/etc/dnsmasq.conf`

```bash
# Route all *.localhost addresses to localhost
address=/localhost/127.0.0.1

# Don't read /etc/resolv.conf or any other configuration files.
no-resolv

# Never forward plain names (without a dot or domain part)
domain-needed

# Never forward addresses in the non-routed address spaces.
bogus-priv
```

### **Run Dnsmasq now and anytime we restart the system**

```bash
sudo brew services start dnsmasq
```

### Make macOS use our local DNS server (Dnsmasq) for .localhost addresses

Create the following file at `/etc/resolver/localhost`:

```
nameserver 127.0.0.1
```

With that, you can go to `subdomain.localhost` in your browser and it will point to `localhost`. So if your app is running on port `3000`, simply go to `subdomain.localhost:3000`.

But what if you're looking for the following setup?

```
cal.localhost       -> localhost:3001
app.cal.localhost   -> localhost:3000
```

This we can solve with [Caddy](https://caddyserver.com/) which is a super-awesome simple HTTP server!

### **Install Caddy**

```bash
brew install caddy
```

### **Configure Caddy**

In my case (because my `brew --prefix` is `/opt/homebrew`), my global Caddyfile is at `/opt/homebrew/etc/Caddyfile`. This file we can setup to act as a simple reverse proxy for our individual apps running on different ports:

<pre><code><strong>https://cal.localhost {
</strong>        reverse_proxy localhost:3001
}

https://app.cal.localhost {
        reverse_proxy localhost:3000
}
</code></pre>

### **Run Caddy now and every time your system restarts**

```bash
brew services start caddy
```

That's it! If you change your Caddyfile, you will need to `brew services restart caddy`.

### Setup our your environment variables

```bash
NEXTAUTH_URL='https://app.cal.localhost'
NEXT_PUBLIC_WEBAPP_URL='https://app.cal.localhost'
NEXT_PUBLIC_WEBSITE_URL='https://cal.localhost'
NODE_TLS_REJECT_UNAUTHORIZED=0  # Needed so HTTPS doesn't complain locally
```

### Run website and web app at the same time

```bash
yarn turbo run dev --scope="@calcom/web" --scope="@calcom/website"
```

### Go to the website or web app domain

You should be able to go to  `https://app.cal.localhost` and `https://cal.localhost` successfully 🙌

Thanks to Max 's article [Local subdomains on macOS with Dnsmasq](https://maxschmitt.me/posts/local-subdomains-dnsmasq-caddy/) and Caddy for making it easy to get started with Dnsmasq.
