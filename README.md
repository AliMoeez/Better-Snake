# Better-Snake

import pygame
import random
import math
import sys

pygame.init()

FPS=30

GREEN=(0,128,0)
RED=(255,0,0)
ORANGE=(255,215,0)
WHITE=(255,255,255)

SCREEN_WIDTH=900
SCREEN_HEIGHT=700

X=100
Y=100

DX=0
DY=0

GX=random.randint(100,800)
GY=random.randint(100,600)

Player_Width=40
Player_Height=40

growth_Width=20
growth_Height=20

SCREEN=pygame.display.set_mode((SCREEN_WIDTH,SCREEN_HEIGHT))

clock=pygame.time.Clock()

while True:
    clock.tick(FPS)
    SCREEN.fill((0,0,0))
    
    player=pygame.draw.rect(SCREEN,GREEN,pygame.Rect(X,Y,Player_Width,Player_Height))
    
    growth=pygame.draw.rect(SCREEN,ORANGE,pygame.Rect(GX,GY,growth_Width,growth_Height))
    
    for event in pygame.event.get():
        if event.type==pygame.QUIT:
            pygame.quit()
            sys.exit()
            
    key=pygame.key.get_pressed()
    
    if key[pygame.K_UP]:
        DY-=3
        DX=0
        
    if key[pygame.K_DOWN]:
        DY+=3
        DX=0
    
    if key[pygame.K_LEFT]:
        DX-=3
        DY=0
        
    if key[pygame.K_RIGHT]:
        DX+=3 
        DY=0
    
    Y+=DY
    X+=DX
    
    distance=math.sqrt(math.pow(X-GX,2))+math.sqrt(math.pow(Y-GY,2))
    print(distance)
    
    if distance<=40:
        GX=random.randint(100,800)
        GY=random.randint(100,600)
    
    if Y>=660:
        Y=650
    
    if Y<=0:
        Y=10
    
    if X<=0:
        X=10
        
    if X>=860:
        X=850
            
    
            
            
    pygame.display.update()
