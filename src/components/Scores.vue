<template>
    <div class="container">
        <div class="top-score">Top Scores of the Day</div>
        <div class="scoreboard header">
            <div class="players">Player Name</div>
            <div class="games-won">Games Won</div>
            <div class="games-lost">Games Lost</div>
            <div class="games-drawn">Games Drawn</div>
            <div class="games-played">Games Played</div>
        </div>
        <div class="scoreboard" v-for="user in users" :key="user.id">
            <div class="players">
                {{user.playerName}}
            </div>
            <div class="games-won">
                {{user.games.gamesWon}}
            </div>
            <div class="games-lost">
                {{user.games.gamesLost}}
            </div>
            <div class="games-drawn">
                {{user.games.gamesDrawn}}
            </div>
            <div class="games-played">
                {{user.games.gamesPlayed}}
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Scores",
        data () {
          return {
              users: [
                  {
                      id: 3,
                      playerName: 'Beanz',
                      lastLogin: Date.now(),
                      games: {
                          gamesPlayed: 100,
                          gamesWon: 32,
                          gamesLost: 9,
                          gamesDrawn: 11
                      }
                  },
                  {
                      id: 32,
                      playerName: 'Sven',
                      lastLogin: Date.now(),
                      games: {
                          gamesPlayed: 52,
                          gamesWon: 25,
                          gamesLost: 13,
                          gamesDrawn: 14
                      }
                  },
                  {
                      id: 5,
                      playerName: 'Taco Jim',
                      lastLogin: Date.now(),
                      games: {
                          gamesPlayed: 19,
                          gamesWon: 12,
                          gamesLost: 3,
                          gamesDrawn: 4
                      }
                  }
              ]

          }
        },
    }
</script>

<style scoped>
    .container {
        width: 0.5fr;
        margin: 0 20px;
        padding-top: 30px;
        font-family: Georgia, sans-serif;
    }

    .scoreboard{
        display: flex;
        flex-direction: row;
    }

    .header {
        height: 30px;
        display: flex;
        align-items: center;
        background-color: #016CFF;
        color: white;
        border-radius: 5px;
    }

    .top-score {
        padding-bottom: 10px;
    }

    .players {
        width: 250px;
    }

    .games-won,
    .games-lost,
    .games-drawn,
    .games-played{
        width: 137px;
    }

</style>

