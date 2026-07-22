# histamine-day

A Claude skill for tracking a day's histamine load from photos or text.

New chat = new day. Send a photo of your dinner, get back what it scored and where your day is sitting. At the end of the day it hands you a one-line summary you can paste into a running note.

Built after nine years of unexplained hives and a lot of emergency rooms. Full story: https://x.com/JimmyNewclaw/status/2079961596361658533?s=20

## Why not an app

Because the tracking part was never the hard bit. The hard bit was noticing that a Tuesday with leftovers and red wine looked different from a Tuesday without. A chat window already does photos, already does text, and doesn't need an account.

## Install

1. Download `SKILL.md` from this repo.
2. In Claude, go to Settings, then Capabilities, then Skills, and upload it.
3. Start a new chat and send a photo of a meal.

That's it. There's nothing to configure.

## How it works

Foods get a rough score:

| Score | What |
|---|---|
| 2 | Aged cheese, cured meat, fermented anything, vinegar, alcohol, canned fish, tomatoes, spinach, eggplant, avocado, mushrooms |
| 1 | Citrus, strawberries, pineapple, chocolate, shellfish, nuts, egg white, tea, most heavily processed food |
| 0 | Fresh meat cooked today, fish frozen at catch, rice, grains, most fresh vegetables, fresh soft cheese, apples, pears, blueberries |

Then modifiers, which matter more than the base score:

- **Leftovers: +1 per day of age.** The biggest variable in the whole thing. Histamine accumulates in food as it sits. Yesterday's chicken is not the same food as today's chicken.
- **Big fried or fatty meal: +1, only if you have no gallbladder.** Bile releases continuously instead of in bursts, so a heavy fat load gets handled less efficiently.
- **Alcohol: +1 on top of its base 2** on any day that already has a 2 in it. It also slows the enzyme that clears histamine.
- **Restaurant food with unknown prep: +1.** Sauces, stocks, and marinades are usually aged or vinegar-based and are the most common hidden source.

Day totals: 0 to 3 is room to spare, 4 to 6 is filling up, 7 or more is high.

## The numbers are made up

Not a joke, and worth saying plainly. Histamine content in food varies enormously by freshness, storage, ripeness, and how it was cooked. There is no validated point system for any of this. The scores here are a shared shorthand for talking about a day, nothing more.

The useful output isn't the number. It's the paste-able end-of-day line. After a few weeks of those, your own reaction days tell you where your threshold actually sits, which is worth more than anything in the table above.

## Not medical advice

This is a note-taking tool. It does not diagnose anything, it can't tell you whether you have histamine intolerance, and it should not be used to decide anything about medication. If your list of avoided foods keeps growing, that's a reason to see a doctor, not a reason to keep logging.

If you have a true allergy, tell it at the start of the chat. Allergens get flagged and excluded from the scoring entirely, because an allergy is a different mechanism and a load model has nothing useful to say about it.

## Contributing

If you know more about this than I do, which is likely, open an issue. Corrections to the food tiers are especially welcome.

## License

MIT
