# Symptom Knowledge Base — Literature Review

This is the clinical literature behind the symptom knowledge base used in the
augmentation stage (`notebooks/01_create_synthetic_profiles.ipynb`, Stage C–D)
to inject realistic, guideline-consistent subjective symptoms into each
profile before note generation.

Symptoms are organized below by the **infection category actually used for
classification** in this project (`Bloodstream/Sepsis`, `Respiratory`,
`Skin/Soft tissue`, `Urinary`, `Other/Mixed`). An earlier draft of this
literature review explored a finer-grained category split (separating out
Surgical Site Infection and *C. difficile* colitis); those two are folded
into **Other/Mixed** below, since the code does not classify them as their
own categories.

## Respiratory (Hospital-Acquired / Ventilator-Associated / Aspiration Pneumonia)

Clinical definition: a new pulmonary infiltrate on imaging together with
infectious signs — new fever, purulent sputum, leukocytosis, and worsening
oxygenation. One historical cohort found fever in 82% of patients, cough in
85%, dyspnea in 72%, and chest pain in 46%.

Patient-reported symptoms: cough, sputum production, dyspnea, tachypnea,
chest pain, fever, and chills.

- CDC/Merck — Hospital-Acquired Pneumonia: https://www.merckmanuals.com/professional/pulmonary-disorders/pneumonia/hospital-acquired-pneumonia
  "Symptoms may include cough, expectoration, a rise in body temperature, chest pain, or dyspnea. Signs include fever, tachypnea, consolidations, or crackles."
- StatPearls — Nosocomial Pneumonia: https://www.ncbi.nlm.nih.gov/books/NBK535441/
  "Symptoms and signs of hospital-acquired pneumonia in nonintubated patients are generally the same as those for community-acquired pneumonia and include malaise, fever, chills, rigor, cough, dyspnea, and chest pain."

## Urinary (UTI / CAUTI)

CDC defines the common symptoms as: burning or pain in the lower abdomen,
fever, burning on urination, and increased urinary frequency. NHSN criteria
for CAUTI include fever (>38°C), suprapubic pain, costovertebral angle
tenderness, frequency, urgency, and dysuria. The literature emphasizes that
in elderly patients, altered mental status is sometimes the first sign.
Important caveat: in catheterized patients, some lower urinary symptoms are
non-specific (direct catheter irritation) — fever, flank pain, suprapubic
tenderness, and confusion are the more informative signs in that population.

- CDC — CAUTI Basics: https://www.cdc.gov/uti/about/cauti-basics.html
  "Burning or pain below the stomach, fever, burning while peeing, peeing more frequently than usual."
- IDSA CAUTI review (PMC): https://pmc.ncbi.nlm.nih.gov/articles/PMC8992741/
  "Signs and symptoms of UTI may include increased bladder sensation, urgency, frequency, dysuria, pain in the urinary tract, suprapubic tenderness, fever, rigors, altered mental status, malaise, lethargy with no other identified cause, flank pain, and/or costovertebral angle tenderness."

## Bloodstream/Sepsis (Bloodstream Infection / CLABSI / Sepsis)

Fever and chills are the most common presentation. In CLABSI specifically,
there may be redness, swelling, tenderness, or purulent discharge around
the catheter insertion site. On progression to sepsis: tachycardia,
hypotension, tachypnea, confusion, and marked weakness. The literature notes
that in immunocompromised and elderly patients, symptoms may be "masked,"
presenting only as altered mental status or generalized weakness.

- CDC — CLABSI Basics: https://www.cdc.gov/clabsi/about/index.html
  "Fever, red skin and soreness around the central line."
- Cleveland Clinic — CLABSI: https://my.clevelandclinic.org/health/diseases/clabsi
  "Fever, chills, redness or darker skin around the catheter insertion site, pain, soreness or swelling around the insertion site, discharge from the insertion site, trouble drawing blood, poor blood flow."

## Skin/Soft tissue (Cellulitis / Abscess)

StatPearls defines cellulitis as an acute, spreading infection characterized
by erythema, local warmth, swelling, and tenderness. The skin may appear
tight and shiny; an abscess presents as a tender, fluctuant, edematous mass
of pus. With systemic involvement: fever, chills, sweats, and body aches.

- StatPearls — Cellulitis: https://www.ncbi.nlm.nih.gov/books/NBK549770/
  "This condition presents with worsening erythema, edema, warmth, and tenderness. Two of the 4 criteria (warmth, erythema, edema, or tenderness) are required to make the diagnosis."
- Cleveland Clinic — Cellulitis: https://my.clevelandclinic.org/health/diseases/15071-cellulitis
  "Pain, tenderness, edema (swelling), warmth, discoloration (red, purple or slightly darker than your usual skin color) that may look like a rash, fluid-filled blisters, skin surface looks lumpy or pitted, like an orange skin, fever, chills, fatigue."

## Other/Mixed

Categories that don't map to their own class in this project's classification
scheme, but were part of the original literature review and inform the
general "infection" symptom pool used for less common or mixed presentations:

### Surgical Site Infection (SSI)

CDC: redness and pain at the surgical site, cloudy/purulent discharge from
the incision, and fever. NHSN criteria for superficial SSI include purulent
drainage from the incision, or at least one of: pain/tenderness, localized
swelling, redness, or local warmth. Johns Hopkins additionally notes delayed
healing and wound dehiscence. Thick, purulent discharge — yellow, green, or
brown, sometimes foul-smelling — is a strong indicator.

- CDC — SSI Basics: https://www.cdc.gov/surgical-site-infections/about/index.html
  "Redness and pain around the area where you had surgery, cloudy fluid draining from your surgical wound, fever."
- Cleveland Clinic — Surgical Wound Infection: https://my.clevelandclinic.org/health/diseases/surgical-wound-infection
  "Thick, cloudy, white- or cream-colored discharge from the wound, noticeable odor from the incision, an opening in the incision line (the line may get deeper, longer or wider), redness or color changes in your skin that go beyond the edge of the incision, pain when you touch the wound or the area around the wound, the incision area feels warm or hot to your touch, fever (greater than 101°F / 38.4°C), chills, sweating."

### C. difficile / Infectious Colitis

The most common and earliest sign is frequent watery diarrhea (≥3 loose
stools per day), typically following antibiotic use. Accompanied by
abdominal cramping/pain, characteristic stool odor, fever, nausea, and loss
of appetite. Vomiting is uncommon in CDI. In severe cases: blood/pus in the
stool and signs of dehydration. The literature notes this is one of the most
common nosocomial infections overall.

- StatPearls — CDI: https://www.ncbi.nlm.nih.gov/books/NBK431054/
  "Common symptoms associated with diarrhea and colitis caused by C difficile include watery diarrhea with mucus or occult blood, anorexia, nausea, vomiting, low-grade fever, and lower abdominal pain. In some cases, patients may progress to fulminant colitis, characterized by diarrhea, diffuse abdominal pain, abdominal distension, hypovolemia, toxic megacolon, and perforated bowel with peritonitis."
- Cleveland Clinic — C. diff: https://my.clevelandclinic.org/health/diseases/15548-c-diff-infection
  "Persistent abdominal pain, swollen, distended abdomen, nausea and vomiting, loss of appetite, fever, rapid heart rate."

## Limitations worth documenting

- **Community-acquired vs. nosocomial:** an ICD code alone does not
  distinguish an infection acquired in the hospital from one already present
  on admission. Some codes are nosocomial by definition (VAP, CAUTI, CLABSI,
  SSI, post-procedural infection), but a "plain" UTI/pneumonia/sepsis code
  could be either. Recommended approach: cross-reference culture timing
  (`charttime` > 48 hours after `admittime`) together with device presence
  (catheter/ventilator/central line).
- **Symptoms are a plausible pool, not a certainty:** not every patient
  experiences every symptom associated with their infection category. The
  Ollama prompt is designed to sample a realistic subset (roughly 2–5
  symptoms) and scale them to severity (e.g., mild sepsis vs. septic shock),
  rather than listing every possible symptom for every note.
