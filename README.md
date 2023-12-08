# DS_2
Data Science Project 2

Spotify Tracks Genre Dataset Research
Considering Spotify Wrapped just came out, I think we can all say we are excited to look at the top Spotify tracks, what genres were the most popular, and overall how certain artists grew throughout this year! In the dataset I have downloaded (from a lovely maharshipandya on kaggle), I will be looking at what the most popular songs were, what genres were the most popular, the danceability and energy of each song, and more!

Here is a list of the main questions I will be looking to answer:

1.) What was the most popular song this year? 2.) Who wrote this song, how long was it, and what album is it in? 3.) What genre was it? 4.) On average, how long were songs this year? 5.) What was the most common genre of song this year? 6.) What was the average danceability of this dataset? Energy?

import pandas as pd
df = pd.read_csv('/Users/summermesler/Downloads/train.csv')
df
<style scoped> .dataframe tbody tr th:only-of-type { vertical-align: middle; }
.dataframe tbody tr th {
    vertical-align: top;
}

.dataframe thead th {
    text-align: right;
}
</style>
Unnamed: 0	track_id	artists	album_name	track_name	popularity	duration_ms	explicit	danceability	energy	...	loudness	mode	speechiness	acousticness	instrumentalness	liveness	valence	tempo	time_signature	track_genre
0	0	5SuOikwiRyPMVoIQDJUgSV	Gen Hoshino	Comedy	Comedy	73	230666	False	0.676	0.4610	...	-6.746	0	0.1430	0.0322	0.000001	0.3580	0.7150	87.917	4	acoustic
1	1	4qPNDBW1i3p13qLCt0Ki3A	Ben Woodward	Ghost (Acoustic)	Ghost - Acoustic	55	149610	False	0.420	0.1660	...	-17.235	1	0.0763	0.9240	0.000006	0.1010	0.2670	77.489	4	acoustic
2	2	1iJBSr7s7jYXzM8EGcbK5b	Ingrid Michaelson;ZAYN	To Begin Again	To Begin Again	57	210826	False	0.438	0.3590	...	-9.734	1	0.0557	0.2100	0.000000	0.1170	0.1200	76.332	4	acoustic
3	3	6lfxq3CG4xtTiEg7opyCyx	Kina Grannis	Crazy Rich Asians (Original Motion Picture Sou...	Can't Help Falling In Love	71	201933	False	0.266	0.0596	...	-18.515	1	0.0363	0.9050	0.000071	0.1320	0.1430	181.740	3	acoustic
4	4	5vjLSffimiIP26QG5WcN2K	Chord Overstreet	Hold On	Hold On	82	198853	False	0.618	0.4430	...	-9.681	1	0.0526	0.4690	0.000000	0.0829	0.1670	119.949	4	acoustic
...	...	...	...	...	...	...	...	...	...	...	...	...	...	...	...	...	...	...	...	...	...
113995	113995	2C3TZjDRiAzdyViavDJ217	Rainy Lullaby	#mindfulness - Soft Rain for Mindful Meditatio...	Sleep My Little Boy	21	384999	False	0.172	0.2350	...	-16.393	1	0.0422	0.6400	0.928000	0.0863	0.0339	125.995	5	world-music
113996	113996	1hIz5L4IB9hN3WRYPOCGPw	Rainy Lullaby	#mindfulness - Soft Rain for Mindful Meditatio...	Water Into Light	22	385000	False	0.174	0.1170	...	-18.318	0	0.0401	0.9940	0.976000	0.1050	0.0350	85.239	4	world-music
113997	113997	6x8ZfSoqDjuNa5SVP5QjvX	Cesária Evora	Best Of	Miss Perfumado	22	271466	False	0.629	0.3290	...	-10.895	0	0.0420	0.8670	0.000000	0.0839	0.7430	132.378	4	world-music
113998	113998	2e6sXL2bYv4bSz6VTdnfLs	Michael W. Smith	Change Your World	Friends	41	283893	False	0.587	0.5060	...	-10.889	1	0.0297	0.3810	0.000000	0.2700	0.4130	135.960	4	world-music
113999	113999	2hETkH7cOfqmz3LqZDHZf5	Cesária Evora	Miss Perfumado	Barbincor	22	241826	False	0.526	0.4870	...	-10.204	0	0.0725	0.6810	0.000000	0.0893	0.7080	79.198	4	world-music
114000 rows × 21 columns

dff = df.dropna()
dff
<style scoped> .dataframe tbody tr th:only-of-type { vertical-align: middle; }
.dataframe tbody tr th {
    vertical-align: top;
}

.dataframe thead th {
    text-align: right;
}
</style>
Unnamed: 0	track_id	artists	album_name	track_name	popularity	duration_ms	explicit	danceability	energy	...	loudness	mode	speechiness	acousticness	instrumentalness	liveness	valence	tempo	time_signature	track_genre
0	0	5SuOikwiRyPMVoIQDJUgSV	Gen Hoshino	Comedy	Comedy	73	230666	False	0.676	0.4610	...	-6.746	0	0.1430	0.0322	0.000001	0.3580	0.7150	87.917	4	acoustic
1	1	4qPNDBW1i3p13qLCt0Ki3A	Ben Woodward	Ghost (Acoustic)	Ghost - Acoustic	55	149610	False	0.420	0.1660	...	-17.235	1	0.0763	0.9240	0.000006	0.1010	0.2670	77.489	4	acoustic
2	2	1iJBSr7s7jYXzM8EGcbK5b	Ingrid Michaelson;ZAYN	To Begin Again	To Begin Again	57	210826	False	0.438	0.3590	...	-9.734	1	0.0557	0.2100	0.000000	0.1170	0.1200	76.332	4	acoustic
3	3	6lfxq3CG4xtTiEg7opyCyx	Kina Grannis	Crazy Rich Asians (Original Motion Picture Sou...	Can't Help Falling In Love	71	201933	False	0.266	0.0596	...	-18.515	1	0.0363	0.9050	0.000071	0.1320	0.1430	181.740	3	acoustic
4	4	5vjLSffimiIP26QG5WcN2K	Chord Overstreet	Hold On	Hold On	82	198853	False	0.618	0.4430	...	-9.681	1	0.0526	0.4690	0.000000	0.0829	0.1670	119.949	4	acoustic
...	...	...	...	...	...	...	...	...	...	...	...	...	...	...	...	...	...	...	...	...	...
113995	113995	2C3TZjDRiAzdyViavDJ217	Rainy Lullaby	#mindfulness - Soft Rain for Mindful Meditatio...	Sleep My Little Boy	21	384999	False	0.172	0.2350	...	-16.393	1	0.0422	0.6400	0.928000	0.0863	0.0339	125.995	5	world-music
113996	113996	1hIz5L4IB9hN3WRYPOCGPw	Rainy Lullaby	#mindfulness - Soft Rain for Mindful Meditatio...	Water Into Light	22	385000	False	0.174	0.1170	...	-18.318	0	0.0401	0.9940	0.976000	0.1050	0.0350	85.239	4	world-music
113997	113997	6x8ZfSoqDjuNa5SVP5QjvX	Cesária Evora	Best Of	Miss Perfumado	22	271466	False	0.629	0.3290	...	-10.895	0	0.0420	0.8670	0.000000	0.0839	0.7430	132.378	4	world-music
113998	113998	2e6sXL2bYv4bSz6VTdnfLs	Michael W. Smith	Change Your World	Friends	41	283893	False	0.587	0.5060	...	-10.889	1	0.0297	0.3810	0.000000	0.2700	0.4130	135.960	4	world-music
113999	113999	2hETkH7cOfqmz3LqZDHZf5	Cesária Evora	Miss Perfumado	Barbincor	22	241826	False	0.526	0.4870	...	-10.204	0	0.0725	0.6810	0.000000	0.0893	0.7080	79.198	4	world-music
113999 rows × 21 columns

df = df.drop_duplicates('track_id')
df
<style scoped> .dataframe tbody tr th:only-of-type { vertical-align: middle; }
.dataframe tbody tr th {
    vertical-align: top;
}

.dataframe thead th {
    text-align: right;
}
</style>
Unnamed: 0	track_id	artists	album_name	track_name	popularity	duration_ms	explicit	danceability	energy	...	loudness	mode	speechiness	acousticness	instrumentalness	liveness	valence	tempo	time_signature	track_genre
0	0	5SuOikwiRyPMVoIQDJUgSV	Gen Hoshino	Comedy	Comedy	73	230666	False	0.676	0.4610	...	-6.746	0	0.1430	0.0322	0.000001	0.3580	0.7150	87.917	4	acoustic
1	1	4qPNDBW1i3p13qLCt0Ki3A	Ben Woodward	Ghost (Acoustic)	Ghost - Acoustic	55	149610	False	0.420	0.1660	...	-17.235	1	0.0763	0.9240	0.000006	0.1010	0.2670	77.489	4	acoustic
2	2	1iJBSr7s7jYXzM8EGcbK5b	Ingrid Michaelson;ZAYN	To Begin Again	To Begin Again	57	210826	False	0.438	0.3590	...	-9.734	1	0.0557	0.2100	0.000000	0.1170	0.1200	76.332	4	acoustic
3	3	6lfxq3CG4xtTiEg7opyCyx	Kina Grannis	Crazy Rich Asians (Original Motion Picture Sou...	Can't Help Falling In Love	71	201933	False	0.266	0.0596	...	-18.515	1	0.0363	0.9050	0.000071	0.1320	0.1430	181.740	3	acoustic
4	4	5vjLSffimiIP26QG5WcN2K	Chord Overstreet	Hold On	Hold On	82	198853	False	0.618	0.4430	...	-9.681	1	0.0526	0.4690	0.000000	0.0829	0.1670	119.949	4	acoustic
...	...	...	...	...	...	...	...	...	...	...	...	...	...	...	...	...	...	...	...	...	...
113995	113995	2C3TZjDRiAzdyViavDJ217	Rainy Lullaby	#mindfulness - Soft Rain for Mindful Meditatio...	Sleep My Little Boy	21	384999	False	0.172	0.2350	...	-16.393	1	0.0422	0.6400	0.928000	0.0863	0.0339	125.995	5	world-music
113996	113996	1hIz5L4IB9hN3WRYPOCGPw	Rainy Lullaby	#mindfulness - Soft Rain for Mindful Meditatio...	Water Into Light	22	385000	False	0.174	0.1170	...	-18.318	0	0.0401	0.9940	0.976000	0.1050	0.0350	85.239	4	world-music
113997	113997	6x8ZfSoqDjuNa5SVP5QjvX	Cesária Evora	Best Of	Miss Perfumado	22	271466	False	0.629	0.3290	...	-10.895	0	0.0420	0.8670	0.000000	0.0839	0.7430	132.378	4	world-music
113998	113998	2e6sXL2bYv4bSz6VTdnfLs	Michael W. Smith	Change Your World	Friends	41	283893	False	0.587	0.5060	...	-10.889	1	0.0297	0.3810	0.000000	0.2700	0.4130	135.960	4	world-music
113999	113999	2hETkH7cOfqmz3LqZDHZf5	Cesária Evora	Miss Perfumado	Barbincor	22	241826	False	0.526	0.4870	...	-10.204	0	0.0725	0.6810	0.000000	0.0893	0.7080	79.198	4	world-music
89741 rows × 21 columns

With this cleaning method, we got rid of all the duplicate songs in this dataset!

df.describe()
<style scoped> .dataframe tbody tr th:only-of-type { vertical-align: middle; }
.dataframe tbody tr th {
    vertical-align: top;
}

.dataframe thead th {
    text-align: right;
}
</style>
Unnamed: 0	popularity	duration_ms	danceability	energy	key	loudness	mode	speechiness	acousticness	instrumentalness	liveness	valence	tempo	time_signature
count	89741.000000	89741.000000	8.974100e+04	89741.000000	89741.000000	89741.000000	89741.000000	89741.000000	89741.000000	89741.000000	89741.000000	89741.000000	89741.000000	89741.000000	89741.000000
mean	53479.144148	33.198438	2.291418e+05	0.562166	0.634458	5.283549	-8.499004	0.636966	0.087442	0.328289	0.173413	0.216970	0.469477	122.058316	3.897427
std	33409.981502	20.580824	1.129477e+05	0.176691	0.256605	3.559897	5.221490	0.480877	0.113277	0.338321	0.323848	0.194884	0.262864	30.117532	0.453435
min	0.000000	0.000000	0.000000e+00	0.000000	0.000000	0.000000	-49.531000	0.000000	0.000000	0.000000	0.000000	0.000000	0.000000	0.000000	0.000000
25%	23767.000000	19.000000	1.730400e+05	0.450000	0.457000	2.000000	-10.322000	0.000000	0.036000	0.017100	0.000000	0.098200	0.249000	99.264000	4.000000
50%	50681.000000	33.000000	2.132930e+05	0.576000	0.676000	5.000000	-7.185000	1.000000	0.048900	0.188000	0.000058	0.132000	0.457000	122.013000	4.000000
75%	80618.000000	49.000000	2.642930e+05	0.692000	0.853000	8.000000	-5.108000	1.000000	0.085900	0.625000	0.097600	0.279000	0.682000	140.077000	4.000000
max	113999.000000	100.000000	5.237295e+06	0.985000	1.000000	11.000000	4.532000	1.000000	0.965000	0.996000	1.000000	1.000000	0.995000	243.372000	5.000000
This cell gives us a lot of averages, descriptions, and mins and maxes for the dataset given above. The first thing I went to look at is the duration, but it shoudl be noted that it is written in milliseconds. To change milliseconds to minutes, we have to divide the value by 60,000). Let's do that!

(df['duration_ms'].mean())/60000
3.8190302030287158
(df['duration_ms'].max())/60000
87.28825
(df['duration_ms'].std())/60000
1.8824623531681983
With the above calculations, we have some easy to understand data from the dataset! On average, songs were 3.800 minutes (3 minutes and 48 seconds) long, with a standard deviation of 1.788 minutes (1 minute and 47 seconds). The maximum length of a song is 87.288 minutes (87 minutes and 17 seconds), and the minimum was 0 minutes. I did no further calculations for this zero value, considering 0/# = 0.

Now, what song was the longest? Who wrote it? Let's see.

df['duration_ms'].max()
5237295
df['track_id'][df['duration_ms']==Out[80]]
73617    3Cnz3Bu9Wcw8p3kiBTXTxp
Name: track_id, dtype: object
df['track_name'][df['duration_ms']==Out[80]]
73617    Unity (Voyage Mix) Pt. 1
Name: track_name, dtype: object
df['artists'][df['duration_ms']==Out[80]]
73617    Tale Of Us
Name: artists, dtype: object
The longest song found in this dataset is "Unity(Voyage Mix) Pt.1" by the Tale of Us, a duo of artists.

Now that we went down that rabbit hole...
Let's actually get on with what I wanted to look at in the beginnong of this project! What song is the most popular in this dataset? Who is it by? How long is it? Let's find all this out.

df['popularity'].max()
100
df['track_name'][df['popularity']==Out[84]]
20001    Unholy (feat. Kim Petras)
Name: track_name, dtype: object
df['artists'][df['popularity']==Out[84]]
20001    Sam Smith;Kim Petras
Name: artists, dtype: object
df['album_name'][df['popularity']==Out[84]]
20001    Unholy (feat. Kim Petras)
Name: album_name, dtype: object
df['track_id'][df['popularity']==Out[84]]
20001    3nqQXoyQOWXiESFLlDF1hG
Name: track_id, dtype: object
df['duration_ms'][df['popularity']==Out[84]]
20001    156943
Name: duration_ms, dtype: int64
Out[98]/60000
20001    2.615717
Name: duration_ms, dtype: float64
Results! How lovely. So, in this dataset, 'Unholy' by Sam Smith (feat. Kim Petras) was the most popular song! Personally, I did listen to this song a lot, and now have it on while I am creating this. Absolute banger, if I do say so. 'Unholy' is listed as coming from the album also named 'Unholy', which really means it is a single (or was, before get grouped into the larger album 'Gloria' on Spotify by Sam Smith. This track_id was not included in the dataset, that is why 'Gloria' did not come up as the album name). It is a solid 2.616 minutes long (2 minutes and 37 seconds), and had a popularity score of 100! This is the highest you can get actually!

What about danceability? Energy? Let's go look.

df['danceability'][df['track_id']=='3nqQXoyQOWXiESFLlDF1hG']
20001    0.714
Name: danceability, dtype: float64
df['energy'][df['track_id']=='3nqQXoyQOWXiESFLlDF1hG']
20001    0.472
Name: energy, dtype: float64
df['explicit'][df['track_id']=='3nqQXoyQOWXiESFLlDF1hG']
20001    False
Name: explicit, dtype: bool
df['loudness'][df['track_id']=='3nqQXoyQOWXiESFLlDF1hG']
20001   -7.375
Name: loudness, dtype: float64
df['mode'][df['track_id']=='3nqQXoyQOWXiESFLlDF1hG']
20001    1
Name: mode, dtype: int64
df['speechiness'][df['track_id']=='3nqQXoyQOWXiESFLlDF1hG']
20001    0.0864
Name: speechiness, dtype: float64
df['acousticness'][df['track_id']=='3nqQXoyQOWXiESFLlDF1hG']
20001    0.013
Name: acousticness, dtype: float64
df['instrumentalness'][df['track_id']=='3nqQXoyQOWXiESFLlDF1hG']
20001    0.000005
Name: instrumentalness, dtype: float64
df['liveness'][df['track_id']=='3nqQXoyQOWXiESFLlDF1hG']
20001    0.266
Name: liveness, dtype: float64
df['valence'][df['track_id']=='3nqQXoyQOWXiESFLlDF1hG']
20001    0.238
Name: valence, dtype: float64
df['tempo'][df['track_id']=='3nqQXoyQOWXiESFLlDF1hG']
20001    131.121
Name: tempo, dtype: float64
df['time_signature'][df['track_id']=='3nqQXoyQOWXiESFLlDF1hG']
20001    4
Name: time_signature, dtype: int64
df['track_genre'][df['track_id']=='3nqQXoyQOWXiESFLlDF1hG']
20001    dance
Name: track_genre, dtype: object
That is a lot of data. Let's simplify it.
So here's what we have for 'Unholy' by Sam Smith.

Danceability = 0.714
Energy = 0.472
Is it explicit? = No
Loudness = -7.375
Mode = 1
Speechiness = 0.0864
Acousticness = 0.013
Instrumentalness = 0.000005
Valence = 0.238
Tempo = 131.121
Time Signature = 4
Track Genre = Dance
What about as a whole? What genre is the most common in this dataset?

count = df['track_genre'].value_counts()
count
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

acoustic = 11.143%
alt-rock = 11.132%
tango = 11.132%
ambient = 11.132%
afrobeat = 11.132%
metal = 0.239%
punk = 0.2518%
house = 0.2340%
indie = 0.01493%
reggaeton = 0.0825%
df['energy'].mean()
0.6344578983586125
df['danceability'].mean()
0.5621656734380037
df['popularity'].mean()
33.198437726345816
A Summary!
So, in trecking through this data, we found out a lot of things! First off, the most popular song in this dataset is 'Unholy' by Sam Smith (feat. Kim Petra). It was a solid 2 minutes and 37 seconds long, fell into the 'dance' genre of music, and much more;

Danceability = 0.714
Energy = 0.472
Is it explicit? = No Note: It's not EXPLICIT but it is (explicit) in idea (if you know you know)
Loudness = -7.375
Mode = 1
Speechiness = 0.0864
Acousticness = 0.013
Instrumentalness = 0.000005
Valence = 0.238
Tempo = 131.121
Time Signature = 4
We also learned that the average length for songs in this dataset is 3 minutes and 48 seconds, with a standard deviation of 1 minute and 47 seconds and a max length of 87 minutes and 17 seconds with 'Unity (Voyage Mix) Pt.1' by Tale of Us.

Last of all, found how common certain genres were...

acoustic = 11.143%
alt-rock = 11.132%
tango = 11.132%
ambient = 11.132%
afrobeat = 11.132%
metal = 0.239%
punk = 0.2518%
house = 0.2340%
indie = 0.01493%
reggaeton = 0.0825%
...and the average stats for danceability, energy, and popularity!

Average Danceability = .562
Average Energy = .634
Average Popularity = 33.198
