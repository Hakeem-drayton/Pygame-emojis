# Pygame-emojis
Gets user input on which images to use from folder, may not work if you do not have images on pycharm, requires you download pygame library
import pygame

WHITE = (255, 255, 255)
BLACK = (0, 0, 0)


def main():
    pygame.init()
    clock = pygame.time.Clock()
    user_input = int(input("What screen proprotions do you want? "))
    screen = pygame.display.set_mode([user_input, user_input])
    pygame.display.set_caption('Emojis')
    emoji_choice = input("Which emoji do you want to use?")
    screen.fill(WHITE)
    emoji = load_picture(emoji_choice)
    draw_picture(screen,emoji)
    # TODO: Ask for the size of screen.
    # TODO: Using the template of Project 2, create the name, title and background color of the screen.

    # The font type and size is defined as:
    font = pygame.font.SysFont("comicsans", 20)
    text = font.render("Click anywhere to quit.", True, BLACK)
    screen.blit(text, (user_input//3, 25))
    # TODO: The text will appear at the top center of the screen.

    # TODO: Ask for the name of file.

    # TODO: Call the load_picture function with its input as the name of file. This function returns the Image object.
    # TODO: Call the draw_picture function with its input as screen and Image object.
    run = True
    while run:
        # The program waits for the events (mouse click, etc.):
        for event in pygame.event.get():
            # If X box on the top right of the screen is pressed, close the screen and end the program:
            if event.type == pygame.QUIT:
                run = False
            # If we click on anywhere on the screen, it will get closed by this command:
            elif event.type == pygame.MOUSEBUTTONDOWN:
                run = False

        pygame.display.flip()
        clock.tick(60)

    pygame.quit()


# Function for file browse
def load_picture(emoji_file):
    emojis = pygame.image.load(emoji_file)
    return emojis
   # emoji_file = pygame.image.load('Downloads/Images3/smiley.png'), (150, 150)






def draw_picture(screen, image_object):
    x,y = screen.get_size()
    screen.blit(image_object, (x/2, y/4))
    screen.blit(image_object, (x/4, y/2))
    screen.blit(image_object, (x/2, 3*y/4))
    screen.blit(image_object, (3*x/4, y/2))


if __name__ == '__main__':
    main()
