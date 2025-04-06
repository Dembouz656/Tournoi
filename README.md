<!DOCTYPE html>
<html lang="fr">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Performics - CUP</title>
    <link rel="stylesheet" href="styles.css">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/fullcalendar@3.2.0/dist/fullcalendar.min.css" />
    <style>
        /* Basic styles for page layout */
        body {
            font-family: 'Arial', sans-serif;
            background-color: #f4f4f9;
            margin: 0;
            padding: 0;
        }

        header {
            background-color: #007bff;
            color: white;
            padding: 10px 0;
            text-align: center;
        }

        header img {
            height: 50px;
            margin-bottom: 10px;
        }

        header h1 {
            font-size: 2rem;
            font-weight: bold;
        }

        .navbar {
            background-color: #007bff;
            padding: 10px;
            text-align: center;
        }

        .navbar a {
            color: white;
            text-decoration: none;
            padding: 10px 20px;
            margin: 0 10px;
            font-size: 1.2rem;
        }

        .navbar a:hover {
            background-color: #0056b3;
            border-radius: 5px;
        }

        .container {
            padding: 20px;
        }

        /* Custom styles for calendar */
        #calendar {
            width: 100%;
            margin-top: 20px;
        }

        .form-container {
            margin-top: 20px;
        }

        button {
            background-color: #007bff;
            color: white;
            border: none;
            padding: 10px 20px;
            font-size: 1rem;
            cursor: pointer;
            border-radius: 5px;
            margin-top: 10px;
        }

        button:hover {
            background-color: #0056b3;
        }
    </style>
</head>

<body>
    <header>
        <img src="Performics.jpeg" alt="Logo Performics">
        <h1>Performics - Cup</h1>
    </header>

    <!-- Navbar -->
    <div class="navbar">
        <a href="about.html">À propos</a>
        <a href="filiere.html">Filière</a>
        <a href="calendrier.html">Calendrier</a>
        <a href="resultats.html">Résultats</a>
        <a href="reglement.html">Règlement</a>
        <a href="contact.html">Contact</a>
    </div>

    <div class="container">
        <h1>Performics_Cup - Gestion du Tournoi</h1>

        <!-- Section pour afficher le calendrier -->
        <section id="calendrier">
            <h2>Calendrier</h2>
            <div id="calendar"></div>
        </section>

        <!-- Section pour gérer les matchs -->
        <section id="matchs">
            <h2>Gestion des matchs</h2>
            <div class="form-container">
                <form id="form-ajout-match">
                    <label for="match-date">Date du match:</label>
                    <input type="datetime-local" id="match-date" required>
                    <label for="match-equipe1">Équipe 1:</label>
                    <input type="text" id="match-equipe1" placeholder="Nom de l'équipe 1" required>
                    <label for="match-equipe2">Équipe 2:</label>
                    <input type="text" id="match-equipe2" placeholder="Nom de l'équipe 2" required>
                    <button type="submit">Ajouter le match</button>
                </form>
            </div>

            <h3>Matchs à venir</h3>
            <ul id="matchs-a-venir"></ul>

            <h3>Matchs joués</h3>
            <ul id="matchs-joues"></ul>
        </section>
    </div>

    <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/fullcalendar@3.2.0/dist/fullcalendar.min.js"></script>
    <script>
        // Calendar initialization
        $(document).ready(function () {
            $('#calendar').fullCalendar({
                events: [
                    // Example event format
                    {
                        title: 'Match 1',
                        start: '2025-04-10T15:00:00',
                        description: 'Match entre L2 Informatique et L2 Gestion A',
                    },
                    {
                        title: 'Match 2',
                        start: '2025-04-12T16:00:00',
                        description: 'Match entre L3 Info/Gestion et L2 Gestion B',
                    },
                ],
                eventClick: function (event) {
                    alert('Détails du match : ' + event.description);
                },
            });
        });

        // Handle form submission to add a match
        document.getElementById('form-ajout-match').addEventListener('submit', function (e) {
            e.preventDefault();
            let date = document.getElementById('match-date').value;
            let equipe1 = document.getElementById('match-equipe1').value;
            let equipe2 = document.getElementById('match-equipe2').value;
            let match = { date, equipe1, equipe2 };

            // Add match to upcoming matches
            let upcomingMatchesList = document.getElementById('matchs-a-venir');
            let li = document.createElement('li');
            li.innerHTML = `${equipe1} vs ${equipe2} - Date: ${date}`;
            upcomingMatchesList.appendChild(li);

            // Clear form fields
            document.getElementById('match-date').value = '';
            document.getElementById('match-equipe1').value = '';
            document.getElementById('match-equipe2').value = '';
        });

        // Example for managing played matches
        function addPlayedMatch(equipe1, equipe2, date) {
            let playedMatchesList = document.getElementById('matchs-joues');
            let li = document.createElement('li');
            li.innerHTML = `${equipe1} vs ${equipe2} - Date: ${date}`;
            playedMatchesList.appendChild(li);
        }

        // Add a played match (example)
        addPlayedMatch('L2 Informatique', 'L2 Gestion A', '2025-04-08');
    </script>

</body>

</html>
