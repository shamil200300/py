import pygame
import sys

FPS = 60
W = 700  # ширина экрана
H = 300  # высота экрана
WHITE = (255, 255, 255)
BLUE = (0, 70, 225)
RIGHT = "right"
LEFT = "left"
UP = "up"
DOWN = "down"
STOP = "stop"

sc = pygame.display.set_mode((W, H))
clock = pygame.time.Clock()

# координаты и радиус круга
x = W // 2
y = H // 2
r = 50

move = STOP

while 1:
    for i in pygame.event.get():
        if i.type == pygame.QUIT:
            sys.exit()
        elif i.type == pygame.KEYDOWN:
            if i.key == pygame.K_LEFT:
                move = LEFT
            elif i.key == pygame.K_RIGHT:
                move = RIGHT
        elif i.type == pygame.KEYUP:
            if i.key == pygame.K_UP:
                move = UP
            elif i.key == pygame.K_DOWN:
                move = DOWN



    sc.fill(WHITE)
    pygame.draw.circle(sc, BLUE, (x, y), r)
    pygame.display.update()

    if move == LEFT:
        x = x - 3
    elif move == RIGHT:
        x = x + 3
    elif move == UP:
        y = y - 3
    elif move == DOWN:
        y = y + 3

    clock.tick(FPS)
