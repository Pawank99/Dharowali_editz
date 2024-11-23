<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dharowali_editz - Edited Videos</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f9;
            color: #333;
        }
        header {
            background-color: #8e44ad;
            color: #fff;
            padding: 20px;
            text-align: center;
        }
        .container {
            padding: 20px;
            text-align: center;
        }
        .button {
            display: inline-block;
            padding: 10px 20px;
            margin: 10px;
            background-color: #8e44ad;
            color: white;
            text-decoration: none;
            border-radius: 5px;
            transition: background-color 0.3s;
        }
        .button:hover {
            background-color: #5e3370;
        }
        footer {
            margin-top: 20px;
            text-align: center;
            color: #666;
        }
        .hidden {
            display: none;
            margin-top: 20px;
        }
        #singers-buttons {
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <header>
        <h1>Welcome to Dharowali_editz</h1>
        <p>Creative Edited Videos by <strong>Pawan</strong></p>
    </header>

    <div class="container">
        <h2>About Dharowali_editz</h2>
        <p>Dharowali_editz is an Instagram page that showcases creatively edited videos. Follow us for amazing content!</p>

        <a class="button" href="https://www.instagram.com/dharowali_editz/" target="_blank">Visit Instagram Page</a>
        <button class="button" id="showOwner">Show Owner's Name</button>

        <!-- Top Singers Button -->
        <button class="button" id="topSingersBtn">Top Singers</button>

        <!-- Hidden Singer Buttons -->
        <div id="singers-buttons" class="hidden">
            <button class="button" id="sidhuMooseWalaBtn">Sidhu Moose Wala</button>
            <button class="button" id="karanAujlaBtn">Karan Aujla</button>
            <button class="button" id="babbuMaanBtn">Babbu Maan</button>
        </div>

        <!-- Voting buttons -->
        <div id="voting-buttons" class="hidden">
            <button class="button" id="sidhuVoteBtn">Vote for Sidhu Moose Wala</button>
            <button class="button" id="karanVoteBtn">Vote for Karan Aujla</button>
            <button class="button" id="babbuVoteBtn">Vote for Babbu Maan</button>
        </div>

        <!-- Locker Button -->
        <button class="button" id="lockerBtn">Locker (Votes)</button>
    </div>

    <footer>
        <p>Copyright &copy; 2024 Dharowali_editz | Managed by Pawan</p>
    </footer>

    <script>
        // Initialize vote counts from localStorage
        if (!localStorage.getItem("votes")) {
            localStorage.setItem("votes", JSON.stringify({ sidhu: 0, karan: 0, babbu: 0 }));
        }

        // Initialize sessionStorage to track voting status
        if (!sessionStorage.getItem("voted")) {
            sessionStorage.setItem("voted", "false");
        }

        // Toggle the visibility of the Top Singers buttons
        document.getElementById("topSingersBtn").addEventListener("click", function () {
            const singersButtons = document.getElementById("singers-buttons");
            singersButtons.classList.toggle("hidden");
            document.getElementById("voting-buttons").classList.toggle("hidden");
        });

        // Handle voting logic for Sidhu, Karan, and Babbu
        document.getElementById("sidhuVoteBtn").addEventListener("click", function () {
            if (sessionStorage.getItem("voted") === "false") {
                updateVote("sidhu");
                sessionStorage.setItem("voted", "true"); // Prevent multiple votes in one session
            } else {
                alert("You have already voted. Refresh the page to vote again.");
            }
        });

        document.getElementById("karanVoteBtn").addEventListener("click", function () {
            if (sessionStorage.getItem("voted") === "false") {
                updateVote("karan");
                sessionStorage.setItem("voted", "true"); // Prevent multiple votes in one session
            } else {
                alert("You have already voted. Refresh the page to vote again.");
            }
        });

        document.getElementById("babbuVoteBtn").addEventListener("click", function () {
            if (sessionStorage.getItem("voted") === "false") {
                updateVote("babbu");
                sessionStorage.setItem("voted", "true"); // Prevent multiple votes in one session
            } else {
                alert("You have already voted. Refresh the page to vote again.");
            }
        });

        function updateVote(artist) {
            const votes = JSON.parse(localStorage.getItem("votes"));
            votes[artist]++;
            localStorage.setItem("votes", JSON.stringify(votes));
            alert(`You voted for ${artist.charAt(0).toUpperCase() + artist.slice(1)}!`);
        }

        // Locker button functionality with password
        document.getElementById("lockerBtn").addEventListener("click", function () {
            const password = prompt("Enter the password to view the votes:");
            if (password === "1234") {
                const votes = JSON.parse(localStorage.getItem("votes"));
                alert(`Votes:\nSidhu Moose Wala: ${votes.sidhu}\nKaran Aujla: ${votes.karan}\nBabbu Maan: ${votes.babbu}`);
            } else {
                alert("Incorrect password!");
            }
        });

        // Display information for Sidhu Moose Wala
        document.getElementById("sidhuMooseWalaBtn").addEventListener("click", function () {
            document.getElementById("singerInfo").innerHTML = `
                <h3>Sidhu Moose Wala</h3>
                <p>Shubhdeep Singh Sidhu (11 June 1993 – 29 May 2022), known professionally as Sidhu Moose Wala, was an Indian singer and rapper. He worked predominantly in Punjabi-language music and cinema. Moose Wala is considered to be one of the most influential and successful Punjabi rappers of all time and to many, amongst the most controversial Punjabi artists of all time.</p>
                <p>In 2020, Moose Wala was named by The Guardian among 50 up-and-coming artists. He also became the first Punjabi and Indian singer to perform at Wireless Festival and won four awards at the Brit Asia TV Music Awards.</p>
                <p>Moose Wala rose to mainstream popularity with his track "So High". His debut album "PBX 1" peaked at number 66 on the Billboard Canadian Albums chart. He has the most number-one singles on the Billboard India Songs chart.</p>
            `;
            document.getElementById("singerInfo").classList.remove("hidden");
        });

        // Display information for Karan Aujla
        document.getElementById("karanAujlaBtn").addEventListener("click", function () {
            document.getElementById("singerInfo").innerHTML = `
                <h3>Karan Aujla</h3>
                <p>Jaskaran Singh Aujla (born 18 January 1997) is an Indian singer, rapper, and songwriter based in Canada who is primarily associated with Punjabi music. His debut album "Bacthafucup" peaked at number 20 on the Billboard Canadian Albums chart and 34th on the New Zealand albums chart.</p>
                <p>Aujla is known for his numerous tracks which have charted on the UK Asian chart and the Global YouTube music chart. He was named the Largest Digital Artist 2021 on Spotify and has become a prominent figure in the Punjabi music industry.</p>
                <p>He rose to popularity with tracks like "Yaarian Ch Fikk", "Unity", "Alcohol 2", "Lafaafe", and his chart-topping hit "Don't Worry".</p>
            `;
            document.getElementById("singerInfo").classList.remove("hidden");
        });

        // Display information for Babbu Maan
        document.getElementById("babbuMaanBtn").addEventListener("click", function () {
            document.getElementById("singerInfo").innerHTML = `
                <h3>Babbu Maan</h3>
                <p>Tejinder Singh "Babbu" Maan (born 29 March 1975) is an Indian singer-songwriter, music director, actor, and film producer, most notably recognized for his work in Punjabi music and films.</p>
                <p>Since 1999, Maan has released eight studio albums, six compilation albums, and has written screenplays for, acted in, and produced Punjabi films. He has significantly contributed to regional and Bollywood film soundtracks.</p>
                <p>Maan is considered one of the most iconic figures in the Punjabi music scene and is also the ambassador for One Hope, One Chance, a non-profit organization based in Punjab.</p>
            `;
            document.getElementById("singerInfo").classList.remove("hidden");
        });

        // Add interactivity to show owner's name
        document.getElementById("showOwner").addEventListener("click", function () {
            alert("The page is owned and managed by Pawan.");
        });
    </script>
</body>
</html>
