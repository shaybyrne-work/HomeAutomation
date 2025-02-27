# Cold Dip Automation: Saving My Marriage One Sensor at a Time

## The Backstory
Over a year ago, my wife decided that casually plunging into frozen lakes in Muskoka, Ontario just wasn’t hardcore enough. Nope — she wanted to bring that delightful near-death experience right to our doorstep.

Before I could even muster a, “Wait, what?!”, there it was — her very own “cold plunge pool” proudly occupying prime real estate on our back deck.

I say **“pool,”** but let’s call it what it really was — a **livestock water trough**. That’s right. The kind designed for cows, not spa enthusiasts. Classy!!

![Cold Plunge Pool - aka Cattle Trough](https://github.com/shaybyrne-work/HomeAutomation/blob/main/ColdDip/trough.jpg)

---

## The Carpenter’s Dilemma
First and foremost, being a carpenter, seeing that eyesore sitting on my deck was unacceptable. So, like any good husband, I **over-engineered the hell out of it**.

### 💥 BOOM! Enter the Enhancements:
- ✅ 2” rigid insulation box
- ✅ Padded insulated lid
- ✅ Small heater pad
- ✅ Charcoal water filter and air pump
- ✅ Smart plug automation

**Oh LA LA... Very Spa Like!!**

![Upgraded Cold Dip Setup](https://github.com/shaybyrne-work/HomeAutomation/blob/main/ColdDip/spalike.jpg)

---

## The First Attempt: A Noble but Flawed Effort
### Step 1: Insulation
Built a custom box around the tank using 2” rigid insulation and a padded lid — because even ice baths deserve a little luxury.

### Step 2: Heating
Slapped a small heater pad to the side, hoping it would fend off the frost.

### Step 3: Filtration
Added a charcoal filter pump and air pump — because my wife draws the line at murky water.

### Step 4: Automation
Tied it all together with a smart plug and a **basic Home Assistant automation** that turned it on whenever the outdoor temperature dipped below freezing.

It was simple. It was elegant. It was... **not enough.**

### Extra Sensor - Shelly Uni + DS18B20
I added a Shelly Uni with a DS18B20 temperature sensor to monitor water temperature. **It still wasn’t enough.**

---

## The Harsh Reality of Canadian Winters
When it hits **-20°C (-4°F)**, no tiny heater pad stands a chance.

### 🚨 The Results?
- ❄️ Ice formed anyway.
- 💪 My wife had to break the ice to get in.
- 😡 My Shelly Uni constantly disconnected.
- 😤 My frustration level hit record highs.

---

## Round Two: The Ultimate Cold Dip Upgrade
I officially declared Phase 1 a “prototype” — a fancy way of saying *it failed*, but at least I learned something.

Luckily, my wife accepted the first-year learning curve... but immediately tried to convince me that buying one of those fancy hipster cold plunges wasn’t that bad of an idea.

**Nice try. But now it was personal.**

Winter 2024 was approaching, and I had **one goal:**  
**Build the most over-the-top, sensor-packed, Home Assistant-powered cold plunge Ontario has ever seen.**

---

## The Upgrades
### Clearly, More Heat + Better Insulation Was Needed
- 🔹 **Two 120V RV tank heating pads**
- 🔹 **NASA-grade Bubble-Pack Insulation**
- 🔹 **Shelly Plus 2PM (for heating pad control)**
- 🔹 **Shelly Plus Add-On + DS18B20 Temperature Sensor**

### Bonus Features
- **Separate Cleaning Cycle:** The charcoal filter and air pump were split onto their own smart plug, handled by a separate cleaning automation.
- **Automation logic:** Refined to adapt to environmental conditions instead of blindly running on/off.

---

## Home Assistant: Where the Real Magic Happens
If you’ve ever fallen into the Home Assistant rabbit hole, you know **there’s no such thing as done**. There’s always something to tweak.

This was no longer about keeping the water unfrozen — this was about making the most **efficient, reliable, and hands-off system possible.**

---

## The Secret Sauce: Smarter Binary Sensor
DS18B20 sensors can be **flappy** (technical term). Water cools unevenly, so the sensor often bounced between on and off.

### The Solution
✅ **A binary sensor template with hysteresis.**  
This **prevents rapid cycling** and gives the heater pads a fighting chance.

---

## Helpers & Automations
Without some **failsafes**, this could have quickly turned into an out-of-control automation nightmare. These helpers kept things sane:

### ✅ Helpers
- **Cold Dip Automation Lock:** Prevents overlapping runs.
- **Cold Dip Cleaning:** Separates cleaning and heating.
- **Cold Dip Heat Mat Timer:** Controls runtime so the pads don’t run 24/7.

---

## 🚀 Automation: The Final Boss
The automation now reacts to:
- ✔️ **Outdoor temperature forecasts** — Longer heating at -20°C, shorter at -5°C.
- ✔️ **Current pool temperature** — Stops unnecessary heating.
- ✔️ **Manual overrides** — Because sometimes you just want a button.
- ✔️ **Automation Lock (Mutex)** — Ensures only one automation run at a time.

And just like that, my cold dip automation dreams became a cold, well-regulated reality.

---

## Final Thoughts
This all kicked off in **September 2023**, with **Phase 2** starting in September 2024. The system officially went live with a water fill on **November 28, 2024**, and after endless tweaks, cursing at YAML, and fighting through January hiccups, the system settled at a beautiful **average temperature of 3.1°C**.

### 💪 After All That:
- ✔️ **The pool never froze this season.**
- ✔️ **My wife is thrilled (the only real success metric).**
- ✔️ **I’ve retired from my unpaid, frostbitten job as Chief Polar Plunge Engineer.**

### And the Best Part?
Not only did I automate a glorified cow trough into the **Cadillac of backyard ice baths**, I out-automated every overpriced, influencer-endorsed cold plunge on Instagram.

**Sorry hipsters — my cattle trough has logs, sensors, and a personal grudge against paying $10k for fancy frozen water.**

---

## Would I Do It Again?
✅ Absolutely.

Would I rather be soaking in my hot tub instead of freezing my hands off fixing sensors?  
✅ 1000%.

**But hey — happy wife, happy life… even if it means automating a cattle trough full of ice water instead of enjoying a warm soak like a sane person.**

---

## 📸 Images
- [Cold Plunge Pool Image 1 - Trough](https://github.com/shaybyrne-work/HomeAutomation/blob/main/ColdDip/trough.jpg)
- [Cold Plunge Pool Image 2 - Spa Like Setup](https://github.com/shaybyrne-work/HomeAutomation/blob/main/ColdDip/spalike.jpg)

## ⚠️ Disclaimer
The YAML, automations, and configurations shared in this post have been edited for privacy and are provided purely for inspiration and entertainment.

I’m by no means a Home Assistant expert — I’m just a stubborn Irish guy living in Canada, trying to keep a glorified cattle trough from becoming a permanent ice sculpture. Every step of this process has been made possible thanks to the incredible Home Assistant community, who generously share their knowledge, tips, and life-saving YAML snippets. Sláinte! 🇮🇪🍁
