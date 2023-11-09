import matplotlib.pyplot as plt
import matplotlib.animation as anime
import math
import time
import time
import moviepy.editor as mp

from PIL import Image
import glob
import webbrowser;
s1 = 180
s2 = 0
t1 = 60
ct = 1
filename = ''
x1 = 100*(math.cos(math.radians(t1))) + 200
y1 = 100*(math.sin(math.radians(t1))) + 200
x = 200*(math.cos(math.radians(t1))) + 200
y = 0 + 200
x2 = 100 * (math.cos(math.radians(s1))) + 200
y2 = 50 * (math.sin(math.radians(s1))) + 200
plt.xlim(0, 400)
plt.ylim(0, 400)
plt.plot([200, x1], [200, y1])
plt.plot([x1, x], [y1, y])
print('Simulation is being generated, please wait a few seconds.....')

while t1 < 121:
    plt.xlim(0, 400)
    plt.ylim(0, 400)
    x1 = 100 * (math.cos(math.radians(t1))) + 200
    y1 = 100 * (math.sin(math.radians(t1))) + 200
    x = 200 * (math.cos(math.radians(t1))) + 200
    y = 0 + 200
    t1 = t1+6
    filename = 'file' + str(ct) + '.png'
    ct = ct + 1
    plt.plot([200, x1], [200, y1])
    plt.plot([x1, x], [y1, y])
    plt.savefig(filename)
    plt.clf()
    ct = ct + 1
    filename = 'file' + str(ct) + '.png'
    plt.savefig(filename)


while s1 > 0:
    plt.xlim(0, 400)
    plt.ylim(0, 400)
    x1 = 100 * (math.cos(math.radians(t1))) + 200
    y1 = 100 * (math.sin(math.radians(t1))) + 200
    x2 = 100 * (math.cos(math.radians(s1))) + 200
    y2 = 50 * (math.sin(math.radians(s1))) + 200
    t1 = t1-4.5
    s1 = s1-4.5
    filename = 'file' + str(ct) + '.png'
    ct = ct + 1
    plt.plot([200, x1], [200, y1])
    plt.plot([x1, x2], [y1, y2])
    plt.savefig(filename)
    plt.clf()
    ct = ct + 1
    filename = 'file' + str(ct) + '.png'
    plt.savefig(filename)

while t1 > -121:
    plt.xlim(0, 400)
    plt.ylim(0, 400)
    x1 = 100 * (math.cos(math.radians(t1))) + 200
    y1 = 100 * (math.sin(math.radians(t1))) + 200
    x = 200 * (math.cos(math.radians(t1))) + 200
    y = 0 + 200
    t1 = t1-6
    filename = 'file' + str(ct) + '.png'
    ct = ct + 1
    plt.plot([200, x1], [200, y1])
    plt.plot([x1, x], [y1, y])
    plt.savefig(filename)
    plt.clf()
    ct = ct + 1
    filename = 'file' + str(ct) + '.png'
    plt.savefig(filename)

s1 = 180

while s1 > 0:
    plt.xlim(0, 400)
    plt.ylim(0, 400)
    x1 = 100 * (math.cos(math.radians(t1))) + 200
    y1 = 100 * (math.sin(math.radians(t1))) + 200
    x2 = 100 * (math.cos(math.radians(s1))) + 200
    y2 = 50 * (math.sin(math.radians(s1))) + 200
    t1 = t1-4.5
    s1 = s1-4.5
    filename = 'file' + str(ct) + '.png'
    ct = ct + 1
    plt.plot([200, x1], [200, y1])
    plt.plot([x1, x2], [y1, y2])
    plt.savefig(filename)
    plt.clf()
    ct = ct + 1
    filename = 'file' + str(ct) + '.png'
    plt.savefig(filename)


# Create the frames
frames = []
imgs = glob.glob("*.png")
filename = 'file'
ct = 1
for i in imgs:
    new_frame = Image.open(filename + str(ct) + '.png')
    ct = ct + 2
    frames.append(new_frame)


# Save into a GIF file that loops forever
frames[0].save('Simulation.gif', format='GIF',
               append_images=frames[1:],
               save_all=True,
               duration=5, loop=0)

clip = mp.VideoFileClip("Simulation.gif")
clip.write_videofile("Simulation.mp4")
webbrowser.open('Simulation.mp4')