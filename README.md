# Karina's Spotify

As one of my first personal projects, I wanted to download my own Spotify data and dive into my listening habits. After sharing some insights to my friend, Karina, she told me she wanted to take a look at her data as well. I offered to analyze it for her so that she can have a more simplified outlook of her music experience, while I can gain more practice in dealing with large datasets and working through them with Google Sheets, Google BigQuery, and Tableau. It was a win, win!

After receiving all the relevant downloads of Karina's Spotify data, I converted the JSON files to CSV files.

_These separate files could be seen as "streamhistory_0", "streamhistory_1", "streamhistory_2", "streamhistory_3", 
"streamhistory_4" in the spreadsheet below._ 

I then uploaded each file to Google Sheets and combined all files of data into one large sheet. This came to a staggering total of 43,767 rows (after cleaning the data)!

_"allstream_history" shows all of the combined data in the spreadsheet below._

You can view the spreadsheet in its entirety [here](https://docs.google.com/spreadsheets/d/1x73eIN_c2P6Nw-ASdNACYE_e-DNZcNBKP-CWkHB2WFE/edit#gid=1663538200).

The data that Spotify delivered consisted of:
  - Date and time of when each stream ended (in UTC) - "**endTime**"
  - Artist name of music track - "**artistName**"
  - Name of music track - "**trackName**"
  - How many miliseconds the track was listened to - "**msPlayed**"

For more information on understanding Spotify data, refer to this [page](https://support.spotify.com/us/article/understanding-my-data/).

<img width="819" alt="Screenshot 2024-04-09 at 5 51 32 PM" src="https://github.com/panche12/karinas-spotify/assets/67511947/999f036f-be16-49ca-8a0c-d1734101fa1c">

#### Converting miliseconds -> seconds -> minutes 
<img width="819" alt="Screenshot 2024-04-09 at 5 51 32 PM" src="https://github.com/panche12/karinas-spotify/assets/67511947/f6af15b9-8af7-407f-935b-4c395141194b">
<img width="1021" alt="Screenshot 2024-04-09 at 8 20 29 PM" src="https://github.com/panche12/karinas-spotify/assets/67511947/62f34031-5583-4347-8ef5-18bc23bd24c0">


