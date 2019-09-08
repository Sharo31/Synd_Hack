# Synd_Voice| Unified Voice based Banking Assistant supporting Offline Payments

Synd_Voice is **an offline payment service**, built on the top of [PayTM APIs](http://paywithpaytm.com/developer/), which can be used on any mobile device (including legacy mobile devices which don't even have a GUI or provisions for internet connectivity) without installing any additional application.

We intended to target the customers who don't own a smartphone or have proper internet access.

Our efforts also highlighted a way for PayTM to increase their user-base.

This was possible due to SMS capabilities in every mobile device, hence we hacked on that to make and receive payments easily using a simple keyword **synd**.

We built this using :

* [Sinatra](http://www.sinatrarb.com/), Web framework for Ruby.
* [Redis](https://redis.io/), In-memory key-value data store.

We also used the following to imitate an SMS gateway :

* [Twilio](https://www.twilio.com/), cloud platform providing SMS APIs for text-messaging.
* A mobile application to route text-messages to a web-server.

## Setup

Requirements:

* Ruby
* Redis
* [bundler](https://bundler.io/) gem

Installation:

1. Run `rake install`. It will install `bundler` if you have not it installed and install needed gems.
1. Rename `config.json.sample` to `config.json` and replace `XXXX` with needed values.

Running:

1. Run the service with `rake run` or just `rake` in your console.

## Current Scope

### Register User

* Since registering a new user (unique : mobile number) is a 2-step process on PayTM, we implemented a similar logic.
* User can simply initiate the registration process by sending the following text to a **PayTM dedicated number**

```vim
synd (reg | registration) <email>
```

* Doing this results in the user receiving a SMS with  an OTP. He/She needs to send this to the dedicated number in the following format.

```vim
synd validate <OTP>
```

Hooray! You successfully registered at PayTM (if you hadn't) and our service as well.

### Check Available Balance

```vim
synd (bal | balance)
```

### Send / Pay Money to another number

```vim
synd (send | pay)  <payee number> <amount>
```


It seems we have created a possible user-base of around 83.3 crore people for PayTM. :v:
