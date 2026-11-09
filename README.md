
# GAIC Translation Workshop 🌍

**Testing a provided English-to-French AI translation workshop using QVAC SDK and Bergamot**

A practical exercise completed during the November 2026 AI Bootcamp.

**Important:** The workshop files, translation script, and package configuration were supplied by the bootcamp instructors. My role was to set up and test the provided project, record results, verify translation output, investigate the SDK's model exports, and troubleshoot dependency warnings.

This repository documents my testing and learning, not an application developed from scratch.

## 1. Project Overview

The provided workshop application accepts an English sentence and returns its French translation using the **Bergamot** translation engine through the **QVAC SDK**.

Once the necessary model files have been downloaded, translation can run locally without sending the text to an online translation API.

### Objectives

- Install and run the Node.js translation project supplied by the instructors.
- Translate the default and custom English sentences into French.
- Record translation response times.
- Test whether translation works without an internet connection.
- Explore the Bergamot model identifiers available through the QVAC SDK.
- Identify and resolve npm dependency vulnerabilities.
- Document my practical results and learning experience.

## 2. Technologies Used

| Technology | Purpose |
| --- | --- |
| Node.js v22.21.0 | JavaScript runtime |
| JavaScript (.mjs) | Workshop scripts |
| QVAC SDK | Access to local AI capabilities |
| Bergamot | Neural machine translation engine |
| npm | Package installation and management |
| VS Code | Development environment |
| PowerShell | Running terminal commands |
| Git and GitHub | Version control and documentation |

### Understanding QVAC and Bergamot

**QVAC SDK** provides tools for working with local AI models.

**Bergamot** is a Neural Machine Translation (NMT) engine that translates text between languages using machine learning.

An interesting feature of Bergamot is that translation can run locally after the required models have been downloaded.

## 3. Project Files

```text
gaic-translation-workshop/
├── README.md
├── START-HERE.txt
├── translate.mjs
├── private-search.mjs
├── package.json
├── package-lock.json
├── SAVED-TRANSLATION.txt
├── SAVED-SEARCH.txt
└── TEST-RESULTS.txt
```

The workshop starter files and package configuration were provided for the exercise.

The main exercise documented in this README is the English-to-French translation using `translate.mjs`.

The `node_modules` folder is generated during installation and should not be uploaded to GitHub.

## 4. Setup and Installation

### Step 1: Check Node.js

The workshop used Node.js version 22.21.0.

```powershell
nvm use 22.21.0
node --version
```

Expected output:

```text
v22.21.0
```

### Step 2: Install Dependencies

```powershell
npm install
```

This installs the dependencies defined in the supplied `package.json` file.

### Step 3: Run the Default Translation

```powershell
npm run translate
```

### Step 4: Run a Custom Translation

```powershell
npm run translate -- "The meeting starts at 6 pm."
```

The first execution may download the translation model. Subsequent runs can use the locally available model.

## 5. Translation Test Results

The following results were recorded during my practical exercise.

| Test | English Input | French Output | Time |
| --- | --- | --- | --- |
| Default | The meeting starts at 5 pm. | La rencontre commence à 17 heures. | 459 ms |
| Custom Run 1 | The meeting starts at 6 pm. | La rencontre débute à 18h. | 554 ms |
| Custom Run 2 | The meeting starts at 6 pm. | La rencontre débute à 18h. | 543 ms |
| Custom Run 3 | The meeting starts at 6 pm. | La rencontre débute à 18h. | 548 ms |
| Offline Test | The meeting starts at 6 pm. | La rencontre débute à 18h. | 523 ms |

### Example Terminal Output

```text
English: The meeting starts at 6 pm.
French:  La rencontre débute à 18h.
Translation request: 548 ms
```

### Observations

- The translation completed successfully.
- The model returned consistent French translations for the custom sentence.
- The response times were below one second.
- The translation continued working after I disconnected from Wi-Fi.

These timings are from my computer and may differ on other devices.

## 6. Offline Translation Test

I wanted to find out whether the downloaded model could translate text without an internet connection.

### Test Procedure

1. Downloaded and ran the translation model successfully.
2. Turned off my Wi-Fi connection.
3. Ran the translation command again.
4. Checked the output and response time.

### Command Used

```powershell
npm run translate -- "The meeting starts at 6 pm."
```

### Result

```text
English: The meeting starts at 6 pm.
French:  La rencontre débute à 18h.
Translation request: 523 ms
```

**Outcome: Successful**

The translation worked without an internet connection, confirming that the downloaded model could perform this translation locally on my computer.

## 7. Translation Verification

Because I do not speak French, I decided to verify the translation rather than assume the AI-generated result was correct.

I used Google to check the French wording and meaning.

This helped me understand the importance of validating AI-generated outputs, particularly when working with languages I am not familiar with.

## 8. Exploring Bergamot Language Models

After completing the translation exercise, I became curious about the other languages available through Bergamot.

I ran the following command in my VS Code terminal:

```powershell
node --input-type=module -e "import * as sdk from '@qvac/sdk'; console.log(Object.keys(sdk).filter(k => k.includes('BERGAMOT')))"
```

### Model Identifiers Found in My Terminal

The following are the visible model identifiers returned by my installed QVAC SDK, with their corresponding language descriptions.

```text
BERGAMOT       - Bergamot engine
BERGAMOT_AR_EN - Arabic to English
BERGAMOT_AZ_EN - Azerbaijani to English
BERGAMOT_BE_EN - Belarusian to English
BERGAMOT_BG_EN - Bulgarian to English
BERGAMOT_BN_EN - Bengali to English
BERGAMOT_BS_EN - Bosnian to English
BERGAMOT_CA_EN - Catalan to English
BERGAMOT_CS_EN - Czech to English
BERGAMOT_DA_EN - Danish to English
BERGAMOT_DE_EN - German to English
BERGAMOT_EL_EN - Greek to English
BERGAMOT_EN_AR - English to Arabic
BERGAMOT_EN_AZ - English to Azerbaijani
BERGAMOT_EN_BG - English to Bulgarian
BERGAMOT_EN_BN - English to Bengali
BERGAMOT_EN_BS - English to Bosnian
BERGAMOT_EN_CA - English to Catalan
BERGAMOT_EN_CS - English to Czech
BERGAMOT_EN_DA - English to Danish
BERGAMOT_EN_DE - English to German
BERGAMOT_EN_EL - English to Greek
BERGAMOT_EN_ES - English to Spanish
BERGAMOT_EN_ET - English to Estonian
BERGAMOT_EN_FA - English to Persian
BERGAMOT_EN_FI - English to Finnish
BERGAMOT_EN_FR - English to French
BERGAMOT_EN_GU - English to Gujarati
BERGAMOT_EN_HE - English to Hebrew
BERGAMOT_EN_HI - English to Hindi
BERGAMOT_EN_HR - English to Croatian
BERGAMOT_EN_HU - English to Hungarian
BERGAMOT_EN_ID - English to Indonesian
BERGAMOT_EN_IS - English to Icelandic
BERGAMOT_EN_IT - English to Italian
BERGAMOT_EN_JA - English to Japanese
BERGAMOT_EN_KN - English to Kannada
BERGAMOT_EN_KO - English to Korean
BERGAMOT_EN_LT - English to Lithuanian
BERGAMOT_EN_LV - English to Latvian
BERGAMOT_EN_ML - English to Malayalam
BERGAMOT_EN_MS - English to Malay
BERGAMOT_EN_NB - English to Norwegian Bokmål
BERGAMOT_EN_NL - English to Dutch
BERGAMOT_EN_NO - English to Norwegian
BERGAMOT_EN_PL - English to Polish
BERGAMOT_EN_PT - English to Portuguese
BERGAMOT_EN_RO - English to Romanian
BERGAMOT_EN_RU - English to Russian
BERGAMOT_EN_SK - English to Slovak
BERGAMOT_EN_SL - English to Slovenian
BERGAMOT_EN_SQ - English to Albanian
BERGAMOT_EN_SR - English to Serbian
BERGAMOT_EN_SV - English to Swedish
BERGAMOT_EN_TA - English to Tamil
BERGAMOT_EN_TE - English to Telugu
BERGAMOT_EN_TH - English to Thai
BERGAMOT_EN_TR - English to Turkish
BERGAMOT_EN_UK - English to Ukrainian
BERGAMOT_EN_VI - English to Vietnamese
BERGAMOT_EN_ZH - English to Chinese
BERGAMOT_ES_EN - Spanish to English
BERGAMOT_ET_EN - Estonian to English
BERGAMOT_FA_EN - Persian to English
BERGAMOT_FI_EN - Finnish to English
BERGAMOT_FR_EN - French to English
BERGAMOT_GU_EN - Gujarati to English
BERGAMOT_HE_EN - Hebrew to English
BERGAMOT_HI_EN - Hindi to English
BERGAMOT_HR_EN - Croatian to English
BERGAMOT_HU_EN - Hungarian to English
BERGAMOT_ID_EN - Indonesian to English
BERGAMOT_IS_EN - Icelandic to English
BERGAMOT_IT_EN - Italian to English
BERGAMOT_JA_EN - Japanese to English
BERGAMOT_KN_EN - Kannada to English
BERGAMOT_KO_EN - Korean to English
BERGAMOT_LT_EN - Lithuanian to English
BERGAMOT_LV_EN - Latvian to English
BERGAMOT_ML_EN - Malayalam to English
BERGAMOT_MS_EN - Malay to English
BERGAMOT_MT_EN - Maltese to English
BERGAMOT_NB_EN - Norwegian Bokmål to English
BERGAMOT_NL_EN - Dutch to English
BERGAMOT_NN_EN - Norwegian Nynorsk to English
BERGAMOT_NO_EN - Norwegian to English
BERGAMOT_PL_EN - Polish to English
BERGAMOT_PT_EN - Portuguese to English
BERGAMOT_RO_EN - Romanian to English
BERGAMOT_RU_EN - Russian to English
BERGAMOT_SK_EN - Slovak to English
BERGAMOT_SL_EN - Slovenian to English
BERGAMOT_SQ_EN - Albanian to English
BERGAMOT_SR_EN - Serbian to English
BERGAMOT_SV_EN - Swedish to English
BERGAMOT_TA_EN - Tamil to English
BERGAMOT_TE_EN - Telugu to English
BERGAMOT_TH_EN - Thai to English
BERGAMOT_TR_EN - Turkish to English
BERGAMOT_UK_EN - Ukrainian to English
```

The terminal abbreviated the final two entries as `... 2 more items`, so they are not included above.

### My Observation

I was particularly interested in whether African languages such as isiZulu and Swahili were represented.

Neither appeared among the visible model identifiers.

This raised an interesting question for me about how local AI translation tools could be extended to support more African languages.

**Note:** These are model identifiers exported by the SDK. I did not download or test all these language models. My practical translation testing was limited to English and French.

## 9. npm Security Audit and Troubleshooting

During the initial installation, npm reported three high-severity vulnerabilities.

### Initial Result

```text
3 high severity vulnerabilities
```

The audit identified vulnerable versions of the `zod` dependency within the installed package tree.

### Troubleshooting

I first attempted to update Zod:

```powershell
npm install zod@4.6.7
```

However, the nested dependency warnings remained.

I then attempted to configure an npm override. My first attempt resulted in an `EOVERRIDE` conflict.

After investigating the error, I used:

```powershell
npm pkg set 'overrides.zod=$zod'
npm install
npm audit
```

### Final Result

```text
found 0 vulnerabilities
```

I then reran the translation exercise to confirm that it still worked after the dependency changes.

The translation completed successfully.

### What I Learned

- How to use `npm audit` to identify dependency vulnerabilities.
- Why updating a direct dependency may not resolve nested dependency warnings.
- How npm overrides can help resolve dependency version conflicts.
- Why it is important to test an application again after modifying dependencies.

## 10. Challenges Encountered

### Node.js Command Error

Initially, I entered:

```powershell
use 22.21.0
```

PowerShell did not recognise the command.

I corrected it by using:

```powershell
nvm use 22.21.0
```

### Dependency Vulnerabilities

The initial npm installation reported three high-severity vulnerabilities.

I investigated the dependency warnings, updated the configuration, and confirmed that the final audit reported zero vulnerabilities.

### Verifying French Translation

Because French is not a language I speak, I independently checked the translated output.

### Exploring Other Languages

I explored the SDK's exported Bergamot model identifiers to understand which language combinations were represented.

## 11. Key Learning Outcomes

This exercise helped me understand:

1. How a provided AI translation application runs using Node.js.
2. How the QVAC SDK and Bergamot work together.
3. How local AI models can perform tasks without a continuous internet connection.
4. How to record and compare translation response times.
5. Why AI-generated outputs should be verified.
6. How to explore the model identifiers exposed by an SDK.
7. How to troubleshoot npm dependency vulnerabilities.
8. How to document practical technical work using GitHub.

Although I am still developing my AI skills, this workshop encouraged me to explore beyond the basic translation task and understand more about the tools involved.

## 12. Future Exploration

As I continue learning AI, I would like to explore:

- Building my own translation interface using React.
- Allowing users to select different supported languages.
- Comparing translation speeds and accuracy across language models.
- Investigating local translation support for isiZulu and Swahili.
- Exploring how offline AI tools could benefit communities with limited internet connectivity.

These are future learning ideas and were not implemented as part of this workshop.

## 13. Author

**Sijabulile Ncube**

AI Bootcamp Participant  
Software Development and AI Learner

**GitHub:** [SIJABULILE-NCUBE](https://github.com/SIJABULILE-NCUBE)

## 14. Acknowledgements

This practical exercise was completed as part of the **GAIC AI Bootcamp, November 2026**.

Special thanks to the bootcamp instructors for providing the workshop materials, scripts, package configuration and learning opportunity.

The original workshop code and packages were provided by the instructors and their respective maintainers.

My contribution focused on installation, testing, verification, troubleshooting, exploration and documentation.

---

**Project Status:** Workshop testing completed successfully.

**Environment:** Windows, VS Code, PowerShell, Node.js v22.21.0, QVAC SDK and Bergamot.
