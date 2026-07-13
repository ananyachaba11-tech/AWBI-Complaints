# What Complaints to the Animal Welfare Board of India Reveal About the Stray-Dog Conflict

## Overview

**Story question:** What do complaints submitted to India’s national animal-welfare body reveal about the country’s stray-dog conflict?

**Why this matters:** Official discussions of the issue often rely on dog-bite, population and sterilisation data. Complaints to the Animal Welfare Board of India, or AWBI, provide a different administrative record: incidents reported as animal-welfare concerns.

**Findings:** The analysis found that most stray-dog-related complaints alleged harm toward dogs, their caregivers or both, rather than harm caused by dogs. Physical cruelty was the most commonly alleged form of harm, followed by the removal or relocation of dogs. Private individuals and organised resident groups were the actors most frequently named.

**Read the story:** https://ananyachaba11-tech.github.io/AWBI-Complaints/

---

## Project Goals

This project was an opportunity to:

- scrape data that was otherwise difficult to access and make it publically available;
- learn AI-assisted text classification;
- learn scraping with beautiful soup
- build and release a complete data story.

---

## Data Source

The data was scraped from the AWBI’s public [Cruelty Complaint portal](https://awbi.gov.in/Cruelty).

The portal displayed **1,156 complaints**, while the state-level tables returned **1,122 records**. The difference of 34 records may be connected to missing state IDs, which were required to retrieve the tables.

Of the records scraped:

- **785** were classified as dog-related;
- **492** were classified as stray-dog-related; and
- **34** were removed as exact duplicate complaint texts.

The main analysis focuses on **453 complaints submitted between 2023 and 2025**, as the 2026 data is incomplete.

---

## Data Collection and Cleaning

The state-level complaint tables were scraped using Python and Beautiful Soup.

The records were then:

1. combined into a national dataset;
2. cleaned and standardised;
3. classified by animal and dog type;
4. checked for exact duplicates; and
5. classified by complaint type, alleged harm and primary actor.

Exact duplicate complaint texts were removed after normalising whitespace and capitalisation.

Near-duplicates were not systematically removed. Similar wording may represent repeated submissions, related incidents or different people reporting the same conflict.

---

## AI Classification

AI was used to classify complaint text across four main dimensions:

- animal type;
- dog type;
- complaint type;
- type of harm; and
- primary actor.

A hand-coded sample was used to validate the classifications.

### Validation Accuracy

### Validation Accuracy

AI classifications were evaluated against a manually coded sample.

| Classification        | Accuracy |
| --------------------- | -------: |
| Animal type           |      98% |
| Dog type              |      96% |
| Complaint type        |      96% |
| Physical cruelty      |      96% |
| Removal or relocation |      92% |
| Institutional neglect |     100% |
| Vehicle collision     |      96% |
| Other harm            |     100% |
| Unclear harm          |      98% |
| Primary actor         |      94% |

Residual classification errors may remain.

---

## Complaint Categories

### Harm or threat to dogs

Alleged cruelty, neglect, removal, relocation, disappearance or threats directed toward stray dogs.

### Harm or threat to caregivers

Alleged harassment, abuse, intimidation or obstruction directed toward people feeding, rescuing or caring for stray dogs.

### Harm or threat to dogs and caregivers

Complaints that clearly alleged harm or threats toward both dogs and their caregivers.

### Harm, fear or nuisance caused by dogs

Complaints alleging bites, attacks, chasing, barking, danger, nuisance or fear caused by stray dogs.

### Harm arising from fear of dogs

Complaints alleging that dogs or caregivers were harmed, threatened or obstructed in response to dog bites, aggression or public-safety concerns.

---

## Harm Categories

A complaint could be assigned more than one harm category.

### Physical cruelty

Deliberate physical harm or an explicit threat of harm, including poisoning, beating, stabbing, burning or killing.

### Removal or relocation

Dogs allegedly captured, displaced, dumped, prevented from returning or threatened with removal.

### Institutional neglect

Unsafe conditions, neglect or improper care in shelters, ABC centres, veterinary facilities or institutional custody.

### Vehicle collision

Dogs allegedly injured or killed through accidental, careless or negligent driving.

### Other harm

A clearly alleged form of harm that did not fit the categories above.

---

## Primary Actor Categories

Each complaint was assigned one primary actor: the actor most directly alleged to have initiated, authorised or carried out the harm.

### Resident group or RWA

Resident welfare associations, housing societies or residents acting collectively.

### Individual

One or more private individuals acting personally rather than through an organisation.

### Government or public body

Municipal bodies, police, panchayats, government departments or officials acting in an official capacity.

### ABC centre, shelter or contractor

Organisations or staff involved in capture, sterilisation, treatment, shelter or animal care.

### Private institution or business

Schools, hospitals, builders, companies, shops or other private organisations.

### Unknown or unclear

Complaints that did not identify the actor clearly enough to classify.

---

## Repository Structure

```text
data_scraping_allstates.ipynb
    Scrapes complaint tables for each state and union territory.

national_dataset.ipynb
    Combines the state-level tables into one national dataset.

state_ids.csv
    Contains the state names and IDs required by the scraper.

ai_classification.ipynb
    Contains the prompts and code used to classify animal type, dog type and broad complaint type.

ai_classification_R2.ipynb
    Contains the prompts and code used to classify specific forms of harm to stray dogs and the primary actor named.

cleaning.ipynb
    Contains the data-cleaning, formatting and de-duplication workflow.

analysis.ipynb
    Contains the analysis and visualisation code.

national_scraped_dataset.csv
    Contains the complete dataset scraped from the AWBI portal.

national_with_ai_labels.csv
    Contains the complete scraped dataset with AI-generated classifications.

stray_dog_ai_labels.csv
    Contains the final stray-dog complaint dataset used for the analysis.
```

```

The `state_ids` dataset must be stored in the required folder before running the national scraping workflow.

---

## Reuse and Citation

The data was scraped from the AWBI’s publicly accessible complaint portal and is being released for public use.

Please cite this project if you reuse the cleaned dataset, methodology, analysis or code:

> Chaba, Ananya. _What Complaints to the Animal Welfare Board of India Reveal About the Stray-Dog Conflict_. 2026.

```
