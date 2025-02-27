**Cold Dip Automation: Saving My Marriage One Sensor at a Time**

Over a year ago, my wife decided that casually plunging into frozen lakes in Muskoka, Ontario just wasn’t hardcore enough. Nope — she wanted to bring that delightful near-death experience right to our doorstep.
Before I could even muster a, “Wait, what?!”, there it was — her very own “cold plunge pool” proudly occupying prime real estate on our back deck.
I say “pool,” but let’s call it what it really was — a livestock water trough. That’s right. The kind designed for cows, not spa enthusiasts. Classy!!

  
**The Carpenter’s Dilemma**
First and foremost, being a carpenter, seeing that eyesore sitting on my deck was unacceptable. So, like any good husband, I over-engineered the hell out of it.
💥 BOOM! Enter the enhancements:
✅ 2” rigid insulation box
✅ Padded insulated lid
✅ Small heater pad
✅ Charcoal Water Filter and Air Pump
✅ Smart plug automation

Oh LA LA,, Very Spa Like !!
   

**The First Attempt: A Noble but Flawed Effort**
Step 1: Insulation. I built a custom box around the tank using 2” rigid insulation and lined the lid with padded insulation—because even ice baths deserve a little comfort.
Step 2: Heating. I stuck a small heater pad to one side, hoping it would keep the water just above iceberg status.
Step 3: Filtration. I dropped in the charcoal filter pump and the air pump, because while my wife enjoys cold water, she draws the line at murky water.
Step 4: Automation. I wired it all to a smart plug, then wrote a Home Assistant automation to turn everything on when the outside temperature dipped below 0°C (32°F).
It was simple. It was elegant. It was... not enough.
Thinking I could improve things, I added a Shelly Uni with a DS18B20 temperature sensor to get real-time water temperature readings. But as winter tightened its grip, I quickly realized:
-20°C (-4°F) doesn’t care about my tiny heater pad.
Neither does ice.

**The Harsh Reality of Canadian Winters**
As any Canadian will tell you, “Below freezing” is a bit of an understatement. When it hits -20°C (-4°F), no tiny heater pad can stand up to the wrath of Ontario winters.
🚨 The results? 🚨
❄️ Ice formed anyway.
💪 My wife had to break the ice to get in.
😡 My Shelly Uni constantly disconnected.
😤 I grew frustrated.
💡 Time for Round Two.

**Round Two: The Ultimate Cold Dip Upgrade**
I officially declared Phase 1 a “prototype”—which is really just a fancy way of saying it failed, but at least I learned something.
Fortunately, my wife accepted it as a first-year learning experience (which was a relief) but then immediately tried to convince me that the fancy hipster versions weren’t that expensive.
Nice try. But at this point, it was personal.
I wasn’t about to let some overpriced, influencer-approved cold plunge tub win. No, Phase 2 was happening, and it was going to be bigger, better, and way more automated.

As I waited for Winter 2024 to loosen its icy death grip so I could finally free the pool from its frozen prison, I began to ponder my next steps.
💭 Should I upgrade the heating system?
💭 Add more insulation?
💭 Maybe just accept defeat and start calling it an outdoor ice rink?
One thing was clear: Round Two was coming, and this time, the automation wasn’t going down without a fight. 🚀

Clearly, more heat + better insulation was needed. Enter:
🔹 Two 120V RV tank heating pads 
🔹 Bubble-Pack Insulation (NASA-grade, probably)
🔹 Shelly Plus 2PM inside a Service Box 
🔹 Shelly Plus Add-On + DS18B20 Temperature Sensor
The Shelly Plus 2PM gave me independent control over each heating pad, and the DS18B20 sensor let me monitor the water temperature. Progress!

**Additional Smart Upgrades**
•	Cleaning Cycle? Now separate! The charcoal filter and air pump got their own smart plug controlled by a simple cleaning automation on a schedule.
•	Automation logic? Refined! Now it adapts to environmental conditions instead of blindly running on/off.

**Home Assistant: Where the Real Magic Happens**
If you’ve ever fallen down the Home Assistant rabbit hole, you know there’s no going back. Every automation can always be improved. This wasn’t just about turning a heater on and off—it was about efficiency, stability, and not waking up to a frozen trough that my wife needed an axe to get into.
The Secret Sauce: A Smarter Binary Sensor
The problem with directly using the DS18B20 sensor? Water cools unevenly, which causes the sensor to flap between on/off states constantly.
Solution: A binary sensor template that smooths out the readings. This prevents rapid on/off cycling, allowing stable heating operation.

**Helpers & Automations**
Let’s be real—without some solid failsafe’s, this whole setup would have turned into an automated mess of competing triggers, confused logic, and a very grumpy me. So, to keep things from spiraling into chaos, I built a set of helpers:
✅ Cold Dip Automation Lock (Input Boolean) – Prevents overlapping executions because nobody wants an automation that fights itself.
✅ Cold Dip Cleaning (Input Boolean) – Separates cleaning from heating, because a warm, murky ice bath isn’t exactly the goal.
✅ Cold Dip Heat Mat Timer (Timer) – Manages runtime durations so the heater isn’t running 24/7 like it’s trying to boil pasta.

**Automation: The Final Boss Battle**
Once the template sensors and helpers were locked in, the automation evolved from barely working to home automation perfection (at least in my mind).
🚀 Now, it runs like a well-oiled (but very, very cold) machine by reacting to:
✔️ Real-time temperature – Heating duration automatically adjusts based on forecasted lows, because -5°C and -25°C are very different problems.
✔️ Current pool temperature – Prevents unnecessary heating cycles, because running heat mats on a perfectly fine pool is just wasting watts.
✔️ Manual overrides – Because sometimes, you just want to hit a switch and feel like you’re in control (even if Home Assistant is still the real boss).
✔️ No automation overlap – A mutex system ensures only one execution at a time, preventing automation chaos and keeping things… chill. 😎
And just like that, my cold dip automation dreams became a cold, well-regulated reality.

**Final Thoughts**
This whole thing started in September 2023, with Phase 2 kicking off in September 2024, long before winter had fully sharpened its icy claws. The system finally came to life with a tank fill on November 28, 2024, and like any great Home Assistant project, it went through endless tweaks, unexpected failures, and the occasional “WHY IS THIS NOT WORKING?!” meltdown in January.
But in the end, the system held steady at a frosty-but-functional average of 3.1°C, except for a few mystery days where the universe — and possibly the cold plunge gods — decided to mess with me.
After weeks of testing, frozen fingers, cursing at YAML, and more automation tweaks than I’d care to admit, I can confidently say:
✔️ The pool hasn’t frozen once this season.
✔️ My wife is beyond thrilled. (Which, let’s be honest, is the only metric that matters.)
✔️ Home Assistant now runs the show, meaning I’ve officially hung up my parka and retired from my prestigious role as Chief Polar Plunge Engineer — a position with no pay, constant frostbite, and the sheer joy of debugging YAML while my fingers slowly froze to the keyboard.
But hey, all that effort paid off, because not only did I automate a glorified cattle trough into the Cadillac of backyard ice baths, I also out-automated every overpriced, influencer-endorsed, artisanal cold plunge tub Instagram could throw at me. Sorry hipsters — my trough has logs, sensors, and a personal grudge against paying $10k for fancy frozen water.
Would I do it again? Absolutely.
Would I rather be soaking in a hot tub instead of freezing my hands off fixing sensors? 1000%.
But hey — happy wife, happy life… even if that means spending an entire winter automating a cattle trough full of ice water instead of enjoying a nice, warm soak like a sane person.🥶😂

 

