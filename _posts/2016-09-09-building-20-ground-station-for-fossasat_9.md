---
title: 'Building a $20 ground station for the FossaSat-1 LoRa
satellite #LoRa #Satellite @spiessa'
date: 2019-12-09T15:10:00+01:00
draft: false
---

[Andreas Spiess on YouTube](https://www.youtube.com/watch?v=5k0aM-PJzo8&feature=youtu.be) discusses building a 20 dollar LoRa Satellite Ground Station and following the FossaSat-1 launch:

> Ordinary Satellite Ground Stations cost millions. We will build one for 20 dollars for the newly launched LoRa satellite. Let’s build it in parallel to the launch of the Electron spacecraft from Rocket Lab. Will it be successful?
> 
> In my last video, I announced that the 16-year old Julian Fernandez and a small team built FossaSat-1. We will accompany the launch and in parallel, we will build a Ground Station and test it with the real satellite. Will it work?
> 
> Links:
> 
> *   Fossa Systems: [https://fossa.systems/](https://www.youtube.com/redirect?v=5k0aM-PJzo8&event=video_description&q=https%3A%2F%2Ffossa.systems%2F&redir_token=mK_KWSmVojtoUwCdVu3RyFEFW_V8MTU3NTkzNjgyNUAxNTc1ODUwNDI1)
> *   Donations here (for the next one): [https://www.gofundme.com/f/fossasat1-…](https://www.youtube.com/redirect?v=5k0aM-PJzo8&event=video_description&q=https%3A%2F%2Fwww.gofundme.com%2Ff%2Ffossasat1-la-democratizacion-del-espacio&redir_token=mK_KWSmVojtoUwCdVu3RyFEFW_V8MTU3NTkzNjgyNUAxNTc1ODUwNDI1)
> *   Ground Station Software: [https://github.com/G4lile0/ESP32-OLED…](https://www.youtube.com/redirect?v=5k0aM-PJzo8&event=video_description&q=https%3A%2F%2Fgithub.com%2FG4lile0%2FESP32-OLED-Fossa-GroundStation&redir_token=mK_KWSmVojtoUwCdVu3RyFEFW_V8MTU3NTkzNjgyNUAxNTc1ODUwNDI1)
> *   TLE File: [https://drive.google.com/file/d/1g0GW…](https://www.youtube.com/redirect?v=5k0aM-PJzo8&event=video_description&q=https%3A%2F%2Fdrive.google.com%2Ffile%2Fd%2F1g0GWEwvYPk8Yy_cBStU0Puzw3HM9j4F5%2Fview%3Fusp%3Dsharing&redir_token=mK_KWSmVojtoUwCdVu3RyFEFW_V8MTU3NTkzNjgyNUAxNTc1ODUwNDI1)
> *   Sensor Software (experimental): [https://github.com/G4lile0/FossaSaT\_S…](https://www.youtube.com/redirect?v=5k0aM-PJzo8&event=video_description&q=https%3A%2F%2Fgithub.com%2FG4lile0%2FFossaSaT_Sensor_Transmission_PoC&redir_token=mK_KWSmVojtoUwCdVu3RyFEFW_V8MTU3NTkzNjgyNUAxNTc1ODUwNDI1)
> *   Gpredict Download: [http://gpredict.oz9aec.net/download.php](https://www.youtube.com/redirect?v=5k0aM-PJzo8&event=video_description&q=http%3A%2F%2Fgpredict.oz9aec.net%2Fdownload.php&redir_token=mK_KWSmVojtoUwCdVu3RyFEFW_V8MTU3NTkzNjgyNUAxNTc1ODUwNDI1)
> *   Join Telegram group: [https://t.me/joinchat/DmYSElZahiJGwHX…](https://www.youtube.com/redirect?v=5k0aM-PJzo8&event=video_description&q=https%3A%2F%2Ft.me%2Fjoinchat%2FDmYSElZahiJGwHX6jCzB3Q&redir_token=mK_KWSmVojtoUwCdVu3RyFEFW_V8MTU3NTkzNjgyNUAxNTc1ODUwNDI1)
> *   Get MQTT credentials after test phase): [https://forms.gle/3Mm74mGdGxvQyJC9A](https://www.youtube.com/redirect?v=5k0aM-PJzo8&event=video_description&q=https%3A%2F%2Fforms.gle%2F3Mm74mGdGxvQyJC9A&redir_token=mK_KWSmVojtoUwCdVu3RyFEFW_V8MTU3NTkzNjgyNUAxNTc1ODUwNDI1)
> *   Map of stations: [https://fossa.apaluba.com/worldmap/](https://www.youtube.com/redirect?v=5k0aM-PJzo8&event=video_description&q=https%3A%2F%2Ffossa.apaluba.com%2Fworldmap%2F&redir_token=mK_KWSmVojtoUwCdVu3RyFEFW_V8MTU3NTkzNjgyNUAxNTc1ODUwNDI1)
> *   TTGO 433MHz board: [http://s.click.aliexpress.com/e/4nF6NXM8](https://www.youtube.com/redirect?v=5k0aM-PJzo8&event=video_description&q=http%3A%2F%2Fs.click.aliexpress.com%2Fe%2F4nF6NXM8&redir_token=mK_KWSmVojtoUwCdVu3RyFEFW_V8MTU3NTkzNjgyNUAxNTc1ODUwNDI1)
> *   RFM95 433MHz: [http://s.click.aliexpress.com/e/F2BMWYSM](https://www.youtube.com/redirect?v=5k0aM-PJzo8&event=video_description&q=http%3A%2F%2Fs.click.aliexpress.com%2Fe%2FF2BMWYSM&redir_token=mK_KWSmVojtoUwCdVu3RyFEFW_V8MTU3NTkzNjgyNUAxNTc1ODUwNDI1)

See [the video above](https://www.youtube.com/watch?v=5k0aM-PJzo8&feature=youtu.be) for details.

![](https://cdn-blog.adafruit.com/uploads/2019/12/Untitled-14.png)