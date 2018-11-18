import pygame
import time

def main():
        pygame.init()
        
        print('Wczytywanie loga i napisow...')
        time.sleep(0.5)
        myfont = pygame.font.SysFont("monospace", 20)
        logo=pygame.image.load('D:\\AI_Projekt_Assets\Sprites_2D\\PizzaSlice.png')
        pygame.display.set_icon(logo)
        pygame.display.set_caption('PIZZA GUY')
        
        print('Wczytywanie i skalowanie tekstur...')
        time.sleep(0.5)
        image_house=pygame.image.load('D:\\AI_Projekt_Assets\Sprites_2D\\House.png')
        image_house_big=pygame.transform.scale(image_house,(80,80))
        
        screen = pygame.display.set_mode((400,400))
        
        print('Tworzenie PizzaGuya...')
        time.sleep(0.5)
        image_one=pygame.image.load('D:\\AI_Projekt_Assets\Sprites_2D\\PizzaGuy.png')
        rot_image_left=pygame.transform.rotate(image_one,90)
        rot_image_right=pygame.transform.rotate(image_one,-90)

        road_image=pygame.image.load('D:\\AI_Projekt_Assets\Sprites_2D\\Road.png')
        
        x=400
        y=240
        
        

        screen.fill((0,204,102))
        print('Tworzenie i numerowanie domow...')
        time.sleep(0.5)
        house_number=0
        for i in range(40,400,120):
                for a in range(40,400,120):
                                house_number+=1
                                label = myfont.render((""+str(house_number)), 1, (0,0,0))
                                screen.blit(image_house_big,(i,a))
                                screen.blit(label, (a, i))
        print('Tworzenie drog...')
        time.sleep(0.5)
        for w in range(240,360,40):
                        screen.blit(road_image,(240,w))
        for w in range(120,240,40):
                        screen.blit(road_image,(120,w))
        for w in range(120,400,40):
                        screen.blit(road_image,(0,w))
        for w in range(120,400,40):
                        screen.blit(road_image,(360,w))
        for w in range(0,400,40):
                        screen.blit(road_image,(w,120))
        for w in range(0,400,40):
                        screen.blit(road_image,(w,240))
        for w in range(0,400,40):
                        screen.blit(road_image,(w,360))
        print('Odpalenie programu...')
        time.sleep(0.5)
        running=True
        turn_right=True

        while running:
                pygame.time.delay(40)
                for event in pygame.event.get():
                        if event.type == pygame.QUIT:
                                running = False
              
                if turn_right:  
                        if(x>0):
                                screen.blit(road_image,(x,y))
                                screen.blit(rot_image_left, (x,y))
                                x-=10
                                pygame.display.update()
                                screen.blit(road_image,(x+40,y))
                        else:
                                if(y>120):
                                        screen.blit(road_image,(x,y))            
                                        screen.blit(image_one, (x,y)) 
                                        y-=10
                                        pygame.display.update()
                                        screen.blit(road_image,(x,y+40))
                                #pygame.display.update()
                                else:
                                        turn_right=False
                else:
                        if(x<200):
                                
                                screen.blit(road_image,(x,y))
                                screen.blit(rot_image_right, (x,y))
                                x+=10
                                pygame.display.update()
                                screen.blit(road_image,(x-40,y))
               

main()