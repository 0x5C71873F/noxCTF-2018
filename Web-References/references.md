# Challenge Name : Reference

>What is your reference again?
>
>http://chal.noxale.com:5000
>

When we visit the address, We get this nice "welcoming" page.

![img1](https://raw.githubusercontent.com/0x5C71873F/noxCTF-2018/master/Web-References/img1.png)

Digging through the HTML Document we find a script tag linking `/js/index.js` 

![img2](https://raw.githubusercontent.com/0x5C71873F/noxCTF-2018/master/Web-References/img2.png)

Upon primitive inspection it's an ajax function which returns success and possibly flag or  failure based on request to url `/check_from_google`.

Inferring from the challenge title and from the url name `/check_from_google` we have to set the [HTTP Referer](https://en.wikipedia.org/wiki/HTTP_referer) field in request header to url `/check_from_google`.

Fire up burp suite, capture the request and add a referer field with `www.google.com` as the value. 

![img3](https://raw.githubusercontent.com/0x5C71873F/noxCTF-2018/master/Web-References/img3.png)

We get a base64 string as response. Decoding it, gives us the flag.

The flag is : 
`noxCTF{G0ogL3_1s_4lW4Ys_Ur_b3ST_R3f3r3nc3}`
