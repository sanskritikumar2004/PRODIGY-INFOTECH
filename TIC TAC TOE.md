def print_board(board):
    print("\n")
    for i in range(3):
        print(" | ".join(board[i]))
        if i < 2:
            print("-" * 5)
    print("\n")

def check_winner(board):
    # Check rows and columns
    for i in range(3):
        if board[i][0] == board[i][1] == board[i][2] != " ":
            return board[i][0]
        if board[0][i] == board[1][i] == board[2][i] != " ":
            return board[0][i]

    # Check diagonals
    if board[0][0] == board[1][1] == board[2][2] != " ":
        return board[0][0]
    if board[0][2] == board[1][1] == board[2][0] != " ":
        return board[0][2]

    return None

def is_full(board):
    return all(cell != " " for row in board for cell in row)

def tic_tac_toe():
    while True:
        board = [[" " for _ in range(3)] for _ in range(3)]
        current_player = "X"
        winner = None

        print("Welcome to Tic Tac Toe!")
        print_board(board)

        while True:
            try:
                move = int(input(f"Player {current_player}, choose your move (1-9): ")) - 1
                row, col = divmod(move, 3)

                if board[row][col] != " ":
                    print("Cell already taken! Try again.")
                    continue

                board[row][col] = current_player
                print_board(board)

                winner = check_winner(board)
                if winner:
                    print(f"🎉 Player {winner} wins! 🎉")
                    break

                if is_full(board):
                    print("It's a draw!")
                    break

                current_player = "O" if current_player == "X" else "X"
            except (ValueError, IndexError):
                print("Invalid input! Please enter a number from 1 to 9.")

        again = input("Do you want to play again? (y/n): ").lower()
        if again != "y":
            print("Thanks for playing!")
            break

if __name__ == "__main__":
    tic_tac_toe()
