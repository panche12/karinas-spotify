# Karina's Spotify

As one of my first personal projects, I wanted to download my own Spotify data and dive into my listening habits. After sharing some insights to my friend, Karina, she told me she wanted to take a look at her data as well. I offered to analyze it for her so that she can have a more simplified outlook of her music experience, while I can gain more practice in dealing with large datasets and working through them with Google Sheets, Google BigQuery, and Tableau. It was a win, win!

I showed Karina how she can download her Spotify data, and she received the zip folder couple days later. Karina's data ranges from March 21, 2023 to March 22, 2024.

After receiving all the relevant downloads of Karina's Spotify data, I converted the JSON files to CSV files.

_These separate files could be seen as "streamhistory_0", "streamhistory_1", "streamhistory_2", "streamhistory_3", 
"streamhistory_4" in the spreadsheet below._ 

I then uploaded each file to Google Sheets and combined all files of data into one large sheet. This came to a staggering total of 43,767 rows (after cleaning the data)!

_"allstream_history" shows all of the combined data in the spreadsheet below._

You can view the spreadsheet in its entirety [here](https://docs.google.com/spreadsheets/d/1x73eIN_c2P6Nw-ASdNACYE_e-DNZcNBKP-CWkHB2WFE/edit#gid=1663538200).

The data Spotify delivered consists of:
  - Date and time of when each stream ended (in UTC) - "**endTime**"
  - Artist name of music track - "**artistName**"
  - Name of music track - "**trackName**"
  - How many miliseconds the track was listened to - "**msPlayed**"

For more information on understanding Spotify data, refer to this [page](https://support.spotify.com/us/article/understanding-my-data/).

<img width="819" alt="Screenshot 2024-04-09 at 5 51 32 PM" src="https://github.com/panche12/karinas-spotify/assets/67511947/999f036f-be16-49ca-8a0c-d1734101fa1c">

### Converting miliseconds -> seconds
<img width="920" alt="Screenshot 2024-04-09 at 8 21 23 PM" src="https://github.com/panche12/karinas-spotify/assets/67511947/2e09a7e9-a021-4d95-90a7-f0b9352e23f8">

### Converting seconds -> minutes
<img width="1021" alt="Screenshot 2024-04-09 at 8 20 29 PM" src="https://github.com/panche12/karinas-spotify/assets/67511947/62f34031-5583-4347-8ef5-18bc23bd24c0">

### Sheet: allstream_history
<img width="1462" alt="Screenshot 2024-04-09 at 8 27 52 PM" src="https://github.com/panche12/karinas-spotify/assets/67511947/78b12fd5-80e6-49f7-b22d-555d87b731c0">

### Pivot Tables

After having all the data combined into one sheet, I wanted to make a pivot table to summarize the data on allstream_history. 

While I was analyzing allstream_history, I realized that there were possibilities of different songs having the same title under distinct artists. The pivot table helped me find which song titles were shared between different singers. 
<img width="863" alt="Screenshot 2024-04-09 at 9 32 01 PM" src="https://github.com/panche12/karinas-spotify/assets/67511947/37a0d8f1-dfff-4ecc-be66-10f8554d7c42">
_ASTRO, R5, and The Vamps all have a song titled "All Night"._

The pivot table consists of: 
- Track names
- Artist names
- Sum of miliseconds played from each song
- Sum of seconds played from each song
- Sum of minutes played from each song
- Amount of times each song has been played

<img width="1243" alt="Screenshot 2024-04-09 at 9 51 34 PM" src="https://github.com/panche12/karinas-spotify/assets/67511947/cdd32adf-aa8d-491e-9581-19c27c2958dc">







