# Captcha Reusable with [```ajax-boot-modal```](https://github.com/Alimir/ajax-bootmodal-login) WordPress plugin  
- Affected: ```ajax-bootmodal-login``` WordPress plugin.
- Version: `1.4.3` and possibly prior
- Privileges required: None
- CVE-ID: ```CVE-2018-15876```
- Author:
  - [Lydéric Lefebvre](https://www.linkedin.com/in/lydericlefebvre/)
  - [Fabien Haureils](https://www.linkedin.com/in/fabien-haureils/)

## Index

| Title        | Description   |
| ------------- |:-------------|
| [Description](#description)  | Description |
| [Scenario1: Register victims](#register-victims-using-same-captcha)  | Register victims using same CAPTCHA |
| [Scenario2: Spam victims](#spam-victims-using-same-captcha)  | Spam victims using same CAPTCHA |
| [Scenario3: Brute forcing credentials](#brute-forcing-credentials)  | Brute forcing credentials |

## Description
Register form, login form and password recovery form need CAPTCHA solving to perform actions. However, these CAPTCHAs seem to be valid as long as the user session is valid. One could send as many requests as one wished by automatisation. This allows an attacker to spam large number of mail addresses, and brute-force credentials.

![plugin](https://image.noelshack.com/fichiers/2018/34/6/1535214692-plugin.png)

## Register victims using same CAPTCHA
#### Requests
First, an attacker can register a list of mail addresses he want to spam simply by replaying register request with Burp Intruder. Here, one of the requests sent:
![regreq](https://image.noelshack.com/fichiers/2018/34/6/1535214212-regreq.png)

#### Responses
Here, one of the server responses:
![regrep](https://image.noelshack.com/fichiers/2018/34/6/1535214288-regrep.png)

## Spam victims using same CAPTCHA
#### Requests
Next, the attacker can spam all users simply by replaying password recovery request with Burp Intruder.
![losreq](https://image.noelshack.com/fichiers/2018/34/6/1535214353-reqpass.png)

#### Responses
Here, one of the server responses:
![losrep](https://image.noelshack.com/fichiers/2018/34/6/1535214378-reppass.png)

#### Spam
Here is what looks like a victim's web mail after the attack. 
![mail](https://image.noelshack.com/fichiers/2018/34/6/1535214487-mail.png)

## Brute forcing credentials
#### Requests
Like password recovery form and register form, login form is also vulnerable. This allows an attacker to brute force credentials.
![logi_req](https://image.noelshack.com/fichiers/2018/34/6/1535225018-log-req.png)

#### Responses
Here, one of the server responses:
![logi_rep](https://image.noelshack.com/fichiers/2018/34/6/1535219675-log-rep.png)
