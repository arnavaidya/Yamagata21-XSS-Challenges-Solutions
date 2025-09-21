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
<img width="684" height="317" alt="image" src="https://github.com/user-attachments/assets/cb8b587b-af7f-466f-bdc0-219497718a28" />
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

We have a target to exploit. Change the input type from 'hidden' to 'text' to see how the input value is stored.
