from random import randint 
from pygame import *
main_win = display.set_mode((700,500))
display.set_caption('ping pong')
back = transform.scale(image.load('hhh.jpg'),(700,500))


clock = time.Clock()
FPS = 60
font.init()
font2 = font.SysFont('Arial',36)
class GameSprite(sprite.Sprite):
    def __init__(self, player_image, player_x, player_y, player_speed,height,width):
        super().__init__()
        self.image = transform.scale(image.load(player_image), (height, width))
        self.speed = player_speed
        self.rect = self.image.get_rect()
        self.rect.x = player_x
        self.rect.y = player_y
    def reset(self):
        main_win.blit(self.image, (self.rect.x, self.rect.y))


#sprite1 = player("rocket.png", 50, 400, 5,80,80)       
class player(GameSprite):
    def update(self):
        keys_pressed = key.get_pressed()
        if keys_pressed[K_a] and self.rect.y > 0:
            self.rect.y -= 10
        if keys_pressed[K_d] and self.rect.y < 425:
            self.rect.y += 10
    def update2(self):
        keys_pressed = key.get_pressed()
        if keys_pressed[K_j] and self.rect.y > 0:
            self.rect.y -= 10
        if keys_pressed[K_l] and self.rect.y < 425:
            self.rect.y += 10
class ball(GameSprite):
    def update(self):
        if sprite.spritecollide(sprite1,ball,True):


sprite1 = player("35vge6b4fwc3zswnsf3e7azdwohequhf.jpg", 30, 50, 5,80,80)
sprite2 = player("35vge6b4fwc3zswnsf3e7azdwohequhf.jpg", 570, 50, 5,80,80)
game = True
speed_x = 3 
speed_y = 3 
while game:
    main_win.blit(back,(0,0))
    for e in event.get():
        if e.type == QUIT:
           game = False 
    sprite1.update()    
    sprite1.reset()
    sprite2.update2()    
    sprite2.reset()
    display.update()
    clock.tick(FPS)
