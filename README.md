# SNAKE GAME
I have developed a classic arcade game using pygame and python where the player controls a snake that moves around the screen, consuming food to grow longer while avoiding collisions with the walls. The game features smooth movements, increasing difficulty as the snake grows, and a scoring system is set-up. 

##TABLES OF CONTENT
1. Technologies Used
  - Programming language--> Python
  - Libraries and framework--> Pygame
2. Concepts Used
  - Continuous - loop(movements)
  - Entering user inputs
  - Collisions detection
  - Placing food at random positions
  - Scoring system
3. Features
  - Player controls the snake movements using arrow keys  ↑ ↓ → ←
  - When the snake eats food,it increases in length
  - The game ends if snake collides with the walls or itself
  - A message appears when the game is over, allowing user to restart.



 ###INSTALLATION
 1. Install Python --> python.org
 2. Install Pygame --> pip install pygame
 3. Create the snake game code


     import pygame
     import random

   pygame.init()

width, height = 600, 600
game_screen = pygame.display.set_mode((width, height))
pygame.display.set_caption("GV Snake game 3")

snake_x, snake_y = width/2, height/2
change_x, change_y =0,0

food_x, food_y = random.randrange(0, width)//10*10, random.randrange(0, height)//10*10

clock = pygame.time.clock()

snake_body = [(snake_x, snake_y)]

def display_snake_and_food():
    global snake_x, snake_y, food_x, food_y
    snake_x = (snake_x + snake_x)%width
    snake_y = (snake_y + snake_y)%height

    if((snake_x, snake_y)in snake_body[1:1]):
        print("GAME OVER!!!")
        quit()

        snake_body.append((snake_x, snake_y))

        if(food_x == snake_x and food_y == snake_y):
            food_x, food_y = random.randrange(0, width)//10*10, random.randrange(0, height)//10*10
            else:
                del snake_body[0]

                game_screen.fill(0,0,0)
                pygame.draw.rect(game_screen,(0,255,0), [food_x, food_y, 10, 10])
                for (x,y) in snake_body:
                    pygame.draw.rect(game_screen,(255,255,255), [x, y, 10, 10])
                    pygame.display.update()

                    while True:
                        events = pygame.event.get()
                        for event in events:
                            if(event.type == pygame.QUIT):
                                pygame.QUIT
                                quit()
                                if(event.key == pygame.KEYDOWN):
                                    if(event.key == pygame.K_LEFT):
                                        change_x = -10
                                        change_y = 0
                                    elif(event.key == pygame.K_RIGHT):
                                        change_x = 10
                                        change_y = 0
                                    elif(event.key == pygame.K_UP):
                                        change_x = 0
                                        change_y = -10
                                    elif(event.key == pygame.K_DOWN):
                                        change_x = 0
                                        change_y = 10
                            display_snake_and_food()
                            clock.tick(5)



4. Run the code --> python snake_game.py

   This will launch the snake game.By using arrow keys the snake movements can be controlled.
   The "GAME OVER!!!" is displayed when the snake hits the walls or itself.  
 
