# GEO project

**Which headphone brands do AI assistants recommend?**

More and more people ask AI assistants (ChatGPT, Gemini…) what to buy instead of searching on Google. **GEO
(Generative Engine Optimization)** is like SEO, but for AI answers: it is about helping a brand show up when AI
recommends products.

In this small project I tested this for noise-cancelling headphones in the UK.

## What I did

1. **Asked questions.** I wrote 30 shopping questions and asked them to Gemini. **26** of them don't mention any
   brand, for example *"Which noise-cancelling headphones are good for the London Underground?"*, so the AI chooses
   the brands itself. The other 4 compare two brands (for example *"Sony or Bose?"*), so I left them out of the
   results. All the numbers below come from the 26 brand-free questions.
2. **Counted the brands.** I saved the answers in a database and used SQL to count which brands appeared and which one
   was recommended first.
3. **Made a dashboard.** I made charts that show each brand's share and which brands win each type of question.
4. **Checked a product page.** I did a simple GEO check of Sennheiser's product page: can AI bots read it, and does it
   have numbers, a spec table, an FAQ and structured data?

## Results (23 Nov 2026)

![dashboard](dashboard.png)

### Which brands does the AI recommend?

| Brand | In how many answers | Share of all mentions | Recommended first |
|---|---|---|---|
| Sony | 100% | 24% | 62% |
| Bose | 96% | 23% | 27% |
| **Sennheiser** | **69%** | **16%** | **0%** |
| Apple | 62% | 15% | 12% |
| Anker Soundcore | 54% | 13% | 0% |

Sony and Bose are almost always in the answers. Sennheiser is in 3rd place: it shows up in 69% of the answers, but
the AI **never** recommended it first.

### Where is Sennheiser missing?

Sennheiser does well in general questions (100%) and budget questions (80%), but only appears in **38%** of
use-case questions. In these questions it was not mentioned at all:

| Question | Recommended first instead |
|---|---|
| Headphones for commuting on the London Underground | Bose |
| Headphones for working from home and video calls | Sony |
| Headphones for the gym and running | Sony |
| Headphones for people who wear glasses | Bose |
| Headphones with the best noise cancellation | Bose |

### Is Sennheiser's product page ready for AI?

The page scored **73 out of 100**.

What is good:
- AI bots are allowed to read the page
- It has a lot of numbers and facts (35)
- It has a short FAQ and a good title and description

What could be better:
- A lot of the page (68 sentences) only appears after JavaScript runs, so some AI bots may not see it
- The structured data is missing the brand, the rating and the reviews
- The specifications are not in a table

### What could Sennheiser do?

1. Write content for specific uses, such as commuting, work calls and travel.
2. Put the specifications in a simple table.
3. Make sure the important content is visible without JavaScript.

## Tools

| Tool | Used for |
|---|---|
| Python | the code |
| Google Colab | running the notebook |
| Gemini | answering the questions |
| DuckDB + SQL | storing the answers and counting the brands |
| pandas | tables |
| Plotly | charts |
| BeautifulSoup, Playwright | reading the product page |
| Google Sheets | saving the results (can be connected to Looker Studio) |

## How to run

1. Open `geo_project.ipynb` in [Google Colab](https://colab.research.google.com).
2. Click **Runtime → Run all**.
3. Wait about 10 minutes. The results are saved in Google Drive in the `geo-project` folder.

## Limitations

This is a small test: 26 questions, asked once, to one AI model, without web search. So the numbers are only
indicative. Next steps would be to ask more questions, repeat the test every week, and use real search data to choose
the questions.
