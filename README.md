# PagerDuty Without OpenSSL
Just changed some package feature flags to make this compile without openssl (no linking to -lssl, or -lcrypto). The rest of it is the same.

You should be able to add a lot more compilation targets now (including wasm)
 
Similar to https://github.com/sachiniyer/megalodon-rs-no-openssl

# PagerDuty
[![Build Status](https://github.com/archisgore/pagerduty-rs/actions/workflows/build.yml/badge.svg)](https://github.com/archisgore/pagerduty-rs/actions/workflows/build.yml)

# pagerduty-rs

A PagerDuty Events V2 API Client Library in Rust.

## Using the API

Complete API examples are provided as [integration tests](./tests).

With feature `sync`:

```.rust
use pagerduty_rs::eventsv2sync::*;
use pagerduty_rs::types::*;

// ....

// Create an API client with an Integration Key
let ev2 = EventsV2::new(String::from("IntegrationKey"), Some("Optional pagerduty-rs user agent".to_owned())).unwrap();

// Then send an event (which might be a change, alert trigger/acknowledge/resolve)...
ev2.event(Event::AlertTrigger(AlertTrigger{
    // ...
}));
```

With feature `async`:

```.rust
use pagerduty_rs::eventsv2async::*;
use pagerduty_rs::types::*;

// ....

// Create an API client with an Integration Key
let ev2 = EventsV2::new(String::from("IntegrationKey"), Some("Optional pagerduty-rs user agent".to_owned())).unwrap();

// Then send an event (which might be a change, alert trigger/acknowledge/resolve)...
ev2.event(Event::AlertTrigger(AlertTrigger{
    // ...
})).await;
```

