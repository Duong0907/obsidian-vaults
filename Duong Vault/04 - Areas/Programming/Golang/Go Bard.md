## Overview
Belarus are some notes about how to use Google Bard Go SDK

---
## OBTAIN A BARD COOKIE

1. Visit [https://bard.google.com/](https://bard.google.com/) (login with your account).
2. F12 for console.
3. Session: Application → Cookies → `__Secure-1PSID` and `__Secure-1PSIDTS` cookie value.
## How to use 
- Create a GOBARD object.
- `.Ask("something")`
- `.GetAnswer()`
- Did not like this answer ? `.Next()` and `.GetAnswer()` (or `.NextAnswer()`)
- Want to go back to previous answer ? `.Prev()` and `.GetAnswer()` (or `.PrevAnswer()`)
- Next question (`.Ask()`) will keep Chat reference until `.Reset()` is called.
- `.Ask()` will use the "current answer" as a reference for the question.
- Have Fun!
## NOTES

1. Each Bard object, from `gobard.new()`, will have its own context until `Reset()` is called:

```
Bard01: Act as a simple calculator and calculate 2 + 2. Give the result only, no more words.

  Sure, I can help you with that.                                             
                                                                              
  2 + 2 = 4                                                                   
                                                                              
  I hope this is helpful. Let me know if you have any other questions.        

Bard02: Act as a simple calculator and calculate 4 + 8. Give the result only, no more words.

  Sure, I can help you with that.                                             
                                                                              
  4 + 8 = 12                                                                  
                                                                              
  Is there anything else I can help you with?                                 

Bard01: What if I add 5 to the result ?

  If you add 5 to the result of 2 + 2, you get 4 + 5 = 9.                     
                                                                              
  Is there anything else I can help you with today?                           

Bard02: What if I add 5 to the result ?

  If you add 5 to the result of 4 + 8, you get 12 + 5 = 17.                   
                                                                              
  Is there anything else I can help you with?  
```

> Reference: https://github.com/aquasecurity/gobard (Unofficial Go Bard Package)
## It's `Markdown` format for the answer. Example:

```md
Sure thing. I found you a few photos of different types of clocks:

* **Analog Clock:** This is the most common type of clock, and it has a face with hands that point to the hour, minute, and second.

[![Image of Analog clock](https://cdn.shopify.com/s/files/1/0556/8066/3742/products/4550344275733_org_1200x1200.jpg?v=1678206891)](https://www.muji.us/products/analog-clock-l-laca0a)
* **Digital Clock:** This type of clock displays the time in numbers, and it can be either battery-powered or plugged into an outlet.

[![Image of Digital clock](https://m.media-amazon.com/images/I/61MuSYQ7yhL._AC_UF894,1000_QL80_.jpg)](https://www.amazon.in/YORTOT-Oversize-Control-Brightness-Temperature/dp/B08R8FW63J)
* **Alarm Clock:** This type of clock is designed to wake you up at a certain time, and it can have a variety of features, such as snooze, a light, and a radio.

[![Image of Alarm clock](https://m.media-amazon.com/images/I/71ggBUmny9L.jpg)](https://www.amazon.com/Sharp-Twin-Bell-Alarm-Clock/dp/B08TB22P29)
* **Sundial:** This type of clock uses the sun to tell time, and it is a popular choice for people who want to live a more sustainable lifestyle.

[![Image of Sundial](https://www.thehoarde.com/resources/images/blog-pictures/Sundial-1-(Deposit-Photos)-21-7-22-crop-v2.jpg)](https://www.thehoarde.com/blog/a-beginners-guide-to-the-garden-sundial)
* **Cuckoo Clock:** This type of clock is a traditional European clock that has a cuckoo bird that pops out to announce the time.

[![Image of Cuckoo clock](https://m.media-amazon.com/images/I/81OBtQVTkuL._AC_UF894,1000_QL80_.jpg)](https://www.amazon.com/Trenkle-Quartz-Cuckoo-Forest-Chopper/dp/B00VZQ5ZTY)

I hope this helps!
```

## SNlM0e is null

If you hit SNlM0e is null issues, you may need to clear the cookie and login again:

- Clear cookies of bard.google.com and again
- login into the account
- F12 > Applications > Cookies > bard > `__Secure-1PSID` and `__Secure-1PSIDTS`
- Copy cookie and paste into your code.
- Re run and you are good to go.

> Reference: https://github.com/LarryDpk/Google-Bard (Java Google Bard SDK)

