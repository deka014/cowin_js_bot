# COWIN Bot
A script to help you book your vaccine slot faster

Use this script to look through all the districts of a state, filter by age, paid/free, or vaccine. This script can also solve the captcha and book the appointment for you! It does not honor specific date preferences yet.

# Demo
https://user-images.githubusercontent.com/1567686/118029491-d758b480-b381-11eb-8413-f69efcbdea6d.mp4

# Steps
* Go to the COWIN website: https://selfregistration.cowin.gov.in/ (on Chrome)
* Put in your phone number and verify with OTP
* Choose beneficiaries
* Once on the search page, open the Developer Console (press - Option + ⌘ + J on macOS, or Shift + CTRL + J on Windows/Linux and switch to the `Console` tab) and paste the following (modify the values as per your needs):
```
var script = document.createElement('script');script.src = "https://cowin-bot.s3-eu-west-1.amazonaws.com/main.js";document.getElementsByTagName('head')[0].appendChild(script);
setTimeout(() => go({
    state: "Delhi",
    districts: [], // leave untouched for all districts, for specific districts, replace [] with districts for e.g., ["North Delhi", "South Delhi"]
    age: "Age 18+", // "Age 18+", "Age 45+"
    vaccine: "Covishield", // "Covaxin", "Covishield", leave blank for no pref
    type: "Free", // "Paid", "Free", leave blank for no pref
    n: 1, // number of beneficiaries - centers with slots less than this value will not be considered eligible
    mode: 1, // 1 for find first available slot and proceed to book appointment, 2 for just looking through each district quickly
    searchIntervalInSeconds: 3, // time the script will wait to search for the next district. Use lower value with mode 1. Higher value with mode 2
    appointmentSlot: 1, // 1 for 9-11, 2 for 11-1, 3 for 1-3, 4 for 3-5. Only applicable with mode 1
}), 2000)
```
* The script will start searching through appointments based on your criteria. If you've selected mode 1, as soon as an eligible appointment is found, the script chooses
the slot, moves to the next page and chooses the time slot and books the appointment for you!

# Contributions
Fork away or send in pull requests!
