import random

# Define the maze as a list of lists
maze = [
    ['#', '#', '#', '#', '#', '#', '#', '#', '#', '#'],
    ['#', ' ', ' ', ' ', '#', ' ', ' ', ' ', ' ', '#'],
    ['#', ' ', '#', ' ', '#', ' ', '#', '#', ' ', '#'],
    ['#', ' ', '#', ' ', ' ', ' ', ' ', '#', ' ', '#'],
    ['#', ' ', '#', '#', '#', '#', ' ', '#', ' ', '#'],
    ['#', ' ', ' ', ' ', ' ', '#', ' ', ' ', ' ', '#'],
    ['#', '#', '#', '#', ' ', '#', '#', '#', '#', '#'],
    ['#', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', '#'],
    ['#', '#', '#', '#', '#', '#', '#', '#', 'E', '#']
]

# Define player's starting position
player_row = 1
player_col = 1

# Define trap position
trap_row = random.randint(1, 7)
trap_col = random.randint(1, 7)

# Define treasure position
treasure_row = 8
treasure_col = 8

# Main game loop
while True:
    # Print the maze
    for row in maze:
        print(''.join(row))
    
    # Check if the player has reached the treasure
    if player_row == treasure_row and player_col == treasure_col:
        print("Congratulations! You've found the treasure!")
        break
    
    # Check if the player has stepped on a trap
    if player_row == trap_row and player_col == trap_col:
        print("Oops! You've stepped on a trap. Game Over!")
        break
    
    # Get user input for movement
    move = input("Enter your move (W/A/S/D): ").upper()
    
    # Update player position based on user input
    if move == 'W' and maze[player_row - 1][player_col] != '#':
        player_row -= 1
    elif move == 'A' and maze[player_row][player_col - 1] != '#':
        player_col -= 1
    elif move == 'S' and maze[player_row + 1][player_col] != '#':
        player_row += 1
    elif move == 'D' and maze[player_row][player_col + 1] != '#':
        player_col += 1
    else:
        print("Invalid move! Try again.")
