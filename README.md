# Yamagata21-XSS-Challenges-Solutions
This repo contains my solutions to the XSS Challenges (by yamagata21).

## Stage #1

This is understandably the easiest stage of this game. 

Simply enter this payload in the input field: 

    <script>alert(document.domain)</script>

<p align="center">
<img width="626" height="346" alt="image" src="https://github.com/user-attachments/assets/28b7d4da-4689-4cfc-8041-5a62e5a22a1a" />
</p>

You'll get an alert and the stage will be cleared!

<p align="center">
<img width="2000" height="300" alt="image" src="https://github.com/user-attachments/assets/c28b75ba-d859-4dda-b16a-77ecbd8b5988" />
</p>

## Stage #2

This is where the game actually begins.

The hint says that there is an existing tag that needs to be closed first.

In order to do this, our payload should begin with something like: "><script......

<p align="center">
<img width="646" height="294" alt="image" src="https://github.com/user-attachments/assets/5f7b86cd-e8bc-444f-95a0-fc7614d18243" />
</p>

This is how the input tag is being closed to begin the injected script tag.

<p align="center">
<img width="335" height="47" alt="image" src="https://github.com/user-attachments/assets/1ae77ae8-47a3-40d0-a2ad-7a05cafe8a08" />
</p>

You'll get an alert and the stage will be cleared!

<p align="center">
<img width="2000" height="300" alt="image" src="https://github.com/user-attachments/assets/911ba403-9270-4f26-ba93-d973bd7b39a9" />
</p>

## Stage #3

The input field seems to be properly escaped. However, we are introduced to a new input field here; the dropdown.

<p align="center">
<img width="669" height="270" alt="image" src="https://github.com/user-attachments/assets/abb60337-7667-46cd-96f0-d789ec3853f3" />
</p>

The previous payload fails because of HTML encoding. Try intercepting the traffic using Burp Suite. 

You'll find another input field 'p2'.

<p align="center">
<img width="260" height="200" alt="image" src="https://github.com/user-attachments/assets/4d458717-28c6-4084-b083-f9e9c9abd258" />
</p>

Enter this payload in place of 'Japan' in p2.

    "><script>alert(document.domain)</script>

Forward this request.

You'll get an alert and the stage will be cleared!

<p align="center">
<img width="2000" height="300" alt="image" src="https://github.com/user-attachments/assets/518ab9a8-e368-4cb0-9031-0746326d2aa6" />
</p>

## Stage #4

The hint says there's a hidden input field. 

<p align="center">
<img width="659" height="269" alt="image" src="https://github.com/user-attachments/assets/b9009458-57ac-4535-8840-d9984e32c879" />
</p>

We have a target to exploit. Intercept the traffic in Burp Suite.

You'll find another input field 'p3'.

<p align="center">
<img width="260" height="200" alt="image" src="https://github.com/user-attachments/assets/54d0ec5b-13eb-4c85-95bd-2cb4404734d6" />
</p>

Enter the same payload as stage 2 in the 'p3' field.

    "><script>alert(document.domain)</script>

Forward the request.

You'll get an alert and the stage will be cleared!

<p align="center">
<img width="2000" height="300" alt="image" src="https://github.com/user-attachments/assets/30ab363d-3e2e-494a-a344-838af30605e1" />
</p>

## Stage #5

The hint says that the input field is now restricted to a certain input length.

<p align="center">
<img width="550" height="270" alt="image" src="https://github.com/user-attachments/assets/7917184c-b38b-4c53-96ab-374ec6724664" />
</p>

Open DevTools -> Elements and simply change the 'maxlength' and 'size' values to a big value like 50.

<p align="center">
<img width="400" height="50" alt="image" src="https://github.com/user-attachments/assets/96e874bd-2f89-451d-b893-8fe1892640ba" />
</p>

Now enter the same payload as stage 2 in the input field.

    "><script>alert(document.domain)</script>

Submitting will get you the alert and the stage will be cleared!

This is a client-side validation bypass.

<p align="center">
<img width="2000" height="300" alt="image" src="https://github.com/user-attachments/assets/85b8540e-1623-4cee-8345-97bf3eb5a56c" />
</p>

## Stage #6

The hint says that this stage has something to do with event handler attributes.

<p align="center">
<img width="550" height="270" alt="image" src="https://github.com/user-attachments/assets/42c97f46-e450-431b-b900-9eab97a73493" />
</p>

These include 'onmouseover', 'onclick', 'oninput' and many more.

So it is safe to assume that the payload in this stage needs to be designed using an event handler attribute.

Something like: 

    " onmouseover="alert(document.domain)"

<p align="center">
<img width="550" height="270" alt="image" src="https://github.com/user-attachments/assets/62f71acb-d78d-4eea-8a31-662b71887785" />
</p>

Submitting will get you an alert and the stage will be cleared.

<p align="center">
<img width="2000" height="300" alt="image" src="https://github.com/user-attachments/assets/eea0ee8a-6db7-4be6-9e94-bf6575ddaeee" />
</p>

## Stage #7

This stage seems to be similar to the previous one.

<p align="center">
<img width="550" height="270" alt="image" src="https://github.com/user-attachments/assets/13d4edb6-8f36-4809-a26f-52eea173ac0b" />
</p>

The previous stage's payload won't work here, since this stage adds an extra " for every double quote entered.

<p align="center">
<img width="550" height="520" alt="image" src="https://github.com/user-attachments/assets/66bc9446-79bf-482c-b938-c4f84c221e01" />
</p>

This payload works for this stage:

    " onmousover=alert(document.domain)

<p align="center">
<img width="2000" height="300" alt="image" src="https://github.com/user-attachments/assets/c21ec5ed-dff8-4956-bb55-9afd35843622" />
</p>

## Stage #8

The hint mentions something about javascript scheme.

<p align="center">
<img width="550" height="270" alt="image" src="https://github.com/user-attachments/assets/ccf2eaa0-a884-4a1a-8763-3d6170f69f4b" />
</p>

We are expected to 'Make a link' using javascript scheme.

The payload will simply look like:

    javascript:alert(document.domain)

Submitting this payload will create a link.

Clicking on it will will send an alert and the stage will be cleared!

<p align="center">
<img width="2000" height="300" alt="image" src="https://github.com/user-attachments/assets/66c627c1-4efe-442b-9008-98b1f0d73633" />
</p>

## Stage #9

This stage has something to do with UTF-7 which is supported in older versions of Internet Explorer only. The stage can be skipped by simply entering 'alert(document.domain)' in the Console in DevTools.

## Stage #10

The hint mentions something which I didn't get. 

<p align="center">
<img width="550" height="270" alt="image" src="https://github.com/user-attachments/assets/bf7327cc-77dd-46d6-90f7-4133272119ae" />
</p>

However I tried the classic <script>alert(document.domain)</script> payload and found out that the word 'domain' (word after the '.') is being removed.

There are a few different approaches to solve this stage.

1. The payload here is designed in such a way that the word 'domain' will be regenerated if broken down.
    
       "><script>alert(document.dodomainmain)</script>

2. Encode and decode 'document.domain' with Base64.

       "><script>(eval(atob('YWxlcnQoZG9jdW1lbnQuZG9tYWluKQ==')))</script>

4. Split the 'document.domain' part and concat it back.

       <script>alert(eval('document.dom'+'ain'))</script>

Submitting any of these payloads will generate an alert and the stage will be cleared.

<p align="center">
<img width="2000" height="300" alt="image" src="https://github.com/user-attachments/assets/8bf0613e-288d-4a7e-97db-63759e3c8ad5" />
</p>

## Stage #11

This stage isn't available.

## Stage #12 - #14

These stages seem to work in older versions of Internet Explorer only and can be skipped by simply entering 'alert(document.domain)' in the Console in DevTools.

## Stage #15

The hint suggests that this stage has something to do with the 'document.write()' function.

<p align="center">
<img width="1617" height="775" alt="image" src="https://github.com/user-attachments/assets/f20cedc3-389c-4321-9945-32a64ae681f8" />
</p>

I tried a test payload of the usual '<script>alert(document.domain)</script>' and observed that the characters '<', '>' are being HTML encoded.

<p align="center">
<img width="400" height="50" alt="image" src="https://github.com/user-attachments/assets/c71935ec-35d1-43d5-b181-feaf969b2d7d" />
</p>
