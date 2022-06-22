CREATE TABLE IF NOT EXISTS artists (
    id SERIAL PRIMARY KEY,
    name VARCHIAR(30) NOT NULL
);

CREATE TABLE IF NOT EXISTS albums (
    id SERIAL PRIMARY KEY,
    title VARCHAR(30) NOT NULL,
    date NUMERIC NOT NULL
);

CREATE TABLE IF NOT EXISTS tracks (
    id SERIAL PRIMARY KEY,
    album_id INTEGER REFERENCES albums(id),
    title VARCHAR(30) NOT NULL,
    duration INTEGER NOT NULL
);

CREATE TABLE IF NOT EXISTS generes (
    id SERIAL PRIMARY KEY,
    name VARCHAR(30) NOT NULL
);

CREATE TABLE IF NOT EXISTS collections (
    id SERIAL PRIMARY KEY,
    name VARCHAR(30) NOT NULL,
    date INTEGER NOT NULL
);

CREATE TABLE IF NOT EXISTS artistGenres (
    id SERIAL PRIMARY KEY,
    artist_id INTEGER REFERENCES artists(id),
    genere_id INTEGER REFERENCES generes(id)
);

CREATE TABLE IF NOT EXISTS artistAlbums (
    id SERIAL PRIMARY KEY,
    artist_id INTEGER REFERENCES artists(id),
    album_id INTEGER REFERENCES albums(id)
);

CREATE TABLE IF NOT EXISTS trackCollection (
    id SERIAL PRIMARY KEY,
    track_id INTEGER REFERENCES tracks(id),
    collection_id INTEGER REFERENCES collections(id)
);
