## Spotify Tracks Genre Dataset Research

Considering Spotify Wrapped just came out, I think we can all say we are excited to look at the top Spotify tracks, what genres were the most popular, and overall how certain artists grew throughout this year! In the dataset I have downloaded (from a lovely maharshipandya on kaggle), I will be looking at what the most popular songs were, what genres were the most popular, the danceability and energy of each song, and more! 

Here is a list of the main questions I will be looking to answer:

1.) What was the most popular song this year?
2.) Who wrote this song, how long was it, and what album is it in?
3.) What genre was it?
4.) On average, how long were songs this year?
5.) What was the most common genre of song this year?
6.) What was the average danceability of this dataset? Energy?


```python

```


```python

```


```python
import pandas as pd
df = pd.read_csv('/Users/summermesler/Downloads/train.csv')
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Unnamed: 0</th>
      <th>track_id</th>
      <th>artists</th>
      <th>album_name</th>
      <th>track_name</th>
      <th>popularity</th>
      <th>duration_ms</th>
      <th>explicit</th>
      <th>danceability</th>
      <th>energy</th>
      <th>...</th>
      <th>loudness</th>
      <th>mode</th>
      <th>speechiness</th>
      <th>acousticness</th>
      <th>instrumentalness</th>
      <th>liveness</th>
      <th>valence</th>
      <th>tempo</th>
      <th>time_signature</th>
      <th>track_genre</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>5SuOikwiRyPMVoIQDJUgSV</td>
      <td>Gen Hoshino</td>
      <td>Comedy</td>
      <td>Comedy</td>
      <td>73</td>
      <td>230666</td>
      <td>False</td>
      <td>0.676</td>
      <td>0.4610</td>
      <td>...</td>
      <td>-6.746</td>
      <td>0</td>
      <td>0.1430</td>
      <td>0.0322</td>
      <td>0.000001</td>
      <td>0.3580</td>
      <td>0.7150</td>
      <td>87.917</td>
      <td>4</td>
      <td>acoustic</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>4qPNDBW1i3p13qLCt0Ki3A</td>
      <td>Ben Woodward</td>
      <td>Ghost (Acoustic)</td>
      <td>Ghost - Acoustic</td>
      <td>55</td>
      <td>149610</td>
      <td>False</td>
      <td>0.420</td>
      <td>0.1660</td>
      <td>...</td>
      <td>-17.235</td>
      <td>1</td>
      <td>0.0763</td>
      <td>0.9240</td>
      <td>0.000006</td>
      <td>0.1010</td>
      <td>0.2670</td>
      <td>77.489</td>
      <td>4</td>
      <td>acoustic</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>1iJBSr7s7jYXzM8EGcbK5b</td>
      <td>Ingrid Michaelson;ZAYN</td>
      <td>To Begin Again</td>
      <td>To Begin Again</td>
      <td>57</td>
      <td>210826</td>
      <td>False</td>
      <td>0.438</td>
      <td>0.3590</td>
      <td>...</td>
      <td>-9.734</td>
      <td>1</td>
      <td>0.0557</td>
      <td>0.2100</td>
      <td>0.000000</td>
      <td>0.1170</td>
      <td>0.1200</td>
      <td>76.332</td>
      <td>4</td>
      <td>acoustic</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>6lfxq3CG4xtTiEg7opyCyx</td>
      <td>Kina Grannis</td>
      <td>Crazy Rich Asians (Original Motion Picture Sou...</td>
      <td>Can't Help Falling In Love</td>
      <td>71</td>
      <td>201933</td>
      <td>False</td>
      <td>0.266</td>
      <td>0.0596</td>
      <td>...</td>
      <td>-18.515</td>
      <td>1</td>
      <td>0.0363</td>
      <td>0.9050</td>
      <td>0.000071</td>
      <td>0.1320</td>
      <td>0.1430</td>
      <td>181.740</td>
      <td>3</td>
      <td>acoustic</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>5vjLSffimiIP26QG5WcN2K</td>
      <td>Chord Overstreet</td>
      <td>Hold On</td>
      <td>Hold On</td>
      <td>82</td>
      <td>198853</td>
      <td>False</td>
      <td>0.618</td>
      <td>0.4430</td>
      <td>...</td>
      <td>-9.681</td>
      <td>1</td>
      <td>0.0526</td>
      <td>0.4690</td>
      <td>0.000000</td>
      <td>0.0829</td>
      <td>0.1670</td>
      <td>119.949</td>
      <td>4</td>
      <td>acoustic</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>113995</th>
      <td>113995</td>
      <td>2C3TZjDRiAzdyViavDJ217</td>
      <td>Rainy Lullaby</td>
      <td>#mindfulness - Soft Rain for Mindful Meditatio...</td>
      <td>Sleep My Little Boy</td>
      <td>21</td>
      <td>384999</td>
      <td>False</td>
      <td>0.172</td>
      <td>0.2350</td>
      <td>...</td>
      <td>-16.393</td>
      <td>1</td>
      <td>0.0422</td>
      <td>0.6400</td>
      <td>0.928000</td>
      <td>0.0863</td>
      <td>0.0339</td>
      <td>125.995</td>
      <td>5</td>
      <td>world-music</td>
    </tr>
    <tr>
      <th>113996</th>
      <td>113996</td>
      <td>1hIz5L4IB9hN3WRYPOCGPw</td>
      <td>Rainy Lullaby</td>
      <td>#mindfulness - Soft Rain for Mindful Meditatio...</td>
      <td>Water Into Light</td>
      <td>22</td>
      <td>385000</td>
      <td>False</td>
      <td>0.174</td>
      <td>0.1170</td>
      <td>...</td>
      <td>-18.318</td>
      <td>0</td>
      <td>0.0401</td>
      <td>0.9940</td>
      <td>0.976000</td>
      <td>0.1050</td>
      <td>0.0350</td>
      <td>85.239</td>
      <td>4</td>
      <td>world-music</td>
    </tr>
    <tr>
      <th>113997</th>
      <td>113997</td>
      <td>6x8ZfSoqDjuNa5SVP5QjvX</td>
      <td>Cesária Evora</td>
      <td>Best Of</td>
      <td>Miss Perfumado</td>
      <td>22</td>
      <td>271466</td>
      <td>False</td>
      <td>0.629</td>
      <td>0.3290</td>
      <td>...</td>
      <td>-10.895</td>
      <td>0</td>
      <td>0.0420</td>
      <td>0.8670</td>
      <td>0.000000</td>
      <td>0.0839</td>
      <td>0.7430</td>
      <td>132.378</td>
      <td>4</td>
      <td>world-music</td>
    </tr>
    <tr>
      <th>113998</th>
      <td>113998</td>
      <td>2e6sXL2bYv4bSz6VTdnfLs</td>
      <td>Michael W. Smith</td>
      <td>Change Your World</td>
      <td>Friends</td>
      <td>41</td>
      <td>283893</td>
      <td>False</td>
      <td>0.587</td>
      <td>0.5060</td>
      <td>...</td>
      <td>-10.889</td>
      <td>1</td>
      <td>0.0297</td>
      <td>0.3810</td>
      <td>0.000000</td>
      <td>0.2700</td>
      <td>0.4130</td>
      <td>135.960</td>
      <td>4</td>
      <td>world-music</td>
    </tr>
    <tr>
      <th>113999</th>
      <td>113999</td>
      <td>2hETkH7cOfqmz3LqZDHZf5</td>
      <td>Cesária Evora</td>
      <td>Miss Perfumado</td>
      <td>Barbincor</td>
      <td>22</td>
      <td>241826</td>
      <td>False</td>
      <td>0.526</td>
      <td>0.4870</td>
      <td>...</td>
      <td>-10.204</td>
      <td>0</td>
      <td>0.0725</td>
      <td>0.6810</td>
      <td>0.000000</td>
      <td>0.0893</td>
      <td>0.7080</td>
      <td>79.198</td>
      <td>4</td>
      <td>world-music</td>
    </tr>
  </tbody>
</table>
<p>114000 rows × 21 columns</p>
</div>




```python
dff = df.dropna()
dff
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Unnamed: 0</th>
      <th>track_id</th>
      <th>artists</th>
      <th>album_name</th>
      <th>track_name</th>
      <th>popularity</th>
      <th>duration_ms</th>
      <th>explicit</th>
      <th>danceability</th>
      <th>energy</th>
      <th>...</th>
      <th>loudness</th>
      <th>mode</th>
      <th>speechiness</th>
      <th>acousticness</th>
      <th>instrumentalness</th>
      <th>liveness</th>
      <th>valence</th>
      <th>tempo</th>
      <th>time_signature</th>
      <th>track_genre</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>5SuOikwiRyPMVoIQDJUgSV</td>
      <td>Gen Hoshino</td>
      <td>Comedy</td>
      <td>Comedy</td>
      <td>73</td>
      <td>230666</td>
      <td>False</td>
      <td>0.676</td>
      <td>0.4610</td>
      <td>...</td>
      <td>-6.746</td>
      <td>0</td>
      <td>0.1430</td>
      <td>0.0322</td>
      <td>0.000001</td>
      <td>0.3580</td>
      <td>0.7150</td>
      <td>87.917</td>
      <td>4</td>
      <td>acoustic</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>4qPNDBW1i3p13qLCt0Ki3A</td>
      <td>Ben Woodward</td>
      <td>Ghost (Acoustic)</td>
      <td>Ghost - Acoustic</td>
      <td>55</td>
      <td>149610</td>
      <td>False</td>
      <td>0.420</td>
      <td>0.1660</td>
      <td>...</td>
      <td>-17.235</td>
      <td>1</td>
      <td>0.0763</td>
      <td>0.9240</td>
      <td>0.000006</td>
      <td>0.1010</td>
      <td>0.2670</td>
      <td>77.489</td>
      <td>4</td>
      <td>acoustic</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>1iJBSr7s7jYXzM8EGcbK5b</td>
      <td>Ingrid Michaelson;ZAYN</td>
      <td>To Begin Again</td>
      <td>To Begin Again</td>
      <td>57</td>
      <td>210826</td>
      <td>False</td>
      <td>0.438</td>
      <td>0.3590</td>
      <td>...</td>
      <td>-9.734</td>
      <td>1</td>
      <td>0.0557</td>
      <td>0.2100</td>
      <td>0.000000</td>
      <td>0.1170</td>
      <td>0.1200</td>
      <td>76.332</td>
      <td>4</td>
      <td>acoustic</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>6lfxq3CG4xtTiEg7opyCyx</td>
      <td>Kina Grannis</td>
      <td>Crazy Rich Asians (Original Motion Picture Sou...</td>
      <td>Can't Help Falling In Love</td>
      <td>71</td>
      <td>201933</td>
      <td>False</td>
      <td>0.266</td>
      <td>0.0596</td>
      <td>...</td>
      <td>-18.515</td>
      <td>1</td>
      <td>0.0363</td>
      <td>0.9050</td>
      <td>0.000071</td>
      <td>0.1320</td>
      <td>0.1430</td>
      <td>181.740</td>
      <td>3</td>
      <td>acoustic</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>5vjLSffimiIP26QG5WcN2K</td>
      <td>Chord Overstreet</td>
      <td>Hold On</td>
      <td>Hold On</td>
      <td>82</td>
      <td>198853</td>
      <td>False</td>
      <td>0.618</td>
      <td>0.4430</td>
      <td>...</td>
      <td>-9.681</td>
      <td>1</td>
      <td>0.0526</td>
      <td>0.4690</td>
      <td>0.000000</td>
      <td>0.0829</td>
      <td>0.1670</td>
      <td>119.949</td>
      <td>4</td>
      <td>acoustic</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>113995</th>
      <td>113995</td>
      <td>2C3TZjDRiAzdyViavDJ217</td>
      <td>Rainy Lullaby</td>
      <td>#mindfulness - Soft Rain for Mindful Meditatio...</td>
      <td>Sleep My Little Boy</td>
      <td>21</td>
      <td>384999</td>
      <td>False</td>
      <td>0.172</td>
      <td>0.2350</td>
      <td>...</td>
      <td>-16.393</td>
      <td>1</td>
      <td>0.0422</td>
      <td>0.6400</td>
      <td>0.928000</td>
      <td>0.0863</td>
      <td>0.0339</td>
      <td>125.995</td>
      <td>5</td>
      <td>world-music</td>
    </tr>
    <tr>
      <th>113996</th>
      <td>113996</td>
      <td>1hIz5L4IB9hN3WRYPOCGPw</td>
      <td>Rainy Lullaby</td>
      <td>#mindfulness - Soft Rain for Mindful Meditatio...</td>
      <td>Water Into Light</td>
      <td>22</td>
      <td>385000</td>
      <td>False</td>
      <td>0.174</td>
      <td>0.1170</td>
      <td>...</td>
      <td>-18.318</td>
      <td>0</td>
      <td>0.0401</td>
      <td>0.9940</td>
      <td>0.976000</td>
      <td>0.1050</td>
      <td>0.0350</td>
      <td>85.239</td>
      <td>4</td>
      <td>world-music</td>
    </tr>
    <tr>
      <th>113997</th>
      <td>113997</td>
      <td>6x8ZfSoqDjuNa5SVP5QjvX</td>
      <td>Cesária Evora</td>
      <td>Best Of</td>
      <td>Miss Perfumado</td>
      <td>22</td>
      <td>271466</td>
      <td>False</td>
      <td>0.629</td>
      <td>0.3290</td>
      <td>...</td>
      <td>-10.895</td>
      <td>0</td>
      <td>0.0420</td>
      <td>0.8670</td>
      <td>0.000000</td>
      <td>0.0839</td>
      <td>0.7430</td>
      <td>132.378</td>
      <td>4</td>
      <td>world-music</td>
    </tr>
    <tr>
      <th>113998</th>
      <td>113998</td>
      <td>2e6sXL2bYv4bSz6VTdnfLs</td>
      <td>Michael W. Smith</td>
      <td>Change Your World</td>
      <td>Friends</td>
      <td>41</td>
      <td>283893</td>
      <td>False</td>
      <td>0.587</td>
      <td>0.5060</td>
      <td>...</td>
      <td>-10.889</td>
      <td>1</td>
      <td>0.0297</td>
      <td>0.3810</td>
      <td>0.000000</td>
      <td>0.2700</td>
      <td>0.4130</td>
      <td>135.960</td>
      <td>4</td>
      <td>world-music</td>
    </tr>
    <tr>
      <th>113999</th>
      <td>113999</td>
      <td>2hETkH7cOfqmz3LqZDHZf5</td>
      <td>Cesária Evora</td>
      <td>Miss Perfumado</td>
      <td>Barbincor</td>
      <td>22</td>
      <td>241826</td>
      <td>False</td>
      <td>0.526</td>
      <td>0.4870</td>
      <td>...</td>
      <td>-10.204</td>
      <td>0</td>
      <td>0.0725</td>
      <td>0.6810</td>
      <td>0.000000</td>
      <td>0.0893</td>
      <td>0.7080</td>
      <td>79.198</td>
      <td>4</td>
      <td>world-music</td>
    </tr>
  </tbody>
</table>
<p>113999 rows × 21 columns</p>
</div>




```python
df = df.drop_duplicates('track_id')
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Unnamed: 0</th>
      <th>track_id</th>
      <th>artists</th>
      <th>album_name</th>
      <th>track_name</th>
      <th>popularity</th>
      <th>duration_ms</th>
      <th>explicit</th>
      <th>danceability</th>
      <th>energy</th>
      <th>...</th>
      <th>loudness</th>
      <th>mode</th>
      <th>speechiness</th>
      <th>acousticness</th>
      <th>instrumentalness</th>
      <th>liveness</th>
      <th>valence</th>
      <th>tempo</th>
      <th>time_signature</th>
      <th>track_genre</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>5SuOikwiRyPMVoIQDJUgSV</td>
      <td>Gen Hoshino</td>
      <td>Comedy</td>
      <td>Comedy</td>
      <td>73</td>
      <td>230666</td>
      <td>False</td>
      <td>0.676</td>
      <td>0.4610</td>
      <td>...</td>
      <td>-6.746</td>
      <td>0</td>
      <td>0.1430</td>
      <td>0.0322</td>
      <td>0.000001</td>
      <td>0.3580</td>
      <td>0.7150</td>
      <td>87.917</td>
      <td>4</td>
      <td>acoustic</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>4qPNDBW1i3p13qLCt0Ki3A</td>
      <td>Ben Woodward</td>
      <td>Ghost (Acoustic)</td>
      <td>Ghost - Acoustic</td>
      <td>55</td>
      <td>149610</td>
      <td>False</td>
      <td>0.420</td>
      <td>0.1660</td>
      <td>...</td>
      <td>-17.235</td>
      <td>1</td>
      <td>0.0763</td>
      <td>0.9240</td>
      <td>0.000006</td>
      <td>0.1010</td>
      <td>0.2670</td>
      <td>77.489</td>
      <td>4</td>
      <td>acoustic</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>1iJBSr7s7jYXzM8EGcbK5b</td>
      <td>Ingrid Michaelson;ZAYN</td>
      <td>To Begin Again</td>
      <td>To Begin Again</td>
      <td>57</td>
      <td>210826</td>
      <td>False</td>
      <td>0.438</td>
      <td>0.3590</td>
      <td>...</td>
      <td>-9.734</td>
      <td>1</td>
      <td>0.0557</td>
      <td>0.2100</td>
      <td>0.000000</td>
      <td>0.1170</td>
      <td>0.1200</td>
      <td>76.332</td>
      <td>4</td>
      <td>acoustic</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>6lfxq3CG4xtTiEg7opyCyx</td>
      <td>Kina Grannis</td>
      <td>Crazy Rich Asians (Original Motion Picture Sou...</td>
      <td>Can't Help Falling In Love</td>
      <td>71</td>
      <td>201933</td>
      <td>False</td>
      <td>0.266</td>
      <td>0.0596</td>
      <td>...</td>
      <td>-18.515</td>
      <td>1</td>
      <td>0.0363</td>
      <td>0.9050</td>
      <td>0.000071</td>
      <td>0.1320</td>
      <td>0.1430</td>
      <td>181.740</td>
      <td>3</td>
      <td>acoustic</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>5vjLSffimiIP26QG5WcN2K</td>
      <td>Chord Overstreet</td>
      <td>Hold On</td>
      <td>Hold On</td>
      <td>82</td>
      <td>198853</td>
      <td>False</td>
      <td>0.618</td>
      <td>0.4430</td>
      <td>...</td>
      <td>-9.681</td>
      <td>1</td>
      <td>0.0526</td>
      <td>0.4690</td>
      <td>0.000000</td>
      <td>0.0829</td>
      <td>0.1670</td>
      <td>119.949</td>
      <td>4</td>
      <td>acoustic</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>113995</th>
      <td>113995</td>
      <td>2C3TZjDRiAzdyViavDJ217</td>
      <td>Rainy Lullaby</td>
      <td>#mindfulness - Soft Rain for Mindful Meditatio...</td>
      <td>Sleep My Little Boy</td>
      <td>21</td>
      <td>384999</td>
      <td>False</td>
      <td>0.172</td>
      <td>0.2350</td>
      <td>...</td>
      <td>-16.393</td>
      <td>1</td>
      <td>0.0422</td>
      <td>0.6400</td>
      <td>0.928000</td>
      <td>0.0863</td>
      <td>0.0339</td>
      <td>125.995</td>
      <td>5</td>
      <td>world-music</td>
    </tr>
    <tr>
      <th>113996</th>
      <td>113996</td>
      <td>1hIz5L4IB9hN3WRYPOCGPw</td>
      <td>Rainy Lullaby</td>
      <td>#mindfulness - Soft Rain for Mindful Meditatio...</td>
      <td>Water Into Light</td>
      <td>22</td>
      <td>385000</td>
      <td>False</td>
      <td>0.174</td>
      <td>0.1170</td>
      <td>...</td>
      <td>-18.318</td>
      <td>0</td>
      <td>0.0401</td>
      <td>0.9940</td>
      <td>0.976000</td>
      <td>0.1050</td>
      <td>0.0350</td>
      <td>85.239</td>
      <td>4</td>
      <td>world-music</td>
    </tr>
    <tr>
      <th>113997</th>
      <td>113997</td>
      <td>6x8ZfSoqDjuNa5SVP5QjvX</td>
      <td>Cesária Evora</td>
      <td>Best Of</td>
      <td>Miss Perfumado</td>
      <td>22</td>
      <td>271466</td>
      <td>False</td>
      <td>0.629</td>
      <td>0.3290</td>
      <td>...</td>
      <td>-10.895</td>
      <td>0</td>
      <td>0.0420</td>
      <td>0.8670</td>
      <td>0.000000</td>
      <td>0.0839</td>
      <td>0.7430</td>
      <td>132.378</td>
      <td>4</td>
      <td>world-music</td>
    </tr>
    <tr>
      <th>113998</th>
      <td>113998</td>
      <td>2e6sXL2bYv4bSz6VTdnfLs</td>
      <td>Michael W. Smith</td>
      <td>Change Your World</td>
      <td>Friends</td>
      <td>41</td>
      <td>283893</td>
      <td>False</td>
      <td>0.587</td>
      <td>0.5060</td>
      <td>...</td>
      <td>-10.889</td>
      <td>1</td>
      <td>0.0297</td>
      <td>0.3810</td>
      <td>0.000000</td>
      <td>0.2700</td>
      <td>0.4130</td>
      <td>135.960</td>
      <td>4</td>
      <td>world-music</td>
    </tr>
    <tr>
      <th>113999</th>
      <td>113999</td>
      <td>2hETkH7cOfqmz3LqZDHZf5</td>
      <td>Cesária Evora</td>
      <td>Miss Perfumado</td>
      <td>Barbincor</td>
      <td>22</td>
      <td>241826</td>
      <td>False</td>
      <td>0.526</td>
      <td>0.4870</td>
      <td>...</td>
      <td>-10.204</td>
      <td>0</td>
      <td>0.0725</td>
      <td>0.6810</td>
      <td>0.000000</td>
      <td>0.0893</td>
      <td>0.7080</td>
      <td>79.198</td>
      <td>4</td>
      <td>world-music</td>
    </tr>
  </tbody>
</table>
<p>89741 rows × 21 columns</p>
</div>



With this cleaning method, we got rid of all the duplicate songs in this dataset!


```python
df.describe()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Unnamed: 0</th>
      <th>popularity</th>
      <th>duration_ms</th>
      <th>danceability</th>
      <th>energy</th>
      <th>key</th>
      <th>loudness</th>
      <th>mode</th>
      <th>speechiness</th>
      <th>acousticness</th>
      <th>instrumentalness</th>
      <th>liveness</th>
      <th>valence</th>
      <th>tempo</th>
      <th>time_signature</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>89741.000000</td>
      <td>89741.000000</td>
      <td>8.974100e+04</td>
      <td>89741.000000</td>
      <td>89741.000000</td>
      <td>89741.000000</td>
      <td>89741.000000</td>
      <td>89741.000000</td>
      <td>89741.000000</td>
      <td>89741.000000</td>
      <td>89741.000000</td>
      <td>89741.000000</td>
      <td>89741.000000</td>
      <td>89741.000000</td>
      <td>89741.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>53479.144148</td>
      <td>33.198438</td>
      <td>2.291418e+05</td>
      <td>0.562166</td>
      <td>0.634458</td>
      <td>5.283549</td>
      <td>-8.499004</td>
      <td>0.636966</td>
      <td>0.087442</td>
      <td>0.328289</td>
      <td>0.173413</td>
      <td>0.216970</td>
      <td>0.469477</td>
      <td>122.058316</td>
      <td>3.897427</td>
    </tr>
    <tr>
      <th>std</th>
      <td>33409.981502</td>
      <td>20.580824</td>
      <td>1.129477e+05</td>
      <td>0.176691</td>
      <td>0.256605</td>
      <td>3.559897</td>
      <td>5.221490</td>
      <td>0.480877</td>
      <td>0.113277</td>
      <td>0.338321</td>
      <td>0.323848</td>
      <td>0.194884</td>
      <td>0.262864</td>
      <td>30.117532</td>
      <td>0.453435</td>
    </tr>
    <tr>
      <th>min</th>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000e+00</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>-49.531000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>23767.000000</td>
      <td>19.000000</td>
      <td>1.730400e+05</td>
      <td>0.450000</td>
      <td>0.457000</td>
      <td>2.000000</td>
      <td>-10.322000</td>
      <td>0.000000</td>
      <td>0.036000</td>
      <td>0.017100</td>
      <td>0.000000</td>
      <td>0.098200</td>
      <td>0.249000</td>
      <td>99.264000</td>
      <td>4.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>50681.000000</td>
      <td>33.000000</td>
      <td>2.132930e+05</td>
      <td>0.576000</td>
      <td>0.676000</td>
      <td>5.000000</td>
      <td>-7.185000</td>
      <td>1.000000</td>
      <td>0.048900</td>
      <td>0.188000</td>
      <td>0.000058</td>
      <td>0.132000</td>
      <td>0.457000</td>
      <td>122.013000</td>
      <td>4.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>80618.000000</td>
      <td>49.000000</td>
      <td>2.642930e+05</td>
      <td>0.692000</td>
      <td>0.853000</td>
      <td>8.000000</td>
      <td>-5.108000</td>
      <td>1.000000</td>
      <td>0.085900</td>
      <td>0.625000</td>
      <td>0.097600</td>
      <td>0.279000</td>
      <td>0.682000</td>
      <td>140.077000</td>
      <td>4.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>113999.000000</td>
      <td>100.000000</td>
      <td>5.237295e+06</td>
      <td>0.985000</td>
      <td>1.000000</td>
      <td>11.000000</td>
      <td>4.532000</td>
      <td>1.000000</td>
      <td>0.965000</td>
      <td>0.996000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>0.995000</td>
      <td>243.372000</td>
      <td>5.000000</td>
    </tr>
  </tbody>
</table>
</div>



This cell gives us a lot of averages, descriptions, and mins and maxes for the dataset given above. The first thing I went to look at is the duration, but it shoudl be noted that it is written in milliseconds. To change milliseconds to minutes, we have to divide the value by 60,000). Let's do that!


```python
(df['duration_ms'].mean())/60000
```




    3.8190302030287158




```python
(df['duration_ms'].max())/60000
```




    87.28825




```python
(df['duration_ms'].std())/60000
```




    1.8824623531681983



With the above calculations, we have some easy to understand data from the dataset! On average, songs were 3.800 minutes (3 minutes and 48 seconds) long, with a standard deviation of 1.788 minutes (1 minute and 47 seconds). The maximum length of a song is 87.288 minutes (87 minutes and 17 seconds), and the minimum was 0 minutes. I did no further calculations for this zero value, considering 0/# = 0.

Now, what song was the longest? Who wrote it? Let's see.


```python
df['duration_ms'].max()
```




    5237295




```python
df['track_id'][df['duration_ms']==Out[80]]
```




    73617    3Cnz3Bu9Wcw8p3kiBTXTxp
    Name: track_id, dtype: object




```python
df['track_name'][df['duration_ms']==Out[80]]
```




    73617    Unity (Voyage Mix) Pt. 1
    Name: track_name, dtype: object




```python
df['artists'][df['duration_ms']==Out[80]]
```




    73617    Tale Of Us
    Name: artists, dtype: object



The longest song found in this dataset is "Unity(Voyage Mix) Pt.1" by the Tale of Us, a duo of artists.

## Now that we went down that rabbit hole...

Let's actually get on with what I wanted to look at in the beginnong of this project! What song is the most popular in this dataset? Who is it by? How long is it? Let's find all this out.


```python
df['popularity'].max()
```




    100




```python
df['track_name'][df['popularity']==Out[84]]
```




    20001    Unholy (feat. Kim Petras)
    Name: track_name, dtype: object




```python
df['artists'][df['popularity']==Out[84]]
```




    20001    Sam Smith;Kim Petras
    Name: artists, dtype: object




```python
df['album_name'][df['popularity']==Out[84]]
```




    20001    Unholy (feat. Kim Petras)
    Name: album_name, dtype: object




```python
df['track_id'][df['popularity']==Out[84]]
```




    20001    3nqQXoyQOWXiESFLlDF1hG
    Name: track_id, dtype: object




```python
df['duration_ms'][df['popularity']==Out[84]]
```




    20001    156943
    Name: duration_ms, dtype: int64




```python
Out[98]/60000
```




    20001    2.615717
    Name: duration_ms, dtype: float64



Results! How lovely. So, in this dataset, 'Unholy' by Sam Smith (feat. Kim Petras) was the most popular song! Personally, I did listen to this song a lot, and now have it on while I am creating this. Absolute banger, if I do say so. 'Unholy' is listed as coming from the album also named 'Unholy', which really means it is a single (or was, before get grouped into the larger album 'Gloria' on Spotify by Sam Smith. This track_id was not included in the dataset, that is why 'Gloria' did not come up as the album name). It is a solid 2.616 minutes long (2 minutes and 37 seconds), and had a popularity score of 100! This is the highest you can get actually!

What about danceability? Energy? Let's go look.


```python
df['danceability'][df['track_id']=='3nqQXoyQOWXiESFLlDF1hG']
```




    20001    0.714
    Name: danceability, dtype: float64




```python
df['energy'][df['track_id']=='3nqQXoyQOWXiESFLlDF1hG']
```




    20001    0.472
    Name: energy, dtype: float64




```python
df['explicit'][df['track_id']=='3nqQXoyQOWXiESFLlDF1hG']
```




    20001    False
    Name: explicit, dtype: bool




```python
df['loudness'][df['track_id']=='3nqQXoyQOWXiESFLlDF1hG']
```




    20001   -7.375
    Name: loudness, dtype: float64




```python
df['mode'][df['track_id']=='3nqQXoyQOWXiESFLlDF1hG']
```




    20001    1
    Name: mode, dtype: int64




```python
df['speechiness'][df['track_id']=='3nqQXoyQOWXiESFLlDF1hG']
```




    20001    0.0864
    Name: speechiness, dtype: float64




```python
df['acousticness'][df['track_id']=='3nqQXoyQOWXiESFLlDF1hG']
```




    20001    0.013
    Name: acousticness, dtype: float64




```python
df['instrumentalness'][df['track_id']=='3nqQXoyQOWXiESFLlDF1hG']
```




    20001    0.000005
    Name: instrumentalness, dtype: float64




```python
df['liveness'][df['track_id']=='3nqQXoyQOWXiESFLlDF1hG']
```




    20001    0.266
    Name: liveness, dtype: float64




```python
df['valence'][df['track_id']=='3nqQXoyQOWXiESFLlDF1hG']
```




    20001    0.238
    Name: valence, dtype: float64




```python
df['tempo'][df['track_id']=='3nqQXoyQOWXiESFLlDF1hG']
```




    20001    131.121
    Name: tempo, dtype: float64




```python
df['time_signature'][df['track_id']=='3nqQXoyQOWXiESFLlDF1hG']
```




    20001    4
    Name: time_signature, dtype: int64




```python
df['track_genre'][df['track_id']=='3nqQXoyQOWXiESFLlDF1hG']
```




    20001    dance
    Name: track_genre, dtype: object



## That is a lot of data. Let's simplify it. 

So here's what we have for 'Unholy' by Sam Smith. 
- Danceability = 0.714
- Energy = 0.472
- Is it explicit? = No
- Loudness = -7.375
- Mode = 1
- Speechiness = 0.0864
- Acousticness = 0.013
- Instrumentalness = 0.000005
- Valence = 0.238
- Tempo = 131.121
- Time Signature = 4
- Track Genre = Dance

What about as a whole? What genre is the most common in this dataset?


```python
count = df['track_genre'].value_counts()
count
```




    acoustic     1000
    alt-rock      999
    tango         999
    ambient       999
    afrobeat      999
                 ... 
    metal         232
    punk          226
    house         210
    indie         134
    reggaeton      74
    Name: track_genre, Length: 113, dtype: int64



The most common genre was acoustic in this dataset, followed by alt-rock, tango, ambient, and afrobeat. At the bottom is reggaeton, with a small 74 songs out of 89741 in this data set (that's 0.0825%!)

Here's a quick breakdown of the others.
- acoustic = 11.143%
- alt-rock = 11.132%
- tango = 11.132%
- ambient = 11.132%
- afrobeat = 11.132%
- metal = 0.239%
- punk = 0.2518%
- house = 0.2340%
- indie = 0.01493%
- reggaeton = 0.0825%


```python
df['energy'].mean()
```




    0.6344578983586125




```python
df['danceability'].mean()
```




    0.5621656734380037




```python
df['popularity'].mean()
```




    33.198437726345816



## A Summary!

So, in trecking through this data, we found out a lot of things! First off, the most popular song in this dataset is 'Unholy' by Sam Smith (feat. Kim Petra). It was a solid 2 minutes and 37 seconds long, fell into the 'dance' genre of music, and much more;

- Danceability = 0.714
- Energy = 0.472
- Is it explicit? = No
Note: It's not EXPLICIT but it is (explicit) in idea (if you know you know)
- Loudness = -7.375
- Mode = 1
- Speechiness = 0.0864
- Acousticness = 0.013
- Instrumentalness = 0.000005
- Valence = 0.238
- Tempo = 131.121
- Time Signature = 4


We also learned that the average length for songs in this dataset is 3 minutes and 48 seconds, with a standard deviation of 1 minute and 47 seconds and a max length of 87 minutes and 17 seconds with 'Unity (Voyage Mix) Pt.1' by Tale of Us.

Last of all, found how common certain genres were...
- acoustic = 11.143%
- alt-rock = 11.132%
- tango = 11.132%
- ambient = 11.132%
- afrobeat = 11.132%
- metal = 0.239%
- punk = 0.2518%
- house = 0.2340%
- indie = 0.01493%
- reggaeton = 0.0825%

...and the average stats for danceability, energy, and popularity!
- Average Danceability = .562
- Average Energy = .634
- Average Popularity = 33.198


```python

```
