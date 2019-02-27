# Matplotlib

import matplotlib.pyplot as pyplot

## Basic Commands

plt.plot(x, y, 'r') #where r is for red

plt.xlabel
plt.ylabel
plt.title
plt.show()



### Multiple Plots

(rows, cols, plotnumber)
plt.subplot(1,2,1)
plt.plot (whatever)
plt.subplot(1,2,2)
plt.plot (whatever)


## Object Oriented Method

Idea is: create and object and then can call methods or attributes from that objects
The code is more complicated, but we can easily add more axes or series


eg.

Create figure
fig = plt.figure()

add set of axes (left, bottom, width, height)

axes = fig.add_axes([0.1, 0.1, 0.8, 0.8])

plot on those axes

axes.plot(x,y,'b')
axes.set_xkabel('set x label')
axes.set_ylabel('set y label')
axes.set_title('set title')



## Subplots()

similar to plt.figure except use tuple unpacking to grab fig and add_axes

fig, axes = plt.subplots()

Use the axes object to add stuff

axes.plot(x,y, 'r')
axes.set_xlabel()
axes.set_ylabel()


Specify the number of rows/cols/Subplots
fig, axes = plt.subplots(nrows=1, ncols=2)

where axes is now an array of axes to plot on, so you can loop through them

eg.

for ax in axes:
  ax.plot(x,y,'b')

Figure size and aspect ratio

fig = plt.figure(figsize=(8,4), dpi=100)

fig, axes = plt.subplots(figsize=(12,3))



Saving Figures

fig.savefig("filename.png")
fig.savefig("filename.png", dpi=200)




## Line and Market Styles

fig, ax = plt.subplots(figsize=(12,6))

ax.plot(x, x+1, color="red", linewidth=0.25)
ax.plot(x, x+2, color="red", linewidth=0.50)
ax.plot(x, x+3, color="red", linewidth=1.00)
ax.plot(x, x+4, color="red", linewidth=2.00)

### possible linestype options ‘-‘, ‘–’, ‘-.’, ‘:’, ‘steps’
ax.plot(x, x+5, color="green", lw=3, linestyle='-')
ax.plot(x, x+6, color="green", lw=3, ls='-.')
ax.plot(x, x+7, color="green", lw=3, ls=':')

### custom dash
line, = ax.plot(x, x+8, color="black", lw=1.50)
line.set_dashes([5, 10, 15, 10]) # format: line length, space length, ...

### possible marker symbols: marker = '+', 'o', '**', 's', ',', '.', '1', '2', '3', '4', ...
ax.plot(x, x+ 9, color="blue", lw=3, ls='-', marker='+')
ax.plot(x, x+10, color="blue", lw=3, ls='--', marker='o')
ax.plot(x, x+11, color="blue", lw=3, ls='-', marker='s')
ax.plot(x, x+12, color="blue", lw=3, ls='--', marker='1')

## marker size and color
ax.plot(x, x+13, color="purple", lw=1, ls='-', marker='o', markersize=2)
ax.plot(x, x+14, color="purple", lw=1, ls='-', marker='o', markersize=4)
ax.plot(x, x+15, color="purple", lw=1, ls='-', marker='o', markersize=8, markerfacecolor="red")
ax.plot(x, x+16, color="purple", lw=1, ls='-', marker='s', markersize=8,
        markerfacecolor="yellow", markeredgewidth=3, markeredgecolor="green");
