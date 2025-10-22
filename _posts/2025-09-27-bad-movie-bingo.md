# Bad Movie Bingo: A little project for fun

Today, I wrapped up v0 of a web app I made for a friend’s birthday. The project, called Bad Movie Bingo, started as an idea I mocked up in Canva.

<img src="/images/bad-movie-canva.png" alt="bad movie bingo canva design" width="400px" class="center" />

## Why Bad Movie Bingo?

My friend Chris is super into collecting and watching really bad movies. And I mean *really* bad. He likes to host "Bad Movie Nights" where he invites a bunch of friends to watch a movie from his collection. Chris will screen a handful of movies before asking for a volunteer to choose a movie that speaks to them. At the last Bad Movie Night, we ended up watching a movie called *The Last Vampire on Earth* from 2009, and it was bad alright... 

I actually wasn’t originally planning on making an app. I was going to go to the public library to print about 20 copies of bingo grids with tiles like “Ketchup Blood”,” “Poor CGI,” and “Continuity Error.” Then, I was going to laminate the copies and get some EXPO markers. But, my friend’s birthday party was approaching quicker than usual, and I thought why not make a simple Next.js app in a few hours? It's been a while since I worked on an app, and this didn't happen without a little vibe coding with ChatGPT/Copilot.

## High-level flow

### Landing page
The first page of the web app is a landing page where players can enter or create a room code with a nickname.

<img src="/images/bmb_landingpage.png" alt="bad movie bingo landing page" width="200" class="center" />

### Game room
Once the player is in a game room, they'll be able to see their bingo card, generated from a randomized array of 25 strings in a 5x5 grid.

<img src="/images/bmb_bingocard1.png" alt="bad movie bingo card" class="center" />

### Bingo detection

Each tap of a bingo square updates the database, and a bingo check is made. When a player gets bingo, they and any other players in the game room will be alerted with a celebratory message.

<img src="/images/bmb_bingo_detection.png" alt="bad movie bingo winner" width="600" class="center" />

## Implementation

### Frontend (Webapp)

I made the frontend with React/Next.js, TailwindCSS, and Vercel for free hosting and instant deployment. This was my first time using TailwindCSS---I had only ever used plain CSS. This was also my first time using Vercel, which was a super smooth experience. 

### Real-time database

I used Firebase for the bingo database, handling game rooms, users, cards, and selections. I've used Firebase before in a Mobile and Ubiquitous Computing class where some friends and I made a dating app (good times). I used the following functions from Cloud Firestore to interact with and manage data within the Firestore database:

- `doc`

  Creates a `DocumentReference` object that points to a document within a collection of a Firestore database.

- `setDoc`

  Creates or completely overwrites a document at a specified `DocumentReference`.

- `getDoc`

  Retrieves a single document's data from Firestore and returns a `DocumentSnapshot` object containing the document's data.
- `onSnapshot`

  Provides real-time updates for a document or a query. Attaches a listener to a `DocumentReference` or `Query` and executes a callback function whenever the data changes. This is what makes the app reactive to changes in the database without needing to manually fetch the data.

- `updateDoc`
  
  Updates specific fields in an existing document without overwriting the entire document.

You can find these functions in the main game .js file for detecting bingo and broadcasting notifications. Visit the [Cloud Firestore docs](https://firebase.google.com/docs/firestore/query-data/get-data) for more information on getting data and real-time updates with Firebase.

## Results

I'm pretty happy with how this v0 came out. It didn't take super long to set up, and in the future I'll be looking into making the tiles more customizable for the user who creates a game. Two main steps I plan on taking:

1. Spend more time on the styling to make the design more accessible, e.g., change the text color to white when the the user selects tiles.
2. Try incorporating AI to come up with tile ideas based on the title of a movie entered. I plan on looking into generative text models served by HuggingFace. 

I'd give the user the following options when they get to the landing page:

- Create a new game.
- Join an existing game.

Creating a new game will lead to a screen with the following options:

- Create tiles from scratch.

  When selected, a screen with blank, editable textboxes will appear. When the options are to the game creator's liking, the creator can submit.

- Use AI to generate tiles.

  After selecting this option, the user will be prompted to submit a movie title. The next screen will be editable textboxes populated with AI-generated bingo tiles. The user will submit when the options are to their liking, with the option to generate more options per option they'd like to change.

  All in all, this was a fun experience, and I'm excited to share the project with my friend today! 
    










