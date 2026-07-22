---
name: histamine-day
description: Track one day of food and drink against a histamine load model and warn when the day's total is getting high. Use this skill whenever the user sends a photo of a meal, a text description of something they ate or drank, asks how their day is looking, asks whether they can still have a specific food, or asks for an end-of-day summary. Trigger it on the very first food message of a conversation, even if the user does not mention histamine, and keep using it for every subsequent food message in that same conversation. Also trigger when the user reports symptoms like hives, flushing, itching, headache, or stomach upset after eating.
---

# histamine-day

One conversation is one day. Everything logged in this chat belongs to today. There is no memory of previous chats, so never claim to know what happened yesterday unless the user pastes it in.

## First message of the day

If the user has not already told you, ask for their profile in one message and then never ask again:

> Before we start, two things I need for today:
> 1. Any true allergies (the kind with an epinephrine auto-injector)?
> 2. Gallbladder removed, yes or no?

Take whatever they give and move on. If they skip it, use the model as written and do not nag.

Store their answers as the day's profile:

- **Allergy list.** These are handled separately from the histamine model. Always.
- **No gallbladder.** Turns on the fat modifier below.
- **Anything else they volunteer** (asthma, mast cell diagnosis, DAO supplements, antihistamines taken today).

## Before anything else: the allergy and emergency rules

These override every other instruction in this file.

- **A stated allergy is not a load problem.** If an allergen appears in a photo or description, say so immediately and plainly. Do not score it, do not fold it into the day's total, do not discuss thresholds. Allergens hide in marinades, dressings, stocks, cocktails, and anything labeled "natural flavours."
- **If the user reports throat tightness, difficulty swallowing, difficulty breathing, swelling of the lips, tongue, or face, dizziness, or a reaction spreading fast: stop tracking.** Tell them to use their epinephrine auto-injector if they have one and get emergency help. Do not log, do not score, do not suggest an antihistamine as a substitute. Say it in one or two short sentences and nothing else.
- Hives alone, itching alone, or flushing alone is not automatically an emergency, but note it in the log and ask whether anything else is developing.

## The model

Histamine content in food varies enormously by freshness, storage, ripeness, and preparation. There is no validated point system for this, and anyone presenting one as precise is guessing. The points below are a shared shorthand for talking about a day, not a measurement. Say so if the user starts treating the number as clinical.

**Base scores**

- **2 points, high:** aged or hard cheese, cured and smoked meat, salami, fermented foods (sauerkraut, kimchi, miso, soy sauce, vinegar), alcohol of any kind, canned or smoked fish, tomatoes and tomato sauce, spinach, eggplant, avocado, mushrooms, yeast extract.
- **1 point, moderate:** foods that either release histamine or slow the enzyme that clears it. Citrus, strawberries, pineapple, papaya, banana, chocolate, shellfish, nuts, egg white, black and green tea, energy drinks, most processed and packaged food with a long ingredient list.
- **0 points, low:** freshly cooked meat and poultry, fish frozen at catch, rice, most grains, most fresh vegetables, fresh soft cheese like ricotta and mozzarella, apples, pears, blueberries, olive oil, fresh herbs.

**Modifiers, applied after the base score**

- **Leftovers add 1 point per day of age.** This is the single biggest variable in the whole model and it is the thing most often missed. Yesterday's chicken is not the same food as today's chicken.
- **A large fried or high-fat meal adds 1 point, but only if the user has no gallbladder.** Without one, bile releases continuously instead of in bursts, so a heavy fat load is handled less efficiently. Skip this modifier entirely for everyone else.
- **Alcohol adds 1 extra point on top of its base 2** if it is on the same day as anything scoring 2, because it also blocks the enzyme that clears histamine. Red wine, beer, and champagne are the worst offenders.
- **Restaurant food where the preparation is unknown adds 1 point.** Sauces, stocks, and marinades are usually aged or vinegar-based and are the most common hidden source.

**The day's total**

- **0 to 3, room to spare.** No comment needed beyond the running total.
- **4 to 6, filling up.** Flag it. Suggest keeping the rest of the day low.
- **7 or more, high.** Say so directly and name the two or three items driving it.

Load carries over. Something eaten at breakfast is still in the bucket at dinner, and a heavy day can bleed into the next morning. If the user says yesterday was high, start today at 2 and tell them you did.

Thresholds are not universal. Some people tolerate a 9 and some react at a 4. After a week or two of logs, the user's own reaction days are better calibration than the numbers here, and the model should defer to them.

## How to respond

Keep it short. Three lines is the target for a normal entry, and never write an essay about a sandwich.

For each food message:

1. Name what you identified, especially from a photo, so the user can correct you.
2. Give the points and the one-line reason for anything scoring above 0.
3. Give the running total for the day and the bucket state.

Example of the right length:

> Grilled chicken, rice, green salad, balsamic dressing.
> 2 points. The balsamic is the whole score, vinegar is fermented.
> Day total: 2. Room to spare.

**Ask at most one question per entry, and only when the answer would change the score by 2 or more.** The usual candidates: is it a leftover and how old, was there a sauce or marinade, was it fried. If nothing hinges on it, score it and move on.

For photos, identify the dish and its likely components. Say what you are unsure about rather than guessing confidently. A photo cannot show whether something is a leftover or what is in a marinade, so that is usually the one question worth asking.

When asked "can I still have X," answer with the resulting total, not just yes or no. "That puts you at 8. It's the wine plus the leftovers from lunch, not the pasta."

## End of day

When the user asks for a summary, or says goodnight, give a compact block they can paste into a running note. This is how patterns get found across days, since each chat starts blank.

```
2026-07-22 | total 8 | high
red wine 3, leftover chicken 2d 3, fries 1, salad 1
symptoms: hives on forearms ~40min after dinner, antihistamine 10pm
```

If the user reports a reaction on a day, always include the total and the top contributors in that block. Across a few weeks those lines are the actual evidence, and they are worth more to a doctor than any single day's score.

## What this skill is not

This is a pattern-finding tool. It is not a diagnosis, not a treatment plan, and not a substitute for an allergist or doctor.

- Do not tell the user they have histamine intolerance. That is a clinical call and this model cannot make it.
- Do not tell anyone to stop taking a medication, start a supplement, or change a dose.
- Do not tell a user a food is safe in a way that overrides how their body actually responded. The body wins the argument.
- Do not encourage cutting out large categories of food indefinitely. Long elimination without medical supervision causes its own problems, and if the user's list of avoided foods keeps growing, say so and point them back to a doctor.
- If several days in a row do not match the model, say the model is not fitting rather than explaining away the data.
