# Karina's Spotify

As one of my first personal projects, I wanted to download my own Spotify data and dive into my listening habits. After sharing some insights to my friend, Karina, she told me she wanted to take a look at her data as well. I offered to analyze it for her so that she can have a more simplified outlook of her music experience, while I can gain more practice in dealing with large datasets and working through them with Google Sheets, writing SQL queries with Google BigQuery, and visualizing with Tableau. It was a win-win!

I showed Karina how she could download her Spotify data, and she received the zip folder a couple days later. Karina's data ranges from March 21, 2023 to March 22, 2024.

After receiving all the relevant downloads of her data, I converted the JSON files to CSV files.

_These separate files could be seen as "streamhistory_0", "streamhistory_1", "streamhistory_2", "streamhistory_3", 
"streamhistory_4" as several sheets in the spreadsheet below._ 

I then uploaded each file to Google Sheets and combined all files of data into one large sheet. This came to a staggering total of 43,767 rows (after cleaning the data)!

_"allstream_history" shows all of the combined data in the spreadsheet below._

You can view the spreadsheet in its entirety [here](https://docs.google.com/spreadsheets/d/1x73eIN_c2P6Nw-ASdNACYE_e-DNZcNBKP-CWkHB2WFE/edit#gid=1663538200).

The data Spotify delivered consists of:
  - Date and time of when each stream ended (in UTC) - "**endTime**"
  - Artist name of music track - "**artistName**"
  - Name of music track - "**trackName**"
  - How many miliseconds the track was listened to - "**msPlayed**"

For more information on understanding Spotify data, refer to this [page](https://support.spotify.com/us/article/understanding-my-data/).

<img width="700" alt="Screenshot 2024-04-09 at 5 51 32 PM" src="https://github.com/panche12/karinas-spotify/assets/67511947/999f036f-be16-49ca-8a0c-d1734101fa1c">

### Converting miliseconds -> seconds
<img width="920" alt="Screenshot 2024-04-09 at 8 21 23 PM" src="https://github.com/panche12/karinas-spotify/assets/67511947/2e09a7e9-a021-4d95-90a7-f0b9352e23f8">

### Converting seconds -> minutes
<img width="1021" alt="Screenshot 2024-04-09 at 8 20 29 PM" src="https://github.com/panche12/karinas-spotify/assets/67511947/62f34031-5583-4347-8ef5-18bc23bd24c0">

### Sheet: allstream_history
<img width="1462" alt="Screenshot 2024-04-09 at 8 27 52 PM" src="https://github.com/panche12/karinas-spotify/assets/67511947/78b12fd5-80e6-49f7-b22d-555d87b731c0">

### Pivot Table

After having all the data combined into one sheet, I wanted to make a pivot table to summarize the data on allstream_history. 

### Sheet: Pivot Table of all_streamhistory
<img width="1243" alt="Screenshot 2024-04-09 at 9 51 34 PM" src="https://github.com/panche12/karinas-spotify/assets/67511947/cdd32adf-aa8d-491e-9581-19c27c2958dc">

The pivot table consists of: 
- Track names
- Artist names
- Sum of miliseconds played from each song
- Sum of seconds played from each song
- Sum of minutes played from each song
- Amount of times each song has been played

While I was analyzing allstream_history, I realized that there were possibilities of different songs having the same title under distinct artists. The pivot table helped me find which song titles were shared between different singers. 
Those song titles are highlighted.
<img width="863" alt="Screenshot 2024-04-09 at 9 32 01 PM" src="https://github.com/panche12/karinas-spotify/assets/67511947/37a0d8f1-dfff-4ecc-be66-10f8554d7c42">

_ASTRO, R5, and The Vamps all have a song titled "All Night"._


### Finding more information 
I then wanted to find the number of times each artist was played as well as the number of their distinct songs that were streamed. 

I also found the total duration played by artist.

<img width="860" alt="Screenshot 2024-04-10 at 3 19 13 PM" src="https://github.com/panche12/karinas-spotify/assets/67511947/6eb253e9-73f2-40ba-9539-898895b3cc78">

Below are also the total number of artists, total number of listens, total number of unique tracks, and total duration of Karina's listening history from the past year. 

<img width="307" alt="Screenshot 2024-04-10 at 3 24 38 PM" src="https://github.com/panche12/karinas-spotify/assets/67511947/42fa3832-5dae-4d77-9259-a9f0009d6511">

To find these answers, I copied and pasted "all_streamhistory" onto a new sheet and did the calculations for the above on the same sheet ("all_streamhistory + more"), grabbing information from the original dataset.

### Sheet: all_streamhistory + more
<img width="1445" alt="Screenshot 2024-04-11 at 11 54 53 AM" src="https://github.com/panche12/karinas-spotify/assets/67511947/466b065b-0d67-4aee-8f95-5f14f70a1b6c">


Here's how I did it:

The COUNTIF function allows me to count the number of times the value in H2 ("Taylor Swift") appears in the column B2:B (**artistName**). In this case, B2:B is the range, and H2 is the criterion. This helped me find the count of Taylor Swift streams Karina played in the past year.

Double-clicking the blue circle on the lower-right corner of the cell allowed me to autofill the column. The same formula is used with their respective criterion (H3 for FIFTY FIFTY, H4 for charlieonnafriday, etc.) This helped me calculate the amount of times each artist was streamed. 
<img width="941" alt="Screenshot 2024-04-10 at 5 17 51 PM" src="https://github.com/panche12/karinas-spotify/assets/67511947/a84a8948-c77c-4959-8817-68f26cd62f7a">

The COUNTUNIQUEIFS function returns the number of tracks Karina listened to by the respective artists. This formula counts the number of unique values, in this case the distinct number of tracks, that meet multiple criteria, which are the artist name in the H column, and the ranges of the **trackName** (C2:C) and **artistName** (B2:B) columns.  
<img width="1058" alt="Screenshot 2024-04-10 at 5 18 13 PM" src="https://github.com/panche12/karinas-spotify/assets/67511947/d68e117f-2821-4f2c-9554-2d8b9769f97a">

The SUMIFS function helps me add up the total number of miliseconds, seconds, and minutes that each artist was played in the past year. This formula helps me return the sum of a range depending on multiple criteria. In this case, I was able to find the sum of miliseconds played for Taylor Swift, calculating the msPlayed (from the range C2:C) where the name in artistName (B2:B) is the value of H2 ("Taylor Swift"). 

This formula was used to find the total number of seconds and minutes for each artist as well. 
<img width="1107" alt="Screenshot 2024-04-10 at 5 18 32 PM" src="https://github.com/panche12/karinas-spotify/assets/67511947/0c7d1370-1ad5-4223-a924-c4cab31a3cf1">

<img width="1166" alt="Screenshot 2024-04-10 at 5 18 49 PM" src="https://github.com/panche12/karinas-spotify/assets/67511947/bca57adf-ec6f-44d2-b740-8dfc8afe5bc1">

<img width="1237" alt="Screenshot 2024-04-10 at 5 19 14 PM" src="https://github.com/panche12/karinas-spotify/assets/67511947/688e1bfc-d352-4c7c-b0a4-d070db90459d">

To count the total number of artists, I used the COUNTA function to count all the values in column H, which already listed all the distinct artists from the original Spotify dataset. 
<img width="1445" alt="Screenshot 2024-04-10 at 5 20 01 PM" src="https://github.com/panche12/karinas-spotify/assets/67511947/efc523b6-5bde-4540-84b2-c3ac5c271742">

To count the total number of listens, the COUNTA function was used again to count the number of values in column H, which listed all the track names that were streamed in the past year. 
<img width="1431" alt="Screenshot 2024-04-10 at 5 20 44 PM" src="https://github.com/panche12/karinas-spotify/assets/67511947/dc45b30f-a046-413d-b9b2-705f8ae2db93">

To learn the number of unique tracks that Karina listened to, I used the pivot table I created on Pivot Table of all_streamhistory and SQL to verify my calculations. 

I used the conditional formatting rule to highlight the cells containing the word "Total" and subtracted that from the amount of rows in the pivot table.

In SQL, I wrote the following query:
```
SELECT DISTINCT trackName, artistName, count(trackName) as amt_times
FROM karina_spotify
GROUP BY trackName, artistName;
```
This gave me 2680 results, verifying that there were a total of unique tracks that Karina listened to during March 2023 - March 2024. 
<img width="1137" alt="Screenshot 2024-04-11 at 12 09 02 PM" src="https://github.com/panche12/karinas-spotify/assets/67511947/768879f3-5ff6-466b-a2ed-e59e623c6c9e">

To find the total minutes, seconds, and miliseconds, I used the SUM function to add up all the values in their respective D (msPlayed), E (sPlayed), and F (mPLayed) columns.
<img width="1434" alt="Screenshot 2024-04-10 at 5 21 41 PM" src="https://github.com/panche12/karinas-spotify/assets/67511947/9e958727-baf2-400c-a86b-f0da2f246f35">
<img width="1434" alt="Screenshot 2024-04-10 at 5 21 24 PM" src="https://github.com/panche12/karinas-spotify/assets/67511947/367eaf3f-48c8-483d-81d0-cbd12cffdffd">
<img width="1433" alt="Screenshot 2024-04-10 at 5 21 07 PM" src="https://github.com/panche12/karinas-spotify/assets/67511947/8112437f-20d2-4c25-bac3-309a9d7cbd53">

















