# Spotipy_api_1
Code to find the playlist of any artist


    import spotipy
    from spotipy.oauth2 import SpotifyClientCredentials
    # Paste the url of any artist
    birdy_uri = 'https://open.spotify.com/artist/4YRxDV8wJFPHPTeXepOstw?si=4DEBdYMmTGOX-McUafCaqw'
    spotify = spotipy.Spotify(client_credentials_manager=SpotifyClientCredentials(client_id='a07d8991bcf64e8baeb3a18a36eef311',
                                                                                  client_secret='57fbfdab77e74b0abdc86691e2baf1fb'))
    
    results = spotify.artist_albums(birdy_uri, album_type='album')
    albums = results['items']
    while results['next']:
        results = spotify.next(results)
        albums.extend(results['items'])
    
    for album in albums:
        print(album['name'])
