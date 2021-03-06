# ACME - Reference

Every Options for ACME
{: .subtitle} 

## TOML

```toml
    # Sample entrypoint configuration when using ACME.
    [entrypoints]
      [entrypoints.web]
      address = ":80"
      [entrypoints.web-secure]
      address = ":443"
        
    # Enable ACME (Let's Encrypt): automatic SSL.
    [acme]
    
    # Email address used for registration.
    #
    # Required
    #
    email = "test@traefik.io"
    
    # File used for certificates storage.
    #
    # Optional (Deprecated)
    #
    #storageFile = "acme.json"
    
    # File or key used for certificates storage.
    #
    # Required
    #
    storage = "acme.json"
    # or `storage = "traefik/acme/account"` if using KV store.
    
    # Deprecated, replaced by [acme.dnsChallenge].
    #
    # Optional.
    #
    # dnsProvider = "digitalocean"
    
    # Deprecated, replaced by [acme.dnsChallenge.delayBeforeCheck].
    #
    # Optional
    # Default: 0
    #
    # delayDontCheckDNS = 0
    
    # If true, display debug log messages from the acme client library.
    #
    # Optional
    # Default: false
    #
    # acmeLogging = true
    
    # If true, override certificates in key-value store when using storeconfig.
    #
    # Optional
    # Default: false
    #
    # overrideCertificates = true
    
    # Deprecated. Enable on demand certificate generation.
    #
    # Optional
    # Default: false
    #
    # onDemand = true
    
    # Enable certificate generation on frontends host rules.
    #
    # Optional
    # Default: false
    #
    # onHostRule = true
    
    # CA server to use.
    # Uncomment the line to use Let's Encrypt's staging server,
    # leave commented to go to prod.
    #
    # Optional
    # Default: "https://acme-v02.api.letsencrypt.org/directory"
    #
    # caServer = "https://acme-staging-v02.api.letsencrypt.org/directory"
    
    # KeyType to use.
    #
    # Optional
    # Default: "RSA4096"
    #
    # Available values : "EC256", "EC384", "RSA2048", "RSA4096", "RSA8192"
    #
    # KeyType = "RSA4096"
    
    # Use a TLS-ALPN-01 ACME challenge.
    #
    # Optional (but recommended)
    #
    [acme.tlsChallenge]
    
    # Use a HTTP-01 ACME challenge.
    #
    # Optional
    #
    # [acme.httpChallenge]
    
      # EntryPoint to use for the HTTP-01 challenges.
      #
      # Required
      #
      # entryPoint = "http"
    
    # Use a DNS-01 ACME challenge rather than HTTP-01 challenge.
    # Note: mandatory for wildcard certificate generation.
    #
    # Optional
    #
    # [acme.dnsChallenge]
    
      # DNS provider used.
      #
      # Required
      #
      # provider = "digitalocean"
    
      # By default, the provider will verify the TXT DNS challenge record before letting ACME verify.
      # If delayBeforeCheck is greater than zero, this check is delayed for the configured duration in seconds.
      # Useful if internal networks block external DNS queries.
      #
      # Optional
      # Default: 0
      #
      # delayBeforeCheck = 0
    
      # Use following DNS servers to resolve the FQDN authority.
      #
      # Optional
      # Default: empty
      #
      # resolvers = ["1.1.1.1:53", "8.8.8.8:53"]
    
      # Disable the DNS propagation checks before notifying ACME that the DNS challenge is ready.
      #
      # NOT RECOMMENDED:
      # Increase the risk of reaching Let's Encrypt's rate limits.
      #
      # Optional
      # Default: false
      #
      # disablePropagationCheck = true
    
    # Domains list.
    # Only domains defined here can generate wildcard certificates.
    # The certificates for these domains are negotiated at traefik startup only.
    #
    # [[acme.domains]]
    #   main = "local1.com"
    #   sans = ["test1.local1.com", "test2.local1.com"]
    # [[acme.domains]]
    #   main = "local2.com"
    # [[acme.domains]]
    #   main = "*.local3.com"
    #   sans = ["local3.com", "test1.test1.local3.com"]
```
