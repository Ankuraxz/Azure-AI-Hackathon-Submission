# Azure-AI-Hackathon-Submission
Submission for AzureAI Hackathon

![Architectural Diagram](./Untitled%20Diagram.jpg)

## Inspiration
All of our team members, like to invest, and we were always on a look out for a tool, which can send out TL;DR on finances, but highly customized, so we don't have to read news. A tool, that can not only tell us rates of our favorite stock, but in a reliable fashion answer, questions like "What will be the Impact of New GPT model, on Microsoft Stock" or "Will the change of President, impact my portfolio". We wanted a platform, that can give us quick summaries about stocks, analysis and news headlines of things, that matter to us.

## What it does
Trendlytics, is the solution to all aforementioned problems, Powered by Generative AI and Microsoft Azure, Trendlytics, is the one finance app, to rule them all. Upon Login, it shows the Latest in trends (News headlines), customized to your demands. In the trend analytics section, see all the latest trends, insight graphs and news summaries, about the stocks you care about, and in the stock analysis, the summary and analysis of your favorite stocks. Moreover, it features a chatbot, using OPENAI GPT-03 Reasoning & GPT-4o , to answer any query you may have. It fetches and sources, its information live from multiple news networks and our database, as well as 3-rd party data applications.

Some Interesting Queries Include:

* In a tabular format, provide me with the mid-cap companies, which are safe to invest in, considering US trade news (News Analytics)
  
* Elon just tweeted about Crypto, which stock may go up (Trend Analytics)
  
* Does AMD gets impacted, with NVIDIA's latest robot release, if yes, how (Stock Analytics)
  
* Teach me how to Invest step by step, how to find a good stock, then how to invest, I use WealthSimple (Education)

## How we built it
*The Backend is 2 parts, a synchronous and another asynchronous *

1. Asynchronous - This Backend Infra is the backbone of the project. It has 4 parts - Data Extractor, Data Analyzer, Database Manager & Notifier, all these components are decoupled, highly scalable and efficient. All these 4 parts reside in different Azure B-Class VM, connected via event driven or time driven components
   
   1. **Data Extractor** - Every Few minutes, it scraps and extracts data from over 7 financial websites, blogs, along with social media. and create events for analyzer, using Azure Event Bus
   2. **Data Analyzer** - Triggered by Event, a Function, analyzes the raw data, cleans it, enriches it using Generative AI models - OpenAI GPT-O3 mini, it also analyze the Images and Videos using OpenAI GPT-Vision models and Models from Azure Cognitive Services. It makes data Database compatible, and pushes it in 2 different Azure Blob Storage Queue
   3. **Database Manager** - This node also features Functions, that get triggered with Queue, to put the data in Azure Cosmos DB or to take data, vectorize it with OpenAI Embeddings and save it in Milvus Database Zilliz hosted on Azure VM, to act as a RAG for chatbot.
   4. **Notifier** - This Node, works based on time, every morning and evening, reads the user-preferences & Latest of News, trends and analytics from CosmosDB, and creates & sends out a customized news letter to all users. 

2. Synchronous - This Backend Infra is for our Website Dashboard. Hosted with Azure App Service & scaled usign Application Gateway & Load balancer, this backend is where multiple Generative AI and Analytics Model sit, to serve Live Analytics, ChatBot, News Summaries from Cosmos, Live currency rates, Forex Rates and more.

*The Frontend*
The Frontend is a NextJS Dashboard, that brings it all together, in a user-friendly fashion. It divides the entire app in 3 sections, News Analytics, Trend Analytics, Stock Analytics, and a chatbot all served from Synchronous backend, with knowledge of Asynchronous backend and other 3rd -party API's


## Features
* Made using over 10 Microsoft Azure Tools, and with over 5 Different Generative AI models, from Microsoft OpenAI
  
* Powered by 5+ cutting-edge Generative AI models, including OpenAI’s GPT-4o, GPT-03 Reasoning, and Azure Cognitive Services for multimodal data analysis.
  
* Real-time financial trend analysis that extracts, processes, and delivers tailored insights directly to users
  
* AI-driven chatbot that fetches live stock analytics, news, and financial data on demand
  
* Automated newsletter service delivering personalized market updates every morning and evening
  
* Robust asynchronous backend handling massive data streams through Azure Event Bus, Blob Storage Queues, and Cosmos DB.
  
  
* Intuitive Next.js-powered frontend that brings News Analytics, Trend Analytics, Stock Analytics, and chatbot interactions into one streamlined dashboard.


## Challenges we ran into
Building a comprehensive financial AI tool that delivers real-time insights wasn’t easy. Some hurdles we overcame:

* **Data Volume & Processing** – Scraping, analyzing, and structuring financial data from multiple sources while maintaining accuracy and speed.

* **Scalability** – Ensuring a seamless experience for all users, even during peak trading hours, required optimizing Azure VM allocations and event-driven components.

* **Multimodal AI Integration** – Implementing OpenAI’s GPT models for both textual and visual financial analysis brought new challenges in processing real-time image and video content.

* **Reliable Stock Predictions** – Training AI models to provide meaningful financial insights rather than generic summaries took careful tuning of embeddings and vectorized financial data.

## Accomplishments that we're proud of

* Successfully created a highly personalized financial AI assistant, offering tailored insights instead of generic news

* Integrated real-time stock and market analysis using AI-powered financial models

* Built a fully automated financial trend detection system, ensuring users stay ahead of market movements

* Developed a scalable, event-driven architecture that handles financial data from multiple sources efficiently

* Deployed an AI chatbot that not only provides stock data but also explains investment strategies step by step

## What we learned

Throughout this journey, we uncovered key insights about building an AI-powered financial tool:

* Real-time financial data needs constant monitoring – Market trends shift rapidly, so a robust data extraction and analysis pipeline is crucial.

* Personalization is everything – Users don’t want just raw data; they need tailored, actionable insights that match their portfolios and interests.

* AI in finance goes beyond text – The impact of multimodal AI, analyzing news, tweets, and even images/videos, is immense for financial predictions.

* Scalability is key – With a global audience in mind, building an event-driven and highly available infrastructure ensures a smooth user experience.

## What's next for Trendlytics

Trendlytics is just getting started! Here’s what’s on the horizon:

* **Deep AI-Powered Portfolio Analysis** – Users will soon be able to get personalized investment advice based on their portfolio and risk appetite.

* **Expanded Data Sources** – More financial sources, including earnings reports, SEC filings, and global market data.

* **AI-Driven Investment Courses** – Interactive lessons powered by AI, teaching users how to invest step by step.

* **Mobile App** – Bringing Trendlytics to iOS and Android for seamless access on the go.

* **Enhanced Chatbot Capabilities** – More intelligent, contextual investment discussions with support for multi-turn financial planning queries.

*Trendlytics isn’t just another finance app—it’s the future of personalized, AI-driven investment intelligence. Stay ahead, stay informed, and make smarter financial decisions with Trendlytics!*
