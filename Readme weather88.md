<div align="center">

🌤️ Weather Glass

La météo, sans compte, sans pub, sans API key.

</div>

---

👋 Welcome

Every weather app I've ever installed wanted something from me first. An account. An email. Location tracking that never stops. A "premium" tier to unlock the hourly view. And the one thing they all have in common: they show you an ad before the temperature.

Weather Glass asks for none of that.

It's a single HTML file that shows you the weather. You open it, it detects where you are, and it tells you what's happening outside. If you'd rather look up a different city, you type its name and press Enter. That's the whole app. No account, no tracking beyond the one location request your browser handles directly, no ads, no subscription, no "Unlock the extended forecast with Premium."

The design is a glass card floating on a slowly shifting sky — a soft gradient that drifts from deep blue to slate and back, like weather rolling in behind a window. The card itself is translucent, blurred, gently bordered. Everything inside it is quiet: small type, thin strokes, muted whites. It looks like a piece of iOS, but it lives in one file on your computer.

The weather icons are drawn by hand, in code — SVG lines and circles and tiny raindrops that change with the WMO weather code. Sunny, cloudy, drizzle, freezing rain, snow, thunderstorm — each one has its own drawing, matching the same calm line-art style. They're not imported from an icon set. They're part of the file.

---

<!--
## 📸 Look Inside

<br />

<div align="center">
  <img src="https://github.com/mohamed005cheikh-rgb/weather88/raw/main/images/preview-1.png" alt="Current weather with the glass card" width="100%" />
  <br />
  <sub><b>① Current conditions</b></sub>
</div>

<br />
<br />

<div align="center">
  <img src="https://github.com/mohamed005cheikh-rgb/weather88/raw/main/images/preview-2.png" alt="The 7-day forecast row" width="100%" />
  <br />
  <sub><b>② The 7-day forecast</b></sub>
</div>

<br />
<br />

<div align="center">
  <img src="https://github.com/mohamed005cheikh-rgb/weather88/raw/main/images/preview-3.png" alt="Searching for a city" width="100%" />
  <br />
  <sub><b>③ Searching for a city</b></sub>
</div>
-->

---

✨ What you'll find

Your location, detected on load.
The moment the page opens, Weather Glass asks your browser for your position. If you say yes, it finds the city you're in, pulls the current weather, and shows you everything. If you say no, it falls back to Kyiv — because a weather app that shows nothing is worse than one that shows a city you didn't ask for.

Search any city in the world.
Type a name — Paris, Dakar, Nouakchott, Tokyo — and press Enter. Weather Glass looks it up through Open-Meteo's geocoding service, finds the first match, and fetches the weather for those coordinates. No dropdown, no autocomplete confusion. Type, Enter, done. If the city doesn't exist, a quiet red line tells you so.

Current temperature, in one big number.
Large, bold, no decimal places — because 23.4° and 23° feel the same outside, and the extra digit is just noise. Below it, a plain-language condition: Clear & Sunny, Partly Cloudy, Light Rain, Thunderstorm + Hail. And behind it, a drawing of the weather itself — the same one you'd make with a pencil if you were patient.

A date and time that stays current.
The card shows the day of the week and the current time in your local zone. It updates the moment you load the page. If you leave the tab open all day, it won't tick forward on its own — refresh when you care, and it'll be right.

Sunrise and sunset, side by side.
Two small sun icons at the top of the info bar, with the exact times for the location you're viewing. Useful at a glance for planning a walk, a photo, or a nap. It comes straight from Open-Meteo's daily forecast — accurate to the minute for the coordinates you're looking at.

Rain chance for the current hour.
A blue cloud-and-drops icon, and a percentage. It's pulled from the hourly forecast at whatever hour it is right now where you are — so Rain: 15% means fifteen percent chance during this hour, not the whole day. Honest, specific, small.

Humidity and wind.
Two quiet numbers in a row at the bottom of the details: relative humidity as a percentage, wind speed in kilometres per hour. Nothing else. No pressure, no UV, no dew point, no "feels like" — because three numbers you'll actually read beat twelve you'll scroll past.

Seven days, at a glance.
A row of seven small tiles: today plus the next six days. Each one shows the day name, a tiny icon, the day's high, and the day's low. Today is highlighted with a subtle background. That's the whole forecast. No hourly chart, no radar, no precipitation maps. Just the next week, reduced to the only things that matter: what day, what weather, how hot, how cold.

One source, one file.
Everything comes from Open-Meteo, a free, open, no-API-key weather service. Nothing is proxied through a server. Nothing is logged. Your browser talks directly to Open-Meteo for the weather, to BigDataCloud for the reverse-geocoding of your coordinates, and to nothing else.

---

🧭 How it works

1. Open the file.
One HTML file, no build step, no install. Double-click it and the card appears, the background gradient starts drifting, and Weather Glass asks for your location.

2. Allow location — or don't.
If you allow it, you get your local weather within a second or two. If you decline, the app falls back to Kyiv and tells you so, quietly, in the location line. Either way you're looking at real weather immediately.

3. Or search for somewhere else.
Type a city name into the search bar at the top and press Enter. The card empties for a moment, then fills with the new city's weather. The location line at the top updates to show which city you're looking at.

4. Read it, close it.
There is no "save this location" button, no favourites list, no persistent state. When you close the tab, it forgets everything except whatever your browser caches. Open it again, and it starts fresh from your current location.

That's the whole interaction. No settings, no account, no notifications, no widget to configure.

---

🛠️ A few small helps

"Why does it show Kyiv when I open it?"
Either you declined the location prompt, or your browser blocked it silently, or the geolocation request timed out. Kyiv is the fallback. You can search for your actual city instead — it takes three seconds.

"The location name says 'My Location' instead of a city."
The reverse-geocoding step uses BigDataCloud, a free service with no API key. Occasionally it doesn't know the name of a place — remote areas, some islands, coordinates in the middle of an ocean. When that happens, Weather Glass falls back to My Location rather than showing nothing. The weather itself is still accurate for your coordinates.

"Does it work offline?"
No. Weather data has to come from somewhere, and here that somewhere is Open-Meteo. The file itself loads offline, but the card will sit at Fetching weather... until the network comes back.

"Why only 7 days of forecast?"
Because Open-Meteo's free tier caps the daily forecast at sixteen days, and most people don't need more than a week. Seven fits the row nicely, too — no scrolling, no wrapping, one clean strip of the week ahead.

"Why doesn't the time update while the tab is open?"
Because the clock is only read at page load. Refreshing the tab re-reads it. It's a small choice — the alternative is a setInterval that ticks every second and drains battery for a number you'll only glance at anyway.

"The temperature is a few degrees off from what another app says."
Different services use different models, different grid resolutions, and different update schedules. Open-Meteo is one of the most accurate free APIs available, but it won't always agree with your phone's built-in weather app. When they disagree, trust the one you've been using longer.

"Can I change the temperature to Fahrenheit?"
Not through the interface. The API call hard-codes metric units. If you want Fahrenheit, open the file in a text editor and change &temperature_unit=fahrenheit — actually, that parameter isn't in the URL yet, so you'd add &temperature_unit=fahrenheit to the fetch URL near the top of the <script>. Wind speed and precipitation units can be changed the same way.

"Will my location be shared with anyone?"
Only with Open-Meteo and BigDataCloud, as coordinates, over HTTPS, for the sole purpose of fetching weather and a place name. Nothing is logged by Weather Glass itself — there is no Weather Glass server, and the file never writes your location to localStorage. Close the tab and the coordinates are gone.

"Can I install it as an app?"
Not as written. It isn't registered as a PWA — no service worker, no manifest. You can still bookmark it or add it to your home screen in most browsers, but it'll behave like a page, not an app. If you want the full installable experience, you'd need to add the manifest and service worker yourself.

"I want to change the fallback city."
Open the file, search for Kyiv, and replace the two occurrences of 50.4501, 30.5234, 'Kyiv, Ukraine' with the coordinates and name of whatever city you'd rather see. There are exactly two: one in the geolocation error handler and one in the commented-out timeout fallback.

---

<div align="center">

📞 A question, an idea, a bug?

https://img.shields.io/badge/Email-mohamed005cheikh@gmail.com-d14836?style=flat-square&logo=gmail&logoColor=white
https://img.shields.io/badge/WhatsApp-+222_30_73_64_75-25D366?style=flat-square&logo=whatsapp&logoColor=white
https://img.shields.io/badge/GitHub-mohamed005cheikh--rgb-181717?style=flat-square&logo=github

<br />

The sky, on your terms.

<sub>© 2026 Mohamed Cheikh — MC88</sub>

</div>