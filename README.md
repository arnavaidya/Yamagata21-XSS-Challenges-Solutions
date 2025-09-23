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

This payload works for this stage:

    " onmousover=alert(document.domain)

<p align="center">
<img width="3840" height="762" alt="image" src="https://github.com/user-attachments/assets/60ad8339-3a1b-490c-94f1-3bc77e1854e8" />
</p>
