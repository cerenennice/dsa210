# Dsa210
# **Understanding Viewing Patterns on Netflix Platform**

## **Introduction**
Understanding viewing patterns on streaming platforms provides valuable insights into entertainment preferences and daily routines. Analyzing Netflix viewing data from my family allows for an in-depth exploration of entertainment choices, routines, and habits. This study aims to identify peak viewing times, compare weekday and weekend behaviors, and uncover seasonal trends in content consumption.

## **Dataset Description**
The dataset contains various aspects of Netflix viewing activity, including clickstream logs, content interactions, user profiles, devices used for streaming, IP addresses, and engagement with Netflix's gaming content. Clickstream and content interaction data reveal details about what was watched, paused, or skipped, while profile information helps differentiate viewing habits among users. Additionally, device and IP address records provide insights into how and where content is accessed, contributing to a more comprehensive understanding of streaming behavior. All tables come from Netflix’s GDPR-compliant “Download your personal information” portal. After logging into my account I navigated to Account -> Privacy & Data -> Download your personal information, submitted a request, and received a ZIP file by e-mail a few days later. 


**Structure of the delivery**
• ACCOUNT/AccessAndDevices.csv – every device that has logged in, with Devices, Date, unique ESN and a “Part of household” flag.
• CLICKSTREAM/Clickstream.csv – Web clicks: Profile Name, Source, Navigation Level, referrer/target URLs and Click Utc Ts.
• CONTENT_INTERACTION/ViewingActivity.csv – core watch log: Profile Name, Start Time, Duration, content attributes, Device Type, bookmarks and country codes.
• PROFILES/Profiles.csv – static profile metadata such as Profile Creation Time, Maturity Level, primary language and autoplay setting.
• DEVICES/Devices.csv – richer device catalogue keyed by ESN with first / last playback dates per account and per profile.
• GAMES/GamePlaySession.csv – start time, length, title and platform for Netflix Games sessions.
• IP_ADDRESSES/… – IP blocks for log-ins and streaming events, plus coarse location strings.
• Auxiliary files (Ratings.csv, SearchHistory.csv, InteractiveTitles.csv, etc.) add thumbs-up ratings, free-text searches and interactive-film choices.



**Variable highlights**
• Profile Name (string) – logical viewer; five adult profiles in this export.
• Start Time / Click Utc Ts (ISO datetime) – precise to the second; resampled to hourly buckets for time-series work.
• Duration (HH:MM:SS) – converted to seconds and aggregated into total watch time.
• Device Type (categorical) – e.g. Chrome PC, Sony Android TV 2019, iPhone 14 Pro Max.
• Title (string) – movie / episode name; used only for descriptive stats, not forecasting.
• Derived flags: hour (0-23), weekday (Mon–Sun index), is_weekend (boolean), plus weekly and daily seasonality indicators for Prophet.

## **Project Goals**
The primary objective of this project is to analyze Netflix viewing data to uncover patterns in entertainment consumption. The key goals include:

- Identifying peak viewing times across different days and months.
- Comparing weekday and weekend viewing habits.
- Detecting seasonal trends in content consumption.
- Understanding device usage and profile-based viewing behaviors.

By examining these trends, this analysis aims to enhance the understanding of family entertainment routines and preferences.

## **Hypothesis Testing**
• Null Hypothesis (H₀): The average viewing time on weekends is equal to the average viewing time on weekdays.
• Alternative Hypothesis (H₁): The average viewing time on weekends is different from the average viewing time on weekdays.
• Null Hypothesis (H₀): The average viewing time in winter is equal to the average viewing time in summer. 
• Alternative Hypothesis (H₁): The average viewing time in winter is different from the average viewing time in summer.

