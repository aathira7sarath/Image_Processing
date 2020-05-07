# Image_Processing
# Image-Processing
import cv2
import numpy as np
#import os
i1 = cv2.imread('/Users/HP/Desktop/bird.jpg')
i2 = cv2.imread('/Users/HP/Desktop/cat.jpg')
i3 = cv2.imread('/Users/HP/Desktop/flowers.jpg')
i4 = cv2.imread('/Users/HP/Desktop/horse.jpg')
# <class 'numpy.ndarray'>
def partA():
    # height, width, number of channels in image
    h1 = i1.shape[0]
    w1= i1.shape[1]
    c1 = i1.shape[2]
    b1,g1,r1 =(i1[213, 320])
    h2 = i2.shape[0]
    w2= i2.shape[1]
    c2 = i2.shape[2]
    b2,g2,r2 =(i2[195, 320])
    h3 = i3.shape[0]
    w3= i3.shape[1]
    c3 = i3.shape[2]
    b3,g3,r3 = (i3[142, 320])
    h4 = i4.shape[0]
    w4= i4.shape[1]
    c4 = i4.shape[2]
    b4,g4,r4 = (i3[202, 320])
    print('Name           Height Width  No.ofChannels  Intensity(BGR)')
    print("bird.jpg      ",h1,"  ",w1,"  ",c1,"            ",b1,g1,r1)
    print("cat.jpg       ",h2,"  ",w2,"  ",c2,"            ",b2,g2,r2)
    print("flowers.jpg   ",h3,"  ",w3,"  ",c3,"            ",b3,g3,r3)
    print("horse.jpg     ",h4,"  ",w4,"  ",c4,"            ",b4,g4,r4)
    pass

def partB():
    # RGB Red
    cv2.imwrite('cat_red.jpg',i2[:, :, 2])
    pass

def partC():
    b_channel, g_channel, r_channel = cv2.split(i3)
    alpha_channel = np.ones(b_channel.shape, dtype=b_channel.dtype) * 50 
    i3_= cv2.merge((b_channel, g_channel, r_channel, alpha_channel))
    i3_[:,:,3]=127
    cv2.imwrite('flowers_.png',i3_)
    pass

def partD():
    gray = i4.copy()
    for x in range(i4.shape[1]):
        for y in range(i4.shape[0]):
            gray[y][x]= (0.11 * i4[y][x][0] + 0.6 * i4[y][x][1] + 0.3 * i4[y][x][2])
    cv2.imwrite('horse_gray.jpg',gray)
    pass

partA()
partB()
partC()
partD()
