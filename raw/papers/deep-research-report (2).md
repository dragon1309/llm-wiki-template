# Do deep research on brainstorming daily-life questions a 5-year-old would ask as Gemini Storybook prompts

## Executive summary

This report provides a **structured prompt bank** of daily-life questions that fit the **cognitive and language profile of many 5‑year‑olds**, designed to be used as **Gemini Storybook prompts**. It includes: a brief developmental rationale; a taxonomy of categories; **12 child‑phrased questions per category** (144 total), each paired with a **1–2 sentence Gemini Storybook prompt template** (kid‑friendly/educational, ~60–120 seconds, with visual cues); a **prioritized list of 30 evergreen starter questions** (with suggested formats); batching guidance for efficient production; safety/legal flags (COPPA, sensitive topics, medical/legal advice); a parental review checklist; a CSV export schema example; and an appendix of prompt patterns plus 10 fully written prompts.

Several operating details are **unspecified**: target country, language variants, and production budget. This report assumes **English** prompts and a broadly “global” everyday-life context. If you target a specific region (e.g., Vietnam/SEA), the question bank can be localized (terminology, routines, school norms) without changing the core taxonomy.

Safety-wise, kids content on YouTube is governed by **child safety rules** and YouTube Kids eligibility constraints; YouTube Kids excludes deceptive/clickbait packaging and restricts commercial content (including paid product placements) and expects age-appropriate handling of sensitive topics. citeturn7view0turn4view1 COPPA compliance and “made for kids” determinations rely on factors such as subject matter and emphasis on kids’ characters/themes. citeturn4view3turn6search3turn4view2

## Developmental rationale for question phrasing at age five

Many 5‑year‑olds can sustain **multi‑turn conversation**, **tell simple multi‑event stories**, and **answer simple questions about a story**, and they increasingly use “why/how” reasoning and time words like “yesterday/tomorrow.” citeturn2view1 That aligns with prompts that are (a) **short**, (b) **single‑concept**, and (c) structured as a mini‑story with one clear cause‑and‑effect explanation and a recap.

The entity["organization","Centers for Disease Control and Prevention","us public health agency"] also notes typical attention spans in this stage: many children can pay attention around **5–10 minutes** during activities like story time (with the explicit note that “screen time does not count”). citeturn2view1 Practically, this supports using **60–120 second episodes** (and even shorter “micro” cuts) with **interactive beats** (e.g., “pause and guess,” “try it with me”) rather than extended explanation.

The entity["organization","American Academy of Pediatrics","pediatrics professional org"] describes many 4–5 year-olds as using **four‑word sentences**, being understandable to strangers, recalling parts of stories, counting 10 objects, and engaging in imaginative play—skills that map well to storybook formats and daily-life “why” questions. citeturn2view0

From a nurturing-care framing, entity["organization","UNICEF","un children's fund"] emphasizes early development needs like responsive caregiving (talking, singing, playing) and opportunities for early learning in safe environments—useful as a tone benchmark: warm, calm, and supportive rather than fear-based. citeturn6search5turn6search1

Because digital media and ads are part of children’s everyday context, AAP resources encourage families to focus on **quality, context, and conversation** and to talk about ads and privacy in age‑appropriate ways—important to how you handle “technology & screens” questions. citeturn5view0turn5view1

## Taxonomy of daily-life question categories and prompt bank

### How to read and use the tables

- **Child questions** are written in **simple, child-like phrasing** (1–8 words) so you can paste directly into prompts or titles.
- **Safety flags** identify questions likely to require **parental framing**, especially for health symptoms, online safety, or high‑risk imitation topics.
- **Gemini prompt templates** are intentionally short and consistent: *kid-friendly/educational*, **~60–120 seconds**, with clear **visual cues** for reuse.

Safety flag legend:
- `ok` = generally safe for kids with ordinary care
- `review_medical` = symptoms/medical care; avoid diagnosis; include “ask a trusted adult”
- `review_online` = privacy, security, ads; emphasize “ask a grown-up”
- `review_sensitive` = grief, intense fear, family conflict; focus on coping, reassurance
- `review_imitation` = hazards (fireworks/matches/unsafe stunts); do not demonstrate; emphasize safety

### Taxonomy categories

Body & health; Family & feelings; Nature & science; Food & cooking; Routines & hygiene; School & learning; Play & toys; Safety & rules; Social & manners; Technology & screens; Weather & seasons; Animals & pets.

### Body & health

| id | category | child_question | safety_flag | gemini_prompt_template | episode_length_suggestion | shared_assets_tags |
|---|---|---|---|---|---|---|
| BH-01 | body_health | Why do I need sleep | ok | Create a kid‑friendly educational 60–120s story: a 5‑year‑old asks “Why do I need sleep”; show bedtime routine, “brain rest” visual, and morning energy payoff; end with one simple recap. | short | bedroom, night_sky, routine_chart |
| BH-02 | body_health | Why do I sneeze | ok | Make a 60–120s storybook where the child wonders “Why do I sneeze”; show dust/pollen icons, a “nose guard” metaphor, and “cover your sneeze” practice; recap with a safe habit. | short | home_livingroom, tissue, germ_icons |
| BH-03 | body_health | Why do I cough | ok | Generate a 60–120s gentle explanation story: “Why do I cough”; show throat/lungs simple diagram, “tickle” trigger icons, and covering cough with elbow; end with recap. | short | home_livingroom, simple_body_diagram, hygiene |
| BH-04 | body_health | Why do I have bones | ok | Create a storybook: “Why do I have bones”; show skeleton-as-frame metaphor, bending vs strong support visuals, and movement play; recap one sentence. | short | simple_body_diagram, playground, movement |
| BH-05 | body_health | Why does my heart beat | ok | Write a kid‑safe story: “Why does my heart beat”; show calm vs running heartbeat, simple heart pump metaphor, and listening with hand on chest; recap. | short | park, running, heart_icon |
| BH-06 | body_health | Why do I get hiccups | ok | Create a playful 60–120s story: “Why do I get hiccups”; show diaphragm “oops” metaphor, sipping water calmly, and breathing slow; recap. | short | kitchen, water_cup, simple_diagram |
| BH-07 | body_health | Why do my teeth wiggle | ok | Make a kid‑friendly story: “Why do my teeth wiggle”; show baby teeth vs grown‑up teeth visual, tooth fairy optional (neutral), and gentle brushing; recap. | short | bathroom, toothbrush, tooth_icons |
| BH-08 | body_health | Why do I have a belly button | ok | Create a calm story: “Why do I have a belly button”; show baby umbilical cord metaphor (simple, non-graphic), family photo cue, and body kindness message; recap. | short | home_bedroom, family_photos, simple_diagram |
| BH-09 | body_health | Why do I cry | review_sensitive | Write a 60–120s supportive story: “Why do I cry”; show feelings meter, comfort strategies (hug, breathe, talk), and a positive resolution; include “talk to a grown‑up” line; recap. | short | feelings_icons, home_livingroom, calming |
| BH-10 | body_health | Why does my tummy hurt | review_medical | Create a gentle storybook: “Why does my tummy hurt”; show common safe causes (hungry, too fast, worry) as icons, comfort steps, and clear “tell a grown‑up/pediatrician if it hurts”; recap. | short | home_kitchen, feelings_icons, adult_help |
| BH-11 | body_health | What is a fever | review_medical | Generate a calm story: “What is a fever”; show thermometer icon, resting and drinking water visuals, and explicitly say “a grown‑up decides medicine”; no dosing; recap. | short | bedroom, thermometer_icon, adult_help |
| BH-12 | body_health | Why do I need shots | review_medical | Write a reassuring story: “Why do I need shots”; show “body shield” metaphor, bravery coping steps, and parent comfort; avoid procedure detail; recap. | short | clinic_simple, bravery_badge, adult_help |

### Family & feelings

| id | category | child_question | safety_flag | gemini_prompt_template | episode_length_suggestion | shared_assets_tags |
|---|---|---|---|---|---|---|
| FF-01 | family_feelings | Why do parents work | ok | Create a 60–120s story: child asks “Why do parents work”; show job helping people, earning for home needs, and family time after work; recap with reassurance. | short | home_kitchen, workplace_icons, family_dinner |
| FF-02 | family_feelings | Why do grown ups say no | ok | Make a storybook: “Why do grown ups say no”; show safety boundary examples, choice alternatives, and calm explanation; recap. | short | home_livingroom, rule_icons, calming |
| FF-03 | family_feelings | Why do I have chores | ok | Generate a kid‑friendly story: “Why do I have chores”; show teamwork at home, simple tasks, and pride badge; recap. | short | home_kitchen, laundry, teamwork |
| FF-04 | family_feelings | Why do we share | ok | Create a 60–120s story: “Why do we share”; show toy conflict, taking turns timer, happy repair; recap. | short | playroom, timer_icon, friendship |
| FF-05 | family_feelings | Why do we say sorry | ok | Write a gentle story: “Why do we say sorry”; show mistake, apology steps (say, fix, hug), and friendship repair; recap. | short | home_livingroom, apology_steps, friendship |
| FF-06 | family_feelings | Why do I feel mad | ok | Generate a story: “Why do I feel mad”; show feelings thermometer, safe calming tools (breathe, words), and problem solving; recap. | short | feelings_icons, calming, home |
| FF-07 | family_feelings | Why do I feel scared | review_sensitive | Make a reassuring story: “Why do I feel scared”; show “alarm system” metaphor, comfort plan, and adult support; avoid scary imagery; recap. | short | bedroom_night, cozy_light, adult_help |
| FF-08 | family_feelings | Why do people hug | ok | Create a storybook: “Why do people hug”; show consent-friendly options (ask first, high‑five), warmth and care; recap. | short | family_home, consent_icons, friendship |
| FF-09 | family_feelings | Why do people laugh | ok | Write a playful story: “Why do people laugh”; show funny surprise, shared joy, and kindness humor (no teasing); recap. | short | park, silly_faces, friendship |
| FF-10 | family_feelings | Why do grown ups argue | review_sensitive | Create a calm story: “Why do grown ups argue”; show disagreement vs unkindness, repair with talking, and reassurance child is safe; recap and “talk to a trusted adult.” | short | home_livingroom, calm_talk, reassurance |
| FF-11 | family_feelings | Why do people die | review_sensitive | Generate an age‑appropriate sensitive story: “Why do people die”; focus on feelings, memories, and support from adults; avoid graphic detail; end with coping and “talk to a grown‑up.” | short | memory_photos, comfort_routine, adult_help |
| FF-12 | family_feelings | Why do I miss you | ok | Create a warm storybook: “Why do I miss you”; show separation (school/work), connection rituals, and reunion; recap. | short | school_dropoff, heart_icons, family_reunion |

### Nature & science

| id | category | child_question | safety_flag | gemini_prompt_template | episode_length_suggestion | shared_assets_tags |
|---|---|---|---|---|---|---|
| NS-01 | nature_science | Why is the sky blue | ok | Create a 60–120s story: “Why is the sky blue”; show sunlight + air “scatter” as simple color-sprinkle metaphor; recap. | short | outdoor_sky, sunlight_icon, color_sprinkles |
| NS-02 | nature_science | Where does rain come from | ok | Generate a storybook: “Where does rain come from”; show water cycle icons (evaporate/cloud/rain), umbrella scene, recap. | short | sky_clouds, water_cycle_icons, umbrella |
| NS-03 | nature_science | Why do shadows move | ok | Make a kid-friendly story: “Why do shadows move”; show flashlight experiment, sun moving, shadow chase; recap safety (adult help for flashlight). | short | livingroom, flashlight, shadow_shapes |
| NS-04 | nature_science | What is wind | ok | Create a 60–120s story: “What is wind”; show moving air with ribbons/kites, trees swaying, recap. | short | park, kite, ribbon_icons |
| NS-05 | nature_science | Why does ice melt | ok | Generate a story: “Why does ice melt”; show warm vs cold, puddle forming, simple temperature meter; recap. | short | kitchen, ice_cube, temp_icons |
| NS-06 | nature_science | Why do magnets stick | ok | Write a storybook: “Why do magnets stick”; show magnet picking clips, invisible pull lines, recap. | short | desk, magnet, paperclips |
| NS-07 | nature_science | Why do things float | ok | Create a story: “Why do things float”; show boat vs rock in tub, “push back” water metaphor, recap with supervision note. | short | bathroom_tub, boat_toy, water_icons |
| NS-08 | nature_science | Why do plants grow | ok | Generate a gentle story: “Why do plants grow”; show seed, water/sun icons, time-lapse style, recap. | short | garden, seed, sun_water_icons |
| NS-09 | nature_science | Where does the sun go | ok | Create a 60–120s story: “Where does the sun go”; show Earth turning as a simple spinning ball, sunset, recap. | short | sky_sunset, globe_icon, day_night |
| NS-10 | nature_science | Why is water wet | ok | Make a playful story: “Why is water wet”; show droplets sticking, towel absorption, simple sensory comparison; recap. | short | bathroom, water_drops, towel |
| NS-11 | nature_science | Why do fireworks boom | review_imitation | Create an age‑appropriate story: “Why do fireworks boom”; explain sound/light at a distance; do **not** show making fireworks; include “only adults, safe places”; recap. | short | night_sky, safe_distance, sound_light_icons |
| NS-12 | nature_science | Why does soap make bubbles | ok | Generate a storybook: “Why does soap make bubbles”; show bubble wand, soap “skin” metaphor, recap. | short | sink, bubbles, soap_icons |

### Food & cooking

| id | category | child_question | safety_flag | gemini_prompt_template | episode_length_suggestion | shared_assets_tags |
|---|---|---|---|---|---|---|
| FC-01 | food_cooking | Why do we cook food | ok | Create a 60–120s story: “Why do we cook food”; show warm food taste, softness, and safety (adult kitchen rules); recap. | short | kitchen, stove_icon, safety_rules |
| FC-02 | food_cooking | Why is soup hot | review_imitation | Generate a story: “Why is soup hot”; show heat steam icon, waiting to cool, “blow and sip” safely; include adult warning; recap. | short | kitchen, steam_icons, cool_down |
| FC-03 | food_cooking | Why do we eat breakfast | ok | Create a storybook: “Why do we eat breakfast”; show morning energy meter, school playtime, recap. | short | kitchen_morning, energy_meter, school |
| FC-04 | food_cooking | Why do onions make me cry | ok | Make a playful story: “Why do onions make me cry”; show onion “tiny smell clouds,” tears, and safe coping (adult cuts, step back); recap. | short | kitchen, onion_icon, tear_drop |
| FC-05 | food_cooking | Why do we wash fruit | ok | Generate a story: “Why do we wash fruit”; show dirt/germs icons washing away, drying towel, recap. | short | kitchen_sink, fruit_bowl, hygiene_icons |
| FC-06 | food_cooking | Where does honey come from | ok | Create a storybook: “Where does honey come from”; show bees, flowers, honeycomb icons, recap (bee safety: don’t swat). | short | garden, bees_flowers, honeycomb |
| FC-07 | food_cooking | What makes popcorn pop | review_imitation | Generate a story: “What makes popcorn pop”; show kernel + heat “steam pop,” adult cooking rule, recap; no microwave instructions for kids. | short | kitchen, popcorn_icons, adult_help |
| FC-08 | food_cooking | Why do we need water | ok | Create a 60–120s story: “Why do we need water”; show body water drop icons, playtime thirst, refill bottle, recap. | short | home, water_bottle, body_icons |
| FC-09 | food_cooking | Why is spicy spicy | ok | Make a gentle story: “Why is spicy spicy”; show tongue “tiny heat sparks,” milk/yogurt comfort icon (ask adult), recap. | short | kitchen, spice_icons, calm_drink |
| FC-10 | food_cooking | Why can’t I eat candy | ok | Generate a story: “Why can’t I eat candy”; show teeth/sugar bugs metaphor, balance plate, treat sometimes; recap. | short | kitchen, tooth_icons, balance_plate |
| FC-11 | food_cooking | Why does bread rise | ok | Create a storybook: “Why does bread rise”; show yeast “tiny balloon makers,” dough puffing, recap. | short | kitchen, bread_dough, balloon_icons |
| FC-12 | food_cooking | Why does milk spoil | review_medical | Generate a story: “Why does milk spoil”; show “tiny germs” icon growing over time, fridge cold slows, “ask adult before tasting”; recap. | short | kitchen, fridge_icon, time_icons |

### Routines & hygiene

| id | category | child_question | safety_flag | gemini_prompt_template | episode_length_suggestion | shared_assets_tags |
|---|---|---|---|---|---|---|
| RH-01 | routines_hygiene | Why do we wash hands | ok | Create a 60–120s routine story: “Why do we wash hands”; show germs icon, sink steps, and “before eating/after toilet”; recap. | short | bathroom_sink, soap, step_icons |
| RH-02 | routines_hygiene | Why do we brush teeth | ok | Generate a storybook: “Why do we brush teeth”; show sugar bugs, brushing timer, dentist smile icon; recap. | short | bathroom, toothbrush, timer |
| RH-03 | routines_hygiene | Why do we take baths | ok | Create a gentle story: “Why do we take baths”; show sweat/dirt icons washing away and feeling fresh; recap. | short | bathtub, bubbles, towel |
| RH-04 | routines_hygiene | Why do we use soap | ok | Generate a story: “Why do we use soap”; show soap breaking up “sticky dirt,” bubbles, rinse; recap. | short | sink, soap_icons, bubbles |
| RH-05 | routines_hygiene | Why do we wear clean clothes | ok | Make a storybook: “Why do we wear clean clothes”; show comfort, germs, laundry basket; recap. | short | bedroom, laundry, cleanliness |
| RH-06 | routines_hygiene | Why do we cut nails | review_imitation | Create a safe story: “Why do we cut nails”; show dirt under nails, adult clipping only, handwashing; recap. | short | bathroom, nail_icons, adult_help |
| RH-07 | routines_hygiene | Why do we comb hair | ok | Generate a story: “Why do we comb hair”; show tangles vs smooth, gentle brushing, recap. | short | bedroom, brush, mirror |
| RH-08 | routines_hygiene | Why do we cover coughs | ok | Make a story: “Why do we cover coughs”; show sneeze/cough cloud, elbow cover, tissues; recap. | short | school, hygiene_icons, tissues |
| RH-09 | routines_hygiene | Why do we go to bed | ok | Create a bedtime story: “Why do we go to bed”; show body recharge battery, growth, morning ready; recap. | short | bedroom_night, battery_icon, stars |
| RH-10 | routines_hygiene | Why do we wear shoes | ok | Generate a story: “Why do we wear shoes”; show feet protection, hot ground/sharp objects icon (non-graphic), recap. | short | outdoor_sidewalk, shoes, safety_icons |
| RH-11 | routines_hygiene | Why do we use sunscreen | ok | Make a storybook: “Why do we use sunscreen”; show sun rays, skin shield icon, hat/shade; recap. | short | park_sunny, sun_icon, hat_shade |
| RH-12 | routines_hygiene | Why do I need potty rules | ok | Generate a gentle routine story: “Why do I need potty rules”; show bathroom steps and privacy/cleanliness, recap. | short | bathroom, routine_steps, privacy_icons |

### School & learning

| id | category | child_question | safety_flag | gemini_prompt_template | episode_length_suggestion | shared_assets_tags |
|---|---|---|---|---|---|---|
| SL-01 | school_learning | Why do I go to school | ok | Create a story: “Why do I go to school”; show learning new things, friends, and trying skills; recap. | short | classroom, friends, books |
| SL-02 | school_learning | Why do we raise hands | ok | Generate a storybook: “Why do we raise hands”; show taking turns, listening, classroom calm; recap. | short | classroom, hand_raise, turn_taking |
| SL-03 | school_learning | Why do we line up | ok | Make a story: “Why do we line up”; show moving safely, fairness, teacher guidance; recap. | short | school_hall, line_icons, safety |
| SL-04 | school_learning | Why do we read books | ok | Create a storybook: “Why do we read books”; show imagination, learning words, cozy reading; recap. | short | library_corner, books, imagination |
| SL-05 | school_learning | How do letters make words | ok | Generate a story: “How do letters make words”; show letter blocks building a word, sound bubbles, recap. | short | classroom, letter_blocks, sound_icons |
| SL-06 | school_learning | Why do numbers matter | ok | Make a story: “Why do numbers matter”; show counting snacks, steps, and time; recap. | short | classroom, counting, time_icons |
| SL-07 | school_learning | Why do we take turns | ok | Create a storybook: “Why do we take turns”; show game sharing, timer, fairness; recap. | short | playground, timer_icon, fairness |
| SL-08 | school_learning | Why do we follow rules | ok | Generate a story: “Why do we follow rules”; show safety and kindness, clear examples, recap. | short | classroom, rule_icons, kindness |
| SL-09 | school_learning | Why do we sit still | ok | Make a story: “Why do we sit still”; show listening body, short wiggle break, teacher cue; recap. | short | classroom, calm_body, wiggle_break |
| SL-10 | school_learning | Why do we share crayons | ok | Create a storybook: “Why do we share crayons”; show art time, sharing tray, teamwork; recap. | short | art_table, crayons, teamwork |
| SL-11 | school_learning | Why do we ask questions | ok | Generate a story: “Why do we ask questions”; show “curiosity key” metaphor and learning; recap. | short | classroom, key_icon, curiosity |
| SL-12 | school_learning | Why do we practice | ok | Make a story: “Why do we practice”; show learning a skill over tries, encouragement, recap. | short | classroom, progress_steps, cheer_icons |

### Play & toys

| id | category | child_question | safety_flag | gemini_prompt_template | episode_length_suggestion | shared_assets_tags |
|---|---|---|---|---|---|---|
| PT-01 | play_toys | Why do we play | ok | Create a storybook: “Why do we play”; show learning skills, joy, friends; recap. | short | playground, laughter, skill_icons |
| PT-02 | play_toys | Why do bubbles pop | ok | Generate a playful story: “Why do bubbles pop”; show bubble thin skin, touch, pop sparkle; recap. | short | backyard, bubbles, sparkle_icons |
| PT-03 | play_toys | Why do balls bounce | ok | Make a story: “Why do balls bounce”; show squish-and-spring metaphor, different balls, recap. | short | park, balls, spring_icons |
| PT-04 | play_toys | Why do toys break | ok | Create a gentle story: “Why do toys break”; show wear and tear, fix/repair, caring for things; recap. | short | playroom, repair_tape, care_icons |
| PT-05 | play_toys | Why do puzzles fit | ok | Generate a story: “Why do puzzles fit”; show shapes matching, patience, recap. | short | table, puzzle, shape_icons |
| PT-06 | play_toys | Why do we pretend | ok | Make a story: “Why do we pretend”; show imagination, trying roles safely, recap. | short | playroom, costume_hat, imagination |
| PT-07 | play_toys | Why do swings swing | ok | Create a storybook: “Why do swings swing”; show push and back-and-forth motion, safety holding on; recap. | short | playground, swing, motion_arrows |
| PT-08 | play_toys | Why do we build blocks | ok | Generate a story: “Why do we build blocks”; show balance, creativity, teamwork; recap. | short | playroom, blocks, balance_icons |
| PT-09 | play_toys | Why do I get bored | ok | Make a story: “Why do I get bored”; show brain wanting new challenge, choice menu, recap. | short | home, choice_icons, activity_cards |
| PT-10 | play_toys | Why do we lose games | ok | Create a storybook: “Why do we lose games”; show learning, sportsmanship, trying again; recap. | short | boardgame, sportsmanship, try_again |
| PT-11 | play_toys | Why do wheels roll | ok | Generate a story: “Why do wheels roll”; show round shape moving, toy car, recap. | short | sidewalk, toy_car, shape_icons |
| PT-12 | play_toys | Why do we play together | ok | Make a story: “Why do we play together”; show sharing ideas, friendship, kindness; recap. | short | playground, friends, teamwork |

### Safety & rules

| id | category | child_question | safety_flag | gemini_prompt_template | episode_length_suggestion | shared_assets_tags |
|---|---|---|---|---|---|---|
| SR-01 | safety_rules | Why can’t I run inside | ok | Create a story: “Why can’t I run inside”; show slipping hazards (non-graphic), walking feet rule, recap. | short | home_hallway, safety_icons, walking_feet |
| SR-02 | safety_rules | Why do we look both ways | ok | Generate a storybook: “Why do we look both ways”; show street crossing, cars, hand-holding; recap. | short | crosswalk, traffic_icons, hand_hold |
| SR-03 | safety_rules | Why do I wear a helmet | ok | Make a story: “Why do I wear a helmet”; show head protection shield, bike ride, recap. | short | sidewalk, helmet, safety_shield |
| SR-04 | safety_rules | Why can’t I touch stove | review_imitation | Create a safe story: “Why can’t I touch stove”; show heat danger with icons only, adult rules, safe distance; recap. | short | kitchen, heat_icons, adult_help |
| SR-05 | safety_rules | Why do we buckle seatbelts | ok | Generate a storybook: “Why do we buckle seatbelts”; show car stop, seatbelt hug metaphor, recap. | short | car_interior, seatbelt_icon, safety |
| SR-06 | safety_rules | Why do we hold hands outside | ok | Create a story: “Why do we hold hands outside”; show busy places, staying together, recap. | short | street, crowd_icons, hand_hold |
| SR-07 | safety_rules | Why can’t I play with matches | review_imitation | Make a strict safety story: “Why can’t I play with matches”; do not show lighting; show danger symbols, “only adults,” and safe alternatives; recap. | short | safety_icons, stop_sign, adult_only |
| SR-08 | safety_rules | Why can’t I swim alone | review_imitation | Create a storybook: “Why can’t I swim alone”; show water safety icons, buddy rule, adult supervision; recap. | short | pool, lifejacket_icon, adult_help |
| SR-09 | safety_rules | Why do we call 911 | review_sensitive | Generate a gentle story: “Why do we call 911”; show emergency concept via icons, emphasize “ask a grown-up,” no dramatized panic; recap. | short | phone_icon, calm_help, adult_help |
| SR-10 | safety_rules | Why can’t I take medicine | review_medical | Create a story: “Why can’t I take medicine”; show medicine as “grown-up only,” safe storage, and telling an adult; recap. | short | bathroom_cabinet, lock_icon, adult_help |
| SR-11 | safety_rules | Why can’t I climb high | ok | Generate a safety story: “Why can’t I climb high”; show safe playground rules, holding rails, adult guidance; recap. | short | playground, height_icons, safety |
| SR-12 | safety_rules | Why can’t I talk to strangers | review_online | Create a child-safe story: “Why can’t I talk to strangers”; show “safe adult list,” staying with caregivers, asking permission; recap. | short | park, safe_adult_icons, caregiver |

### Social & manners

| id | category | child_question | safety_flag | gemini_prompt_template | episode_length_suggestion | shared_assets_tags |
|---|---|---|---|---|---|---|
| SM-01 | social_manners | Why say please | ok | Create a storybook: “Why say please”; show asking kindly, helper smiles, recap. | short | home_kitchen, kindness_icons, speech_bubbles |
| SM-02 | social_manners | Why say thank you | ok | Generate a story: “Why say thank you”; show gratitude loop, happy feelings, recap. | short | school, gratitude_icons, smile_faces |
| SM-03 | social_manners | Why do we wait | ok | Make a story: “Why do we wait”; show line, patience tools, recap. | short | store_line, timer_icon, patience |
| SM-04 | social_manners | Why do we take turns | ok | Create a story: “Why do we take turns”; show game sharing, fairness heart, recap. | short | playground, fairness_icons, turn_taking |
| SM-05 | social_manners | Why do we listen | ok | Generate a story: “Why do we listen”; show listening ears icon, better understanding, recap. | short | classroom, ear_icon, calm |
| SM-06 | social_manners | Why do we knock | ok | Make a storybook: “Why do we knock”; show privacy, manners, recap. | short | home_door, privacy_icons, knock_sound |
| SM-07 | social_manners | Why do we whisper | ok | Create a story: “Why do we whisper”; show library or resting baby context, volume meter, recap. | short | library, volume_meter, quiet_icons |
| SM-08 | social_manners | Why can’t I grab | ok | Generate a story: “Why can’t I grab”; show asking first, sharing, recap. | short | playroom, ask_icon, sharing |
| SM-09 | social_manners | Why do we greet people | ok | Make a storybook: “Why do we greet people”; show hello wave, making friends, recap. | short | school_entry, wave_icon, friendship |
| SM-10 | social_manners | Why do we use inside voice | ok | Create a story: “Why inside voice”; show volume meter, classroom/home, recap. | short | classroom, volume_meter, calm |
| SM-11 | social_manners | Why do we help others | ok | Generate a story: “Why do we help others”; show kindness acts, community, recap. | short | park, help_icons, kindness |
| SM-12 | social_manners | Why do we share snacks | ok | Make a story: “Why share snacks”; show asking permission, allergy-safe generic mention, fairness, recap. | short | lunch_table, sharing, kindness |

### Technology & screens

These prompts should follow AAP-aligned principles: emphasize **content quality**, **co‑use with caregivers**, and talking about ads/privacy at a child-appropriate level. citeturn5view0turn5view1

| id | category | child_question | safety_flag | gemini_prompt_template | episode_length_suggestion | shared_assets_tags |
|---|---|---|---|---|---|---|
| TS-01 | tech_screens | Why do screens glow | ok | Create a 60–120s story: “Why do screens glow”; show pixels as tiny lights, dim/bright slider, recap with “ask a grown‑up for screen rules.” | short | livingroom, screen_icon, light_dots |
| TS-02 | tech_screens | Why can’t I watch forever | ok | Generate a storybook: “Why can’t I watch forever”; show body needing play/sleep, timer, fun offline swap; recap. | short | home, timer_icon, outdoor_play |
| TS-03 | tech_screens | Why do videos keep playing | ok | Make a story: “Why do videos keep playing”; show autoplay concept as “next button,” and parent rule to pause and choose; recap. | short | tablet_icon, pause_button, caregiver |
| TS-04 | tech_screens | Why do ads show up | review_online | Create a simple story: “Why do ads show up”; show “this is an advertisement” label, explain selling vs learning, and “ask a grown‑up before clicking”; recap. | short | screen_icon, ad_label, caregiver |
| TS-05 | tech_screens | Why do we need passwords | review_online | Generate a kid-safe story: “Why passwords”; show “secret key” metaphor, never share with strangers, ask adult; no technical detail; recap. | short | lock_icon, key_icon, caregiver |
| TS-06 | tech_screens | Why can’t I click everything | review_online | Make a storybook: “Why can’t I click everything”; show safe vs unsafe buttons, asking permission, recap. | short | screen_icon, stop_sign, caregiver |
| TS-07 | tech_screens | What is an app | ok | Create a story: “What is an app”; show apps as “tiny tools,” examples (drawing, music), and ask adult to choose; recap. | short | app_icons, toolbox, caregiver |
| TS-08 | tech_screens | Why do phones ring | ok | Generate a storybook: “Why do phones ring”; show call as “talking far away,” polite phone manners, recap. | short | phone_icon, wave_icon, manners |
| TS-09 | tech_screens | Why do we take screen breaks | ok | Create a story: “Why screen breaks”; show eyes blinking, stretch break, water sip, recap. | short | stretch_icons, water_cup, timer |
| TS-10 | tech_screens | Why do we ask permission online | review_online | Make a storybook: “Why ask permission online”; show trusted adult check, privacy lock icons, recap. | short | lock_icon, caregiver, safe_rules |
| TS-11 | tech_screens | What is Wi Fi | review_online | Create a kid-friendly story: “What is Wi‑Fi”; show invisible air-paths, devices connecting, and privacy rule “don’t share info”; recap. | short | wifi_icon, invisible_lines, caregiver |
| TS-12 | tech_screens | Why do games have rules | ok | Generate a story: “Why games have rules”; show fairness, turn-taking, recap. | short | game_board, fairness_icons, rules |

### Weather & seasons

| id | category | child_question | safety_flag | gemini_prompt_template | episode_length_suggestion | shared_assets_tags |
|---|---|---|---|---|---|---|
| WS-01 | weather_seasons | Why does it rain | ok | Create a storybook: “Why does it rain”; show clouds holding water, raining, puddles, recap. | short | sky_clouds, umbrella, water_cycle |
| WS-02 | weather_seasons | Why is it windy | ok | Generate a story: “Why is it windy”; show moving air ribbons, trees swaying, kite, recap. | short | park, ribbon_icons, kite |
| WS-03 | weather_seasons | Why is it hot | ok | Create a story: “Why is it hot”; show sun rays, shade/hat, hydration, recap. | short | sunny_park, sun_icon, water |
| WS-04 | weather_seasons | Why is it cold | ok | Make a storybook: “Why is it cold”; show clouds/season icons, warm clothes, hot drink with adult, recap. | short | winter_icons, scarf_hat, warm_home |
| WS-05 | weather_seasons | Why do we have seasons | ok | Generate a story: “Why seasons”; show Earth tilt with simple globe, seasonal clothes icons, recap. | short | globe_icon, seasonal_icons, calendar |
| WS-06 | weather_seasons | Why do leaves fall | ok | Create a storybook: “Why do leaves fall”; show tree resting, wind, leaf pile play; recap. | short | park_trees, leaf_icons, seasons |
| WS-07 | weather_seasons | Why do leaves change color | ok | Make a story: “Why leaves change color”; show green food in leaves, autumn change visuals, recap. | short | park_trees, color_change, seasons |
| WS-08 | weather_seasons | Why does thunder boom | ok | Generate a gentle story: “Why thunder boom”; show lightning + sound delay, cozy safety (stay indoors), recap. | short | storm_icons, cozy_blanket, safety |
| WS-09 | weather_seasons | Why is there a rainbow | ok | Create a storybook: “Why rainbow”; show sun + rain droplets prism, simple arc, recap. | short | sky_rain, sun_icon, rainbow |
| WS-10 | weather_seasons | Where do clouds go | ok | Generate a story: “Where do clouds go”; show wind moving clouds and changing shapes, recap. | short | sky_clouds, wind_arrows, shapes |
| WS-11 | weather_seasons | Why do we need umbrellas | ok | Create a storybook: “Why umbrellas”; show staying dry, raincoat alternatives, recap. | short | rainy_street, umbrella, puddles |
| WS-12 | weather_seasons | Why does the sky get dark | ok | Make a story: “Why sky gets dark”; show sunset and Earth turning metaphor, bedtime cue, recap. | short | sunset, globe_icon, bedtime |

### Animals & pets

| id | category | child_question | safety_flag | gemini_prompt_template | episode_length_suggestion | shared_assets_tags |
|---|---|---|---|---|---|---|
| AP-01 | animals_pets | Why do dogs bark | ok | Create a storybook: “Why dogs bark”; show dog communication icons (alert/play), calm response, recap. | short | home, dog_icons, feelings |
| AP-02 | animals_pets | Why does Mochi wag | ok | Generate a story: “Why Mochi wags”; show happy tail, greeting and play cues, recap. | short | home, pet_mochi, wag_icons |
| AP-03 | animals_pets | Why do cats purr | ok | Make a storybook: “Why cats purr”; show comfort/hello, gentle petting, recap “ask before touching animals.” | short | pet_icons, gentle_hands, consent |
| AP-04 | animals_pets | Why do birds fly | ok | Create a story: “Why birds fly”; show wings and air lift as simple metaphor, nest, recap. | short | park_sky, birds, wing_icons |
| AP-05 | animals_pets | Why do fish swim | ok | Generate a storybook: “Why fish swim”; show fins pushing water, school of fish, recap. | short | aquarium_icons, water_arrows, fins |
| AP-06 | animals_pets | Why do bugs crawl | ok | Make a story: “Why bugs crawl”; show tiny legs, exploring for food, recap. | short | garden, bug_icons, legs |
| AP-07 | animals_pets | Why do we feed pets | ok | Create a story: “Why feed pets”; show food, water, routine chart, recap responsibility. | short | kitchen, pet_bowl, routine_chart |
| AP-08 | animals_pets | Why do pets need shots | review_medical | Generate a gentle story: “Why pets need shots”; show “health shield” metaphor, vet visit calm, adult responsibility, recap. | short | vet_clinic_simple, shield_icon, adult_help |
| AP-09 | animals_pets | Why do pets sleep a lot | ok | Create a storybook: “Why pets sleep a lot”; show energy recharge, play then rest, recap. | short | home, pet_bed, battery_icon |
| AP-10 | animals_pets | Why do animals have tails | ok | Make a story: “Why animals have tails”; show balance, communication, swish; recap. | short | park, animal_icons, balance |
| AP-11 | animals_pets | Why do mosquitoes bite | review_medical | Generate a story: “Why mosquitoes bite”; explain “they look for food” simply, show safe prevention (long sleeves, ask adult for repellent), avoid medical advice; recap. | short | outdoor_evening, bug_icons, adult_help |
| AP-12 | animals_pets | Why do bees buzz | ok | Create a storybook: “Why bees buzz”; show wings and flower work, safety “stay calm,” recap. | short | garden_flowers, bee_icons, calm |

## Evergreen starter slate and batching strategy

### Prioritized starter list of 30 evergreen questions with format suggestions

Interpretation note: you asked for “30 evergreen questions for first 6–8 episodes.” The most practical approach is a **30‑question runway**, with the first **8** labeled as **Launch (P0)** and the remaining **22** as **Early (P1)** for continuity.

| priority | category | child_question | episode_format | shared_assets_tags | notes |
|---|---|---|---|---|---|
| P0 | routines_hygiene | Why do we wash hands | short | bathroom_sink, soap, step_icons | Core evergreen routine |
| P0 | family_feelings | Why do parents work | standard | kitchen, workplace_icons, family_dinner | Strong emotional hook |
| P0 | school_learning | Why do we raise hands | short | classroom, turn_taking, hand_raise | Classroom norms |
| P0 | social_manners | Why say please | micro | home, kindness_icons, speech_bubbles | Easy to animate |
| P0 | nature_science | Where does rain come from | short | sky_clouds, water_cycle_icons | Classic “why” |
| P0 | play_toys | Why do bubbles pop | micro | bubbles, backyard | High visual payoff |
| P0 | animals_pets | Why do dogs bark | short | pet_icons, home | Pet relatability |
| P0 | body_health | Why do I need sleep | standard | bedroom_night, routine_chart | Bedtime episodes perform well |
| P1 | routines_hygiene | Why do we brush teeth | short | bathroom, toothbrush, timer | Repeatable |
| P1 | family_feelings | Why do we say sorry | short | home, apology_steps | Prosocial skill |
| P1 | nature_science | Why do shadows move | short | flashlight, shadow_shapes | Simple experiment visuals |
| P1 | weather_seasons | Why is it windy | micro | park, kite, ribbons | Reuse park |
| P1 | school_learning | Why do we line up | micro | school_hall, line_icons | Easy staging |
| P1 | food_cooking | Why do we wash fruit | micro | kitchen_sink, fruit_bowl | Reuse kitchen |
| P1 | food_cooking | Why can’t I eat candy | short | tooth_icons, balance_plate | Gentle health framing |
| P1 | tech_screens | Why can’t I watch forever | short | timer_icon, outdoor_play | Avoid moralizing |
| P1 | tech_screens | Why do videos keep playing | micro | pause_button, caregiver | Autoplay explained |
| P1 | safety_rules | Why do we look both ways | short | crosswalk, traffic_icons | Safety evergreen |
| P1 | safety_rules | Why do we buckle seatbelts | micro | car_interior, seatbelt_icon | Very reusable |
| P1 | nature_science | Why does ice melt | micro | kitchen, ice_cube | Simple concept |
| P1 | animals_pets | Why does Mochi wag | micro | pet_mochi, wag_icons | Character branding |
| P1 | play_toys | Why do balls bounce | micro | park, balls, spring_icons | Motion-friendly |
| P1 | social_manners | Why say thank you | micro | school, gratitude_icons | Fast |
| P1 | family_feelings | Why do I feel mad | short | feelings_icons, calming | Socio-emotional |
| P1 | family_feelings | Why do I miss you | short | school_dropoff, heart_icons | Separation routine |
| P1 | nature_science | Why is the sky blue | short | outdoor_sky, sunlight_icon | Classic |
| P1 | weather_seasons | Why is there a rainbow | micro | rain + sun icons | A+ visuals |
| P1 | school_learning | Why do we read books | standard | library_corner, imagination | Reinforce literacy |
| P1 | play_toys | Why do we pretend | short | costume_hat, imagination | Fits storybook |
| P1 | routines_hygiene | Why do we cover coughs | micro | hygiene_icons, tissues | Seasonal evergreen |

### Batch production guidance: how to group prompts efficiently

A high-efficiency production plan for storybook-style videos is to batch by **shared backgrounds** and **shared props**, while keeping The Little Explorers cast constant.

1. **Lock a small background library**: kitchen, bedroom, bathroom sink, classroom, park, street/crosswalk. This supports reuse across >60% of the question bank.
2. **Create a “prop kit”**: toothbrush, soap, tissue, timer icon, umbrella, flashlight, book, toy blocks, pet bowl, seatbelt icon, feelings meter.
3. **Schedule by environment blocks**:
   - **Home block** (kitchen/bedroom/bathroom): hygiene, food, bedtime, feelings.
   - **School block** (classroom/hall): learning, manners, turn-taking.
   - **Outdoor block** (park/sky/street): weather, nature, safety.
4. **Reuse narrative beats** aligned with CDC developmental patterns: short story + two “why/how” questions + recap (children at this age can answer simple questions about a story and sustain back-and-forth exchanges). citeturn2view1
5. **Use AAP media guidance as a content principle** for tech topics: show “ask a grown‑up,” avoid ad-heavy framing, and model calm stopping points. citeturn5view0turn5view1

## Safety and legal flags with parental review checklist

### COPPA and “made for kids” implications for prompt choices

If your channel is directed to children, COPPA-related guidance becomes relevant to how you structure engagement and avoid eliciting personal information; the entity["organization","Federal Trade Commission","us consumer protection agency"] provides COPPA compliance guidance and factors for child-directed determination. citeturn4view2turn4view4 On entity["company","YouTube","video platform"], “made for kids” classification uses COPPA-derived factors (e.g., subject matter, emphasis on kids’ characters/themes), and “made for kids” content has different platform behaviors and restrictions. citeturn6search3turn4view3

### YouTube Kids constraints that affect question selection and packaging

entity["organization","YouTube Kids","kids video app"] eligibility is filtered, and YouTube Kids policies explicitly disallow deceptive/sensational/clickbait content and restrict commercial content like paid product placement/endorsements (with removal from YouTube Kids if disclosed through Studio). citeturn7view0 YouTube’s child safety policy prohibits “misleading family content” that mixes kids packaging with mature themes (including medical procedures, self-harm, adult horror characters) and addresses dangerous acts minors could imitate. citeturn4view1

### Parental review checklist for flagged questions

Use this checklist to decide whether a question should be labeled `review_*`:

| Review trigger | Why it’s flagged | Safer editorial approach |
|---|---|---|
| Symptoms/medical care (fever, tummy pain, medicine) | Risk of implying diagnosis or dosage advice; YouTube rules also treat some medical procedures as sensitive in family content contexts. citeturn4view1 | Use general comfort steps (rest, water), and add “tell a trusted adult/pediatrician”; avoid medication/dosing. |
| Dangerous imitation risk (matches, fireworks, stove, swimming alone) | YouTube child safety rules address dangerous acts that could be imitated. citeturn4view1 | Use icons/metaphors, no demonstration, explicit “only adults / with supervision.” |
| Online privacy/ads/passwords | COPPA context + marketing influence; AAP encourages talking about privacy and ads in age-appropriate ways. citeturn5view1turn5view0 | “Ask a grown‑up” rule, no tutorials, no calls to click links. |
| Sensitive topics (death, grief, intense fear, family arguments) | YouTube Kids allows sensitive topics only if age-appropriate and focused on coping; avoid extreme sadness/fear. citeturn7view0 | Soft tone, reassurance, coping strategies, encourage adult conversation. |
| Commercial framing | YouTube Kids restricts paid product placements/endorsements and overly commercial content. citeturn7view0 | Keep brand-neutral props and avoid “buy this” language. |

## CSV export schema and prompt appendix

### Export-ready CSV structure example

Below is a minimal **CSV schema** you can paste into a spreadsheet and scale to the full 144-row bank.

```csv
id,category,child_question,gemini_prompt_template,safety_flag,episode_length_suggestion,shared_assets_tags
BH-01,body_health,Why do I need sleep,"Create a kid-friendly educational 60–120s story: a 5-year-old asks 'Why do I need sleep'; show bedtime routine, brain-rest visuals, morning energy; end with 1-sentence recap.",ok,short,"bedroom|night_sky|routine_chart"
TS-04,tech_screens,Why do ads show up,"Create a simple 60–120s story: explain ads as 'someone trying to sell'; show ad label icon; include 'ask a grown-up before clicking'; end with recap.",review_online,short,"screen_icon|ad_label|caregiver"
SR-07,safety_rules,Why can’t I play with matches,"Create a strict-safety 60–120s story: do not show lighting; use danger icons, adult-only rule, safe alternatives; end with recap.",review_imitation,short,"safety_icons|stop_sign|adult_only"
```

### Gemini Storybook prompt phrasing patterns

Use these patterns to keep outputs consistent:

1. **Story-first**: “Create a 60–120s storybook episode: child asks ‘[Q]’; show a small problem, a helpful adult explanation, and a practice step; end with recap.”
2. **Explain-first**: “Create a kid-friendly explanation story: start with a simple ‘big idea’ sentence; then 3 scenes; end with ‘Remember: [one line].’”
3. **Routine coach**: “Show a routine with 3 steps (icons); include one ‘try it with me’ beat; end with praise and recap.”
4. **Feelings coach**: “Name the feeling, show the body clue, show 2 coping tools, show repair/reconnection; end with reassurance.”

### Ten sample fully written Gemini prompts ready to paste

```text
1) (Routines) Create a kid-friendly educational storybook episode (~60–120 seconds). A 5-year-old asks: “Why do we wash hands?” Use a bathroom sink scene, show tiny “germ” icons washing away with soap, and end with a simple recap plus one safe habit: “wash before eating.”

2) (Family) Create a warm storybook episode (~60–120 seconds). A child asks: “Why do parents work?” Show three scenes: parent helping people at work (generic), family buying groceries, and family time at home. End with reassurance and a one-sentence recap.

3) (School) Create a calm classroom storybook episode (~60–120 seconds). The child asks: “Why do we raise hands?” Show taking turns, listening, and a teacher praising good waiting. End with a short recap: “Hands help everyone get a turn.”

4) (Nature) Create a bright outdoor storybook episode (~60–120 seconds). The child asks: “Where does rain come from?” Show a simple water-cycle visual (sun warms water → clouds → rain), then puddles and umbrellas. End with a one-line recap.

5) (Body) Create a gentle bedtime storybook episode (~60–120 seconds). The child asks: “Why do I need sleep?” Show a “battery recharge” metaphor, growth/rest visuals, and waking up ready to play. End with a recap and a calm bedtime tip.

6) (Feelings) Create a supportive storybook episode (~60–120 seconds). The child asks: “Why do I feel mad?” Show a feelings meter, two calming tools (slow breaths, words), and a repair moment (saying sorry / finding a fair plan). End with a recap: “Feelings are okay—what we do matters.”

7) (Safety) Create a child-safe storybook episode (~60–120 seconds). The child asks: “Why do we look both ways?” Show a crosswalk, cars stopping, and holding hands with a caregiver. End with a recap and a safety rule.

8) (Tech) Create an age-appropriate storybook episode (~60–120 seconds). The child asks: “Why can’t I watch forever?” Show a timer, eyes needing a break, and a fun swap to outdoor play or reading. End with a recap and “ask a grown-up” message.

9) (Food) Create a cheerful kitchen storybook episode (~60–120 seconds). The child asks: “Why can’t I eat candy?” Show sugar “bugs” near teeth, a balanced snack plate, and “sometimes treats” with boundaries. End with a recap about balance.

10) (Pets) Create a cozy home storybook episode (~60–120 seconds). The child asks: “Why does Mochi wag?” Show wagging as “happy hello,” gentle petting, and a simple pet-care routine. End with a recap about reading pet feelings.
```

