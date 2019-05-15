<template>
    <div class="container">
        <div class="header" v-if="winnerFlag">{{winner}}</div>
        <div class="header" v-else>It is {{playerTurn ? '🌮' : '🍔'}} turn.</div>
        <div class="game-rows" v-for="(rows, indexRow) in board">
            <div class="game-columns" v-for="(column, indexCol) in rows">
                <button @click="playerClick(indexRow, indexCol)">
                    {{column === null ? '' : (column ? '🌮' : '🍔')}}</button>
            </div>
        </div>
        <button @click="restartGame" class="btn-submit">Restart Game</button>
        <div class="note">Note: You can override another players spot</div>
    </div>
</template>

<script>
    export default {
        name: "Gameboard",
        props: {
            boardProp: Number
        },
        data () {
            return {
                boardSize: this.boardProp,
                board: [],
                playerTurn: true,
                diagonalUpCheck: [],
                diagonalDownCheck: [],
                rowCheck: [],
                colCheck: [],
                winner: '',
                winnerFlag: false
            }
        },
        methods: {
            restartGame() {
                this.board = [...Array(this.boardSize)].map(() => Array(this.boardSize).fill(null));
                this.playerTurn = true;
                this.winnerFlag = false;
            },
            playerClick(row, column) {
                if (this.playerTurn){
                    this.board[row].splice(column, 1, true);
                } else {
                    this.board[row].splice(column, 1, false);
                }
                this.checkBoard();
                this.playerTurn = !this.playerTurn;
            },
            allEquals(arr, check) {
                return arr.every(v => v === check);
            },
            winCheck(inputArr) {
                if(inputArr.includes(null) === true){
                    // pass
                }else if(this.allEquals(inputArr, false) === true){
                    this.winner = "Hamburger Wins!";
                    this.winnerFlag = true;
                }else if(this.allEquals(inputArr, true) === true) {
                    this.winner = "Taco Wins!";
                    this.winnerFlag = true;
                }else{
                    // pass
                }
            },
            checkBoard(){
                // CheckBoard Function to be called @change
                for(let i = 0; i < this.board.length; i++){
                    // Check Rows
                    this.rowCheck = this.board[i];
                    this.winCheck(this.rowCheck);

                    // Check Columns
                    this.columnCheck = this.board.map(a => a[i]);
                    this.winCheck(this.columnCheck);

                    // Create Diagonal Down value to array
                    this.diagonalUpCheck.push(this.board[i][i]);

                    // Push Diagonal Up value to array
                    this.diagonalDownCheck.push(this.board[(this.board.length - 1 - i)][i]);
                }
                this.winCheck(this.diagonalUpCheck);
                this.winCheck(this.diagonalDownCheck);
                this.diagonalUpCheck = [];
                this.diagonalDownCheck = [];
            }
        },
        created(){
            this.board = [...Array(this.boardSize)].map(() => Array(this.boardSize).fill(null));
        }
    }
</script>

<style scoped>
    .container {
        display: flex;
        flex-direction: column;

    }
    .game-rows {
        display: flex;
        flex-direction: row;
        justify-content: center;
    }

    button {
        width: 75px;
        height: 50px;
        cursor: pointer;
        font-size: 20px;
    }
    .btn-submit {
        width: 300px;
        font-family: Georgia, sans-serif;
        background-color: #016CFF;
        color: white;
        text-align: center;
        text-decoration: none;
        font-size: 14px;
        border-radius: 8px;
        box-shadow: 1px 1px #404040;
        border: none;
        align-self: center;
        margin-top: 20px;
    }
    .header {
        font-size: 20px;
    }
    .note {
        font-family: Georgia, sans-serif;
        margin-top: 25px;
    }
</style>