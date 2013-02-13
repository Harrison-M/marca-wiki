So, I found inspiration for markup UI in a bizarre place--I was looking up some song lyrics, and I stumbled across rapgenius.com. Let me document a few steps of their markup process, along with my thoughts about how we could implement these ideas in Marca.

Song lyrics (document text)
![Screen 1](https://f.cloud.github.com/assets/867379/153486/ae735f76-75f9-11e2-9d2f-b4ea3153bb83.png)

Selection brings up "Explain" bubble (Insert note / markup)
![Screen 2](https://f.cloud.github.com/assets/867379/153485/ae700da8-75f9-11e2-9ff9-ebefd85afea0.png)
This design is helpful because the "Explain" bubble appears right at the point you've stopped highlighting. For us, I think that the Explain bubble could contain two buttons, Insert Note and Add Markup

Clicking explain brings up modal dialogue
![Screen 3](https://f.cloud.github.com/assets/867379/153484/ae6f5bce-75f9-11e2-8880-f74d295c6524.png)
I'm not sure about this bit. Obviously, it'd be somewhat redundant if we kept our right-hand menu where all this functionality lives now. On the other hand, if we adopted this approach, it could potentially allow us to eliminate the right-hand menu, leading to a cleaner display.



