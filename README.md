# TIC-TAC-TOE-py.processing
It's a tic-tac-toe game using processing with python mode

#var declaration
start = False
nClicks =0
checked=[None for i in range(9)]
odd = True    #donne la main pour jouer
image=[None for i in range(9)]
win = False
againstPC = True   


#set up window
def setup():
    size(500,700)
    keyPressed()

#darw
def draw():
    global win
    global odd
    global nClicks
    if not start:
        reset()
    else:
        background(112,128,144)
        strokeWeight(1)
        stroke(100)
        fill(239, 239, 239)
        rect(10, 30, width - 20, height - 40, 100)
        fill(112,128,144)
        textSize(20)
        stroke(112,128,144)
        strokeWeight(10)
        line(175, 150, 175, 650)
        line(325, 150, 325, 650)
        line(20, 325, 480, 325)
        line(20, 475, 480, 475)
        for i in range (9):
            if checked[i] :
                if (i==0):
                    if (image[0] == 'X'):
                        cross(0)
                    else:
                        circle(0)
                        
                if (i==1):
                    if (image[1] == 'X'):
                        cross(1)
                    else:
                        circle(1)
                         
                if (i==2):
                    if (image[2] == 'X'):
                        cross(2)
                    else:
                        circle(2)
                        
                if (i==3):
                    if (image[3] == 'X'):
                        cross(3)
                    else:
                        circle(3)
                        
                if (i==4):
                    if (image[4] == 'X'):
                        cross(4)
                    else:
                        circle(4)
                        
                if (i==5):
                    if (image[5] == 'X'):
                        cross(5)
                    else:
                        circle(5)
                        
                if (i==6):
                    if (image[6] == 'X'):
                        cross(6)
                    else:
                        circle(6)
                        
                if (i==7):
                    if (image[7] == 'X'):
                        cross(7)
                    else:
                        circle(7)
                        
                if (i==8):
                    if (image[8] == 'X'):
                        cross(8)
                    else:
                        circle(8)
                        
        if nClicks == 9 or win:
            stroke(255)
            strokeWeight(1)
            text("Game Ended !!  Press UP to continue", 75, 100)
    
            
        winCheck()
        if againstPC and not win and not  odd:
            computePlay()
        if not againstPC:
            comment()

def comment():
    if odd:
        stroke(255)
        strokeWeight(1)
        text("joueur 1", 75, 100)
    else:
        stroke(255)
        strokeWeight(1)
        text("joueur 2", 75, 100)  
#keyPressed
def keyPressed() :
    global start
    global againstPC
    if keyCode == UP:
        start = not start

    if not start:
        if keyCode == LEFT:
            againstPC = True    
            start = True    

        if keyCode == RIGHT:
            againstPC = False
            start = True    
        
#reset
def reset() :
    global win
    global odd
    global nClicks
    background(112,128,144)
    strokeWeight(1)
    stroke(100)
    fill(239, 239, 239)
    rect(10, 30, width - 20, height - 40, 100)
    fill(112,128,144)
    textSize(20)
    text("To play with", 70, 380)
    text("Computer", 80, 400)
    text("(PRESS LEFT)", 70, 420)
    text("To  play  with", 315, 380)
    text("Other Player", 320, 400)
    text("(PRESS RIGHT)", 310, 420)
    textSize(70)
    fill(0, 102, 153)
    text("Tic Tac Toe", 50, 160)
    fill(0, 102, 153, 51)
    text("Tic Tac Toe", 50, 190)
    
    for i in range (9):
        checked[i]=False
        image[i] =  ' '
    if win :
        win = False
        
    odd = True    
    nClicks = 0

#computerPlay want to be unbeatable
def computePlay():
    global odd
    global nClicks
    if image[0] == 'X' :
        if image[1] == 'X' and not checked[2]:
            cross(2)
            nClicks=nClicks+1
            checked[2] = True    
            image[2] = 'X'
            odd = not odd
            return

        if image[2] == 'X' and  not checked[1]:
            cross(1)
            nClicks=nClicks+1
            checked[1] = True    
            image[1] = 'X'
            odd = not odd
            return
    
        if image[4] == 'X' and not  checked[8]:
            cross(8)
            nClicks=nClicks+1
            checked[8] = True    
            image[8] = 'X'
            odd= not odd
            return
    
        if image[8] == 'X' and not  checked[4]:
            cross(4)
            nClicks=nClicks+1
            checked[4] = True    
            image[4] = 'X'
            odd= not odd
            return

        if image[3] == 'X' and not  checked[6]:
            cross(6)
            nClicks=nClicks+1
            checked[6] = True    
            image[6] = 'X'
            odd= not odd
            return

        if image[6] == 'X' and not checked[3]:
            cross(3)
            nClicks=nClicks+1
            checked[3] = True    
            image[3] = 'X'
            odd= not odd
            return
  
    if image[1] == 'X' :
        if image[2] == 'X' and not checked[0]:
            cross(0)
            nClicks=nClicks+1
            checked[0] = True    
            image[0] = 'X'
            odd= not odd
            return
    
        if image[4] == 'X' and not checked[7]:
            cross(7)
            nClicks=nClicks+1
            checked[7] = True    
            image[7] = 'X'
            odd= not odd
            return
   
        if image[7] == 'X' and not checked[4]:
            cross(4)
            nClicks=nClicks+1
            checked[4] = True    
            image[4] = 'X'
            odd= not odd
            return
  
  
    if(image[2] == 'X'):
        if image[4] == 'X' and not checked[6]:
            cross(6)
            nClicks=nClicks+1
            checked[6] = True    
            image[6] = 'X'
            odd= not odd
            return
        
        if image[6] == 'X' and not checked[4]:
            cross(4)
            nClicks=nClicks+1
            checked[4] = True    
            image[4] = 'X'
            odd= not odd
            return
   
        if image[5] == 'X' and not checked[8]:
            cross(8)
            nClicks=nClicks+1
            checked[8] = True    
            image[8] = 'X'
            odd= not odd
            return
   
        if image[8] == 'X' and not checked[5]:
            cross(5)
            nClicks=nClicks+1
            checked[5] = True    
            image[5] = 'X'
            odd= not odd
            return
   
    if image[3] == 'X':
        if image[4] == 'X' and not checked[5]:
            cross(5)
            nClicks=nClicks+1
            checked[5] = True    
            image[5] = 'X'
            odd= not odd
            return
   
        if image[5] == 'X' and not checked[4]:
            cross(4)
            nClicks=nClicks+1
            checked[4] = True    
            image[4] = 'X'
            odd= not odd
            return
    
        if image[6] == 'X' and not checked[0]:
            cross(0)
            nClicks=nClicks+1
            checked[0] = True    
            image[0] = 'X'
            odd= not odd
            return
  
    if image[4] == 'X':
        if image[5] == 'X' and not checked[3]:
            cross(3)
            nClicks=nClicks+1
            checked[3] = True    
            image[3] = 'X'
            odd= not odd
            return
   
        if image[6] == 'X' and not checked[2]:
            cross(2)
            nClicks=nClicks+1
            checked[2] = True    
            image[2] = 'X'
            odd= not odd
            return
    
        if image[7] == 'X' and not checked[1]:
            cross(1)
            nClicks=nClicks+1
            checked[1] = True    
            image[1] = 'X'
            odd= not odd
            return
    
        if image[8] == 'X' and not checked[0]:
            cross(0)
            nClicks=nClicks+1
            checked[0] = True    
            image[0] = 'X'
            odd= not odd
            return
  
  
    if image[5] == 'X' :
        if image[8] == 'X' and not checked[2]:
            cross(2)
            nClicks=nClicks+1
            checked[2] = True    
            image[2] = 'X'
            odd= not odd
            return
  
    if image[6] == 'X':
        if image[7] == 'X' and not checked[8]:
            cross(8)
            nClicks=nClicks+1
            checked[8] = True    
            image[8] = 'X'
            odd= not odd
            return
    
        if image[8] == 'X' and not checked[7]:
            cross(7)
            nClicks=nClicks+1
            checked[7] = True    
            image[7] = 'X'
            odd= not odd
            return
  
    if image[7] == 'X' :
        if image[8] == 'X' and not checked[6]:
            cross(6)
            nClicks=nClicks+1
            checked[6] = True    
            image[6] = 'X'
            odd= not odd
            return

    if image[0] == 'O':
        if image[1] == 'O' and not checked[2]:
            cross(2)
            nClicks=nClicks+1
            checked[2] = True    
            image[2] = 'X'
            odd= not odd
            return
    
        if image[2] == 'O' and not checked[1]:
            cross(1)
            nClicks=nClicks+1
            checked[1] = True    
            image[1] = 'X'
            odd= not odd
            return
    
        if image[4] == 'O' and not checked[8]:
            cross(8)
            nClicks=nClicks+1
            checked[8] = True    
            image[8] = 'X'
            odd= not odd
            return
    
        if image[8] == 'O' and not checked[4]:
            cross(4)
            nClicks=nClicks+1
            checked[4] = True    
            image[4] = 'X'
            odd= not odd
            return
        
        if image[3] == 'O' and not checked[6]:
            cross(6)
            nClicks=nClicks+1
            checked[6] = True    
            image[6] = 'X'
            odd= not odd
            return
    
        if image[6] == 'O' and not checked[3]:
            cross(3)
            nClicks=nClicks+1
            checked[3] = True    
            image[3] = 'X'
            odd= not odd
            return

    if image[1] == 'O':
        if image[2] == 'O' and not checked[0]:
            cross(0)
            nClicks=nClicks+1
            checked[0] = True    
            image[0] = 'X'
            odd= not odd
            return
    
        if image[4] == 'O' and not checked[7]:
            cross(7)
            nClicks=nClicks+1
            checked[7] = True    
            image[7] = 'X'
            odd= not odd
            return
    
        if image[7] == 'O' and not checked[4]:
            cross(4)
            nClicks=nClicks+1
            checked[4] = True    
            image[4] = 'X'
            odd= not odd
            return

    if image[2] == 'O':
        if image[4] == 'O' and not checked[6]:
            cross(6)
            nClicks=nClicks+1
            checked[6] = True    
            image[6] = 'X'
            odd= not odd
            return
    
        if image[6] == 'O' and not checked[4]:
            cross(4)
            nClicks=nClicks+1
            checked[4] = True    
            image[4] = 'X'
            odd= not odd
            return
    
        if image[5] == 'O' and not checked[8]:
            cross(8)
            nClicks=nClicks+1
            checked[8] = True    
            image[8] = 'X'
            odd= not odd
            return
    
        if image[8] == 'O' and not checked[5]:
            cross(5)
            nClicks=nClicks+1
            checked[5] = True    
            image[5] = 'X'
            odd= not odd
            return

    if image[3] == 'O':
        if image[4] == 'O' and not checked[5]:
            cross(5)
            nClicks=nClicks+1
            checked[5] = True    
            image[5] = 'X'
            odd= not odd
            return
    
        if image[5] == 'O' and not checked[4]:
            cross(4)
            nClicks=nClicks+1
            checked[4] = True    
            image[4] = 'X'
            odd= not odd
            return
    
        if image[6] == 'O' and not checked[0]:
            cross(0)
            nClicks=nClicks+1
            checked[0] = True    
            image[0] = 'X'
            odd= not odd
            return
  

    if image[4] == 'O':
        if image[5] == 'O' and not checked[3]:
            cross(3)
            nClicks=nClicks+1
            checked[3] = True    
            image[3] = 'X'
            odd= not odd
            return

        if image[6] == 'O' and not checked[2]:
            cross(2)
            nClicks=nClicks+1
            checked[2] = True    
            image[2] = 'X'
            odd= not odd
            return

        if image[7] == 'O' and not checked[1]:
            cross(1)
            nClicks=nClicks+1
            checked[1] = True    
            image[1] = 'X'
            odd= not odd
            return
    
        if image[8] == 'O' and not checked[0]:
            cross(0)
            nClicks=nClicks+1
            checked[0] = True    
            image[0] = 'X'
            odd= not odd
            return


    if image[5] == 'O':
        if image[8] == 'O' and not checked[2]:
            cross(2)
            nClicks=nClicks+1
            checked[2] = True    
            image[2] = 'X'
            odd= not odd
            return

    if image[6] == 'O':
        if image[7] == 'O' and not checked[8]:
            cross(8)
            nClicks=nClicks+1
            checked[8] = True    
            image[8] = 'X'
            odd= not odd
            return
    
        if image[8] == 'O' and not checked[7]:
            cross(7)
            nClicks=nClicks+1
            checked[7] = True    
            image[7] = 'X'
            odd= not odd
            return
  

    if image[7] == 'O':
        if image[8] == 'O' and not checked[6]:
            cross(6)
            nClicks=nClicks+1
            checked[6] = True    
            image[6] = 'X'
            odd= not odd
            return
  
    if image[0] == 'X':
        if not checked[1] and not checked[2]:
            cross(2)
            nClicks=nClicks+1
            checked[2] = True    
            image[2] = 'X'
            odd= not odd
            return
    
        if not checked[3] and not checked[6]:
            cross(6)
            nClicks=nClicks+1
            checked[6] = True    
            image[6] = 'X'
            odd= not odd
            return
    
        if not checked[4] and not checked[8]:
            cross(8)
            nClicks=nClicks+1
            checked[8] = True    
            image[8] = 'X'
            odd= not odd
            return
  
    if image[2] == 'X':
        if not checked[0] and not checked[1]:
            cross(0)
            nClicks=nClicks+1
            checked[0] = True    
            image[0] = 'X'
            odd= not odd
            return
    
        if not checked[4] and not checked[6] :
            cross(6)
            nClicks=nClicks+1
            checked[6] = True    
            image[6] = 'X'
            odd= not odd
            return
    
        if not checked[5] and not checked[8] :
            cross(8)
            nClicks=nClicks+1
            checked[8] = True    
            image[8] = 'X'
            odd= not odd
            return
    
  
    if image[6] == 'X' :
        if not checked[0] and not checked[3] :
            cross(0)
            nClicks=nClicks+1
            checked[0] = True    
            image[0] = 'X'
            odd= not odd
            return
    
        if not checked[2] and not checked[4] :
            cross(2)
            nClicks=nClicks+1
            checked[2] = True    
            image[2] = 'X'
            odd= not odd
            return
    
        if not checked[7] and not checked[8] :
            cross(8)
            nClicks=nClicks+1
            checked[8] = True    
            image[8] = 'X'
            odd= not odd
            return
    
    
    if image[8] == 'X' :
        if not checked[0] and not checked[4] :
            cross(0)
            nClicks=nClicks+1
            checked[0] = True    
            image[0] = 'X'
            odd= not odd
            return
    
        if not checked[2] and not checked[5] :
            cross(2)
            nClicks=nClicks+1
            checked[2] = True    
            image[2] = 'X'
            odd= not odd
            return
    
        if not checked[6] and not checked[7] :
            cross(6)
            nClicks=nClicks+1
            checked[6] = True    
            image[6] = 'X'
            odd= not odd
            return
  
        if  not checked[4] :
            cross(4)
            nClicks=nClicks+1
            checked[4] = True    
            image[4] = 'X'
            odd= not odd
            return
  
    if image[0] == 'O' :
        if not checked[5] and not checked[6]  and image[7] == 'O' :
            cross(8)
            nClicks=nClicks+1
            checked[8] = True    
            image[8] = 'X'
            odd= not odd
            return
    
  
    if image[2] == 'O' :
        if not checked[5] and not checked[8]  and image[7] == 'O' :
            cross(8)
            nClicks=nClicks+1
            checked[8] = True    
            image[8] = 'X'
            odd= not odd
            return
    
        if not checked[0] and not checked[1]  and image[3] == 'O' :
            cross(0)
            nClicks=nClicks+1
            checked[0] = True    
            image[0] = 'X'
            odd= not odd
            return
    
        if not checked[0] and not checked[1] :
            cross(1)
            nClicks=nClicks+1
            checked[1] = True    
            image[1] = 'X'
            odd= not odd
            return
    
        if not checked[5] and not checked[8] :
            cross(5)
            nClicks=nClicks+1
            checked[5] = True    
            image[5] = 'X'
            odd= not odd
            return
    
        if not checked[4] and not checked[6] :
            cross(4)
            nClicks=nClicks+1
            checked[4] = True    
            image[4] = 'X'
            odd= not odd
            return

    for i in range(8):
        if  not checked[i] :
            cross(i)
            nClicks=nClicks+1
            checked[i] = True    
            image[i] = 'X'
            odd= not odd
            return 

#winCheck
def winCheck():
    global win
    if image[0] == 'X'  and image[1] == 'X'  and image[2] == 'X':
        win = True    
    if image[0] == 'X'  and image[4] == 'X'  and image[8] == 'X' :
        win = True    
    if image[0] == 'X'  and image[3] == 'X'  and image[6] == 'X' :
        win = True    
    if image[1] == 'X'  and image[4] == 'X'  and image[7] == 'X' :
        win = True    
    if image[2] == 'X'  and image[4] == 'X'  and image[6] == 'X' :
        win = True    
    if image[2] == 'X'  and image[5] == 'X'  and image[8] == 'X' :
        win = True    
    if image[3] == 'X'  and image[4] == 'X'  and image[5] == 'X' :
        win = True    
    if image[6] == 'X'  and image[7] == 'X'  and image[8] == 'X' :
        win = True    

    if image[0] == 'O'  and image[1] == 'O'  and image[2] == 'O' :
        win = True    
    if image[0] == 'O'  and image[4] == 'O'  and image[8] == 'O' :
        win = True        
    if image[0] == 'O'  and image[3] == 'O'  and image[6] == 'O' :
        win = True    
    if image[1] == 'O'  and image[4] == 'O'  and image[7] == 'O' :
        win = True    
    if image[2] == 'O'  and image[4] == 'O'  and image[6] == 'O' :
        win = True    
    if image[2] == 'O'  and image[5] == 'O'  and image[8] == 'O' :
        win = True    
    if image[3] == 'O'  and image[4] == 'O'  and image[5] == 'O' :
        win = True    
    if image[6] == 'O'  and image[7] == 'O'  and image[8] == 'O':
        win = True    

#void circle
def circle(box):
    x1 = 0
    x2 = 0
    y1 = 0
    y2 = 0
    if box == 0:
        x1 = 20 
        y1 = 150 
        x2 = 175 
        y2 = 325
    
    if box == 1:
        x1 = 175 
        y1 = 150 
        x2 = 325 
        y2 = 325
        
    if box == 2:
        x1 = 325
        y1 = 150 
        x2 = 475 
        y2 = 325
        
    if box == 3:
        x1 = 20 
        y1 = 315
        x2 = 175
        y2 = 485
        
    if box == 4:
        x1 = 175 
        y1 = 315 
        x2 = 325 
        y2 = 485
        
    if box ==5:
        x1 = 325 
        y1 = 315 
        x2 = 475 
        y2 = 485
        
    if box == 6:
        x1 = 20 
        y1 = 475 
        x2 = 175
        y2 = 650
        
    if box == 7:
        x1 = 175 
        y1 = 475 
        x2 = 325 
        y2 = 650
        
    if box == 8:
        x1 = 325 
        y1 = 475 
        x2 = 475 
        y2 = 650
        
    
    strokeWeight(10)
    stroke(255, 0, 0)
    noFill()
    ellipse(x1 + (x2 - x1) / 2, y1 + (y2 - y1) / 2, 75, 75)

#cross
def cross(box) :
    x1 = 0
    x2 = 0
    y1 = 0
    y2 = 0
    if box == 0:
        x1 = 20 
        y1 = 150 
        x2 = 175 
        y2 = 325
        
    if box == 1:
        x1 = 175 
        y1 = 150 
        x2 = 325 
        y2 = 325
        
    if box == 2:
        x1 = 325 
        y1 = 150 
        x2 = 475 
        y2 = 325
        
    if box == 3:
        x1 = 20 
        y1 = 315 
        x2 = 175 
        y2 = 485
        
    if box == 4:
        x1 = 175 
        y1 = 315 
        x2 = 325 
        y2 = 485
        
    if box == 5:
        x1 = 325 
        y1 = 315 
        x2 = 475 
        y2 = 485
        
    if box == 6: 
        x1 = 20
        y1 = 475 
        x2 = 175 
        y2 = 650
        
    if box == 7:
        x1 = 175 
        y1 = 475 
        x2 = 325 
        y2 = 650
        
    if box == 8:
        x1 = 325 
        y1 = 475 
        x2 = 475 
        y2 = 650
        
    
    strokeWeight(10)
    stroke(0, 0, 255)
    line(x1 + 50, y1 + 50, x2 - 50, y2 - 50)
    line(x2 - 50, y1 + 50, x1 + 50, y2 - 50)

#mouceClicked
def mouseClicked():
    global nClicks
    global odd
    global againstPC
    if againstPC:
        if start and not win  :
            if mouseX > 20 and mouseX < 175 :
                if mouseY > 150 and mouseY < 325 :
                    if not checked[0]:
                        checked[0] = True 
                        if odd :
                            image[0] = 'O'
                        else :
                            image[0] = 'X'
                        odd = not odd;
                        nClicks = nClicks +1
         
                if mouseY > 325 and  mouseY < 475:
                    if not checked[3] :
                        checked[3] = True
                        if odd :
                            image[3] = 'O'
                        else :
                            image[3] = 'X'
                        odd = not odd;
                        nClicks = nClicks + 1 
        
                if mouseY > 475 and  mouseY < 650 :
                    if not checked[6] :
                        checked[6] = True   
                        if odd:
                            image[6] = 'O'
                        else :
                            image[6] = 'X'
                        odd = not odd;
                        nClicks = nClicks + 1 
        
            if mouseX > 175 and  mouseX < 325 :
                if mouseY > 150 and  mouseY < 325 :
                    if not checked[1]:
                        checked[1] = True    
                        if odd:
                            image[1] = 'O'
                        else :
                            image[1] = 'X'
                        odd = not odd
                        nClicks = nClicks + 1 
         
                if mouseY > 325 and  mouseY < 475: 
                    if not checked[4] :
                        checked[4] = True   
                        if odd :
                            image[4] = 'O'
                        else :
                            image[4] = 'X'
                        odd = not odd
                        nClicks = nClicks + 1 
        
                if mouseY > 475 and  mouseY < 650 :
                    if not checked[7] :
                        checked[7] = True    
                        if odd:
                            image[7] = 'O'
                        else:
                            image[7] = 'X'
                        odd = not odd
                        nClicks = nClicks + 1 
        
            if mouseX > 325 and  mouseX < 475:
                if mouseY > 150 and  mouseY < 325:
                    if not checked[2] :
                        checked[2] = True    
                        if odd :
                            image[2] = 'O'
                        else:
                            image[2] = 'X'
                        odd = not odd
                        nClicks = nClicks + 1 
         
                if mouseY > 325 and  mouseY < 475:
                    if not checked[5] :
                        checked[5] = True    
                        if odd :
                            image[5] = 'O'
                        else:
                            image[5] = 'X'
                        odd = not odd
                        nClicks = nClicks + 1
          
                if mouseY > 475 and  mouseY < 650 :
                    if not checked[8] :
                        checked[8] = True    
                        if odd :
                            image[8] = 'O'
                        else:
                            image[8] = 'X'
                        odd = not odd
                        nClicks = nClicks + 1 
         
        
    
    if not againstPC:
        if start and not win:
            if mouseX > 20 and mouseX < 175 :
                if mouseY > 150 and mouseY < 325 :
                    if not checked[0]:
                        checked[0] = True 
                        if odd :
                            image[0] = 'O'
                        else :
                            image[0] = 'X'
                        odd = not odd;
                        nClicks = nClicks +1
         
                if mouseY > 325 and  mouseY < 475:
                    if not checked[3] :
                        checked[3] = True
                        if odd :
                            image[3] = 'O'
                        else :
                            image[3] = 'X'
                        odd = not odd;
                        nClicks = nClicks + 1 
        
                if mouseY > 475 and  mouseY < 650 :
                    if not checked[6] :
                        checked[6] = True   
                        if odd:
                            image[6] = 'O'
                        else :
                            image[6] = 'X'
                        odd = not odd;
                        nClicks = nClicks + 1 
        
            if mouseX > 175 and  mouseX < 325 :
                if mouseY > 150 and  mouseY < 325 :
                    if not checked[1]:
                        checked[1] = True    
                        if odd:
                            image[1] = 'O'
                        else :
                            image[1] = 'X'
                        odd = not odd
                        nClicks = nClicks + 1 
         
                if mouseY > 325 and  mouseY < 475: 
                    if not checked[4] :
                        checked[4] = True   
                        if odd :
                            image[4] = 'O'
                        else :
                            image[4] = 'X'
                        odd = not odd
                        nClicks = nClicks + 1 
        
                if mouseY > 475 and  mouseY < 650 :
                    if not checked[7] :
                        checked[7] = True    
                        if odd:
                            image[7] = 'O'
                        else:
                            image[7] = 'X'
                        odd = not odd
                        nClicks = nClicks + 1 
        
            if mouseX > 325 and  mouseX < 475:
                if mouseY > 150 and  mouseY < 325:
                    if not checked[2] :
                        checked[2] = True    
                        if odd :
                            image[2] = 'O'
                        else:
                            image[2] = 'X'
                        odd = not odd
                        nClicks = nClicks + 1 
         
                if mouseY > 325 and  mouseY < 475:
                    if not checked[5] :
                        checked[5] = True    
                        if odd :
                            image[5] = 'O'
                        else:
                            image[5] = 'X'
                        odd = not odd
                        nClicks = nClicks + 1
          
                if mouseY > 475 and  mouseY < 650 :
                    if not checked[8] :
                        checked[8] = True    
                        if odd :
                            image[8] = 'O'
                        else:
                            image[8] = 'X'
                        odd = not odd
                        nClicks = nClicks + 1 
         
    
