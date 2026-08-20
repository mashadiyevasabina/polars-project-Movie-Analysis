# 🎬 Movie Ratings & User Behavior Analysis with Polars

This project focuses on the cleaning, transformation, and business-oriented exploratory data analysis (EDA) of a large-scale movie ratings dataset using the **Polars** library. By leveraging high-performance DataFrames, key aspects such as user behavior, movie popularity, and genre engagement were thoroughly analyzed.

---

## 🛠️ Technologies & Tools

| Category | Technology / Library |
| :--- | :--- |
| **Language** | `Python 3.x` |
| **Data Processing** | `Polars` |
| **Environment** | `Google Colab` / `Jupyter Notebook` |
| **Dataset** | MovieLens (`Movies`, `Ratings`, `Tags`) |

---

## 📁 Dataset Overview

The project is built on 3 main relational tables:

* 🎬 **`movies.csv`** — Unique movie IDs (`movieid`), titles (`title`), and associated genres (`genres`).
* ⭐ **`ratings.csv`** — User ratings (`rating`) ranging from 0.5 to 5.0 assigned by users (`userid`), along with timestamps (`timestamp`).
* 🏷️ **`tags.csv`** — User-applied keywords (`tag`) assigned to movies and their creation times (`tag_timestamp`).

---

## 🧹 Data Cleaning & Preprocessing

Capitalizing on the performance advantages of Polars, the following pipeline steps were executed:

* 🔠 **Column Name Standardization:** Converted all column names across tables to lowercase (`to_lowercase()`).
* 🏷️ **Column Renaming:** Renamed `timestamp` in `tags.csv` to `tag_timestamp` to eliminate schema collisions with `ratings.csv`.
* 🔍 **Integrity Checks:** Verified and validated Null, NaN, and duplicate values across datasets.
* 🧹 **Logical Duplicate Filtering:** Cleaned multiple ratings submitted by a single user for the same movie.

---

## 📊 Key Performance Indicators (KPIs)

To evaluate platform dynamics and user engagement, the following metrics were engineered:

* 📈 **Average Rating:** Overall satisfaction benchmark across movies and genres.
* 🗳️ **Rating Count / Volume:** Total votes received per movie (proxy for overall popularity).
* 🎯 **High Rating Proportion (HRP):** Percentage share of ratings rated $\ge 4.0$ out of total votes received.
* 👤 **User Engagement Index:** Total volume of submitted ratings and custom tags per user.
* 🎭 **Genre Priority & Volume:** Mass viewership, preference distribution, and interaction rates by genre.

---

## 📈 Key Findings

1. **Rating Volume vs. Score Correlation:**
   > Most movies holding a perfect $5.0$ score received ratings from only 1 or 2 users. Conversely, highly popular movies stabilized at an average score between **$3.8$ and $4.3$**.

2. **Dominant Genres:**
   > **Drama**, **Comedy**, and **Action** lead in total view volume and overall user interaction.

3. **High-Performing Niche Genres:**
   > Specific genres like **Film-Noir**, **War**, and **Documentary** accumulated fewer overall votes, but yielded the highest satisfaction rates based on High Rating Proportion (HRP).

4. **Tag Usage & Engagement Patterns:**
   > Only a small subset of power users actively contribute tags. Most common tags reflect movie mood, director, or plot elements (*e.g., 'classic', 'sci-fi', 'atmospheric'*).

---

## 💡 Strategic Recommendations & Business Proposals

* 🤖 **Recommendation Engine Optimization (Bayesian Average Filtering):**
  Integrate a *Bayesian Average* algorithm into rating calculations to properly weigh vote volume and prevent single-vote $5.0$ movies from topping recommendation lists.

* 💎 **Curated Collections & Niche Targeting:**
  Create dedicated *"Expert Picks"* or *"Hidden Gems"* categories for genres showing high satisfaction despite lower exposure (*e.g., Film-Noir, Documentary*).

* 🏆 **User Engagement Incentivization (Gamification):**
  Implement badges and loyalty points for users who submit tags and detailed reviews, enriching organic platform metadata.

* 🎯 **Correlation-Based Personalization:**
  Deliver personalized notifications and curated watchlists based on user-preferred tags and high-rating genre combinations (*e.g., 'Action|Sci-Fi'*).
