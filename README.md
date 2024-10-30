# Fruit Market Analytics

## Project Overview
This project was made for a job interview challenge as a Business Intelligence Intern. After 3 months with the company, I decided to revisit the same project to see how much I’d learned. The results surprised me; even after a short period, there were many things I would change, and that’s exactly what I did.

## Problems to Solve

The data cleaning and formatting were fine; even the exploratory analysis was ok to answer the requested questions. The problem was with data visualization.

After some experience with dashboards and clients, I realized that my 2-page dashboard didn't *tell a story*. It had comments to answer the questions since the visuals didn’t deliver the message easily on their own.

To solve this, I changed a few things:

- ⬆️**More Indicators** - Added percentage indicators to show how much sales increased or decreased.
- ⚠️**Draw Attention to Specific parts** - Highlighted parts of the graphs that I wanted to emphasize for sales insights.
- ✅**Show the Why** - Added subtitles to explain why the data was shown in that way.
- 💸**More Intuitive Colors** - Psychologically, our brains associate patterns and tend to think of green as representing money. Assigning this color to all income-related elements improves user interpretation.
- ⏳**Less Figma and more Power BI** -  I created all cards, text, and gradients using only Power BI. Using Figma for decoration isn’t always ideal, cause we need to choose wisely where to spend our time on details that aren’t very useful.
- 🔎**Less is More** - If one of the client’s questions is "What was my best sales day?", I need to ensure they can find that insight easily. Instead of a large and colorful table with the income for all days, I created two small tables showing the best and worst sales days (using specific colors only for the information I wanted to highlight).


You can compare all of these changes in the before/after images below:

## Before:
![fruitfarm sem fundo 1](https://github.com/user-attachments/assets/235178a5-78a4-44a8-bdb6-1c4d8f2cdf1a)

![fruitfarm sem fundo 2](https://github.com/user-attachments/assets/f12d4e53-ae5a-4ffb-bd38-9025cd392fef)

## After:
![Análise geral - vendas](https://github.com/user-attachments/assets/940f6148-61e4-4d34-ad5c-8dc607dde392)

![image](https://github.com/user-attachments/assets/159d1d88-6ff0-473c-a3d5-f40751fb1db5)

------------------------

## Answered Questions

The original challenge had some main questions to be answered:

1. **How is the evolution of my overall revenue (considering all products)?**

   A: In September, the volume of fruits sold decreased by 9.54%, and the income decreased by 2.73% compared to August.
   
   ![image](https://github.com/user-attachments/assets/aed2508c-4f18-4018-a897-5f6c41c8dacd)

2. **Which was my best sales day?**

   A: The best sales day was October 26.
   
   ![image](https://github.com/user-attachments/assets/764a9b5f-08c3-438a-b724-07213239a875)

   We can see that on this day, oranges were the most sold fruit, but grapes generated more revenue.
 
   ![image](https://github.com/user-attachments/assets/d9096906-3400-4f36-86c0-9d8e4131625f)

4. **On which day did I sell the most bananas?**
   
   A: We can find the answer on page 2 of the report, where we can see more details about the sales by product. The day when the most bananas were sold was October 28.

   ![Análise - banana](https://github.com/user-attachments/assets/c87913c1-b74c-449c-a5d5-05e01cbd281e)

5. **Which product do I sell in the highest quantity (kg)?**

   A: Orange. Following the top 3, we have tangerines and lemons, which together represent 51.77% of the total volume sold.

   ![image](https://github.com/user-attachments/assets/e339b6d3-a6cd-47a7-9ab1-04eabd23a3df)

## New Formulas

For the original project, I created some common formulas using SUM, CALCULATE and DIVIDE for *Revenue* and *Average Ticket*. After gaining more experience with PBI, I was able to create additional formulas to answer questions more easily. Some examples are:

- **Revenue of The Day**
  
```DAX
FATURAMENTO_DIA = CALCULATE(SUM(fVendas[Valor de Venda]), FILTER(fVendas, dCalendario[Data] = fVendas[DATA]))
```

- **Peak Revenue Day**

```DAX
DIA_MAIOR_FAT_GERAL = 
CALCULATE(
    MAX(dCalendario[Data]), 
    FILTER(
        dCalendario,
        dCalendario[FATURAMENTO DIA] = 
            CALCULATE(MAX(dCalendario[FATURAMENTO DIA]), ALLEXCEPT(dCalendario, dCalendario[Mês], dCalendario[Ano]))
    )
)
```

- **Revenue on the Day of Peak Revenue**
  ```DAX
  FAT_DIA_MAIOR = CALCULATE(
    SUM(dCalendario[FATURAMENTO DIA]),
    FILTER(
        dCalendario,
        dCalendario[Data] = [DIA_MAIOR_FAT_GERAL]
    ))
  ```

## Recomendations

Based on the analysis, I recommend the following actions:

- **Leverage Peak Hours**

Since 7 AM is a specific time of profitability and the hours from 11 AM to 2 PM are also the most profitable, consider implementing specific promotional strategies during these times.

- **Focus on August and October for Seasonality**

As August and October had high revenue, these months may naturally favor sales. Propose early stock preparations and logistics optimization to meet the increased demand during these months.

- **Sales Incentives in September**

Given that September showed a decline, investigate potential causes such as weather conditions, lack of specific campaigns or a reduced variety of fruits. Since oranges performed well in September, one strategy could be to reinforce the sale of citrus fruits during this month and introduce combos that include grapes and carambola, which generate high revenue.

 - **Promotions for Citrus Fruits**

Take advantage of the high sales volume of citrus fruits like oranges, tangerines and lemons to create campaigns that highlight their qualities and attract consumers looking for value in bulk.

- **Highlight the Revenue Champions**

Grapes, tangerines, and carambolas are the most profitable. Showcase them prominently, offer samples or volume discounts and run marketing campaigns that showcase their benefits.



