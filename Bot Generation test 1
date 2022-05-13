import random
from ursina import *
def update():
    global number, max_list, entity_list
    # move cam around
    if held_keys['w']:
        camera.y += 10
    if held_keys['s']:
        camera.y -= 10
    if held_keys['d']:
        camera.x += 10
    if held_keys['a']:
        camera.x -= 10
    if held_keys['e']:
        camera.z -= 10
    if held_keys['r']:
        camera.z += 10
    # ------------------------------
    hit_info = voxel.intersects()
    if hit_info.hit:
        if hit_info.entity in entity_list:
            r, g, b = 0,0,0
            bot = Voxel(R = r, G = g,B = b)
            number += 1
            entity_list.append(bot)
    # move
    for bot in entity_list:
        move_random_pos = random.randint(1,6)
        if move_random_pos == 1:
            bot.x += 1
        elif move_random_pos == 2:
            bot.x -= 1
        elif move_random_pos == 3:
            bot.y -= 1
        elif move_random_pos == 4:
            bot.y += 1
        elif move_random_pos == 5:
            bot.z -= 1
        elif move_random_pos == 6:
            bot.z += 1

app = Ursina()
max_list = []
number = 0
class Voxel(Button):
    def __init__(self,R,G,B):
        super().__init__()
        global max_list,number
        self.parent = scene
        self.model = 'sphere'
        self.texture = 'white_cube'
        self.collider = 'sphere'
        self.scale = 5
        self.x = random.randint(-number,number)
        self.y = random.randint(-number,number)
        self.z = random.randint(-number, number)
        if number < 2:
            self.R = R
            self.G = G
            self.B = B
        else:
            self.R = random.randint(0,max_list[0][0])
            self.G = random.randint(0,max_list[0][1])
            self.B = random.randint(0,max_list[0][2])
        self.color = color.rgb(self.R,self.G,self.B)
        self.text = 'R {}  G {}  B {}'.format(self.R,self.G,self.B)
        self.text_origin = (0,0,-1)

entity_list = []
for x in range(2):
    r, g, b = random.randint(0, 255), random.randint(0, 255), random.randint(0, 255)
    max_list.append([r,g,b])
    voxel = Voxel(R = r, G = g,B = b)
    number += 1
    entity_list.append(voxel)

print(max_list[0][0],max_list[0][1],max_list[0][2])
app.run()
