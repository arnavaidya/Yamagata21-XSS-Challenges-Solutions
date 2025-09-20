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
<img width="616" height="396" alt="image" src="https://github.com/user-attachments/assets/738b3311-57b6-43b8-bde8-51a0aaf9d9fb" />
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

Try entering a payload where the 'option' tag is closed and the alert tag is embedded.

    test123><img src=x onerror=alert(document.domain)>

<p align="center">
<img width="348" height="151" alt="image" src="https://github.com/user-attachments/assets/f77f6523-bcab-40c1-9efd-3e014b4ecb70" />
</p>

You'll get an alert and the stage will be cleared!

<p align="center">
<img width="673" height="298" alt="image" src="https://github.com/user-attachments/assets/c7f26df1-fece-46f0-9797-44b1df721bca" />
</p>
