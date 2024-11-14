#Cubo 3D para Disciplina de Matemática

import numpy as np
import matplotlib.pyplot as plt
from mpl_toolkits.mplot3d import Axes3D
from matplotlib.animation import FuncAnimation

x = np.array([0, 0, 1, 1, 0, 0, 1, 1])
y = np.array([0, 1, 1, 0, 0, 1, 1, 0])
z = np.array([0, 0, 0, 0, 1, 1, 1, 1])

fig = plt.figure()
ax = fig.add_subplot(111, projection='3d')
ax.set_box_aspect([1,1,1])
edges = [
    (0, 1), (1, 2), (2, 3), (3, 0),
    (4, 5), (5, 6), (6, 7), (7, 4),
    (0, 4), (1, 5), (2, 6), (3, 7)
]

def update(angle):
    ax.cla()
    ax.scatter(x, y, z, color='red', s=100)
    for edge in edges:
        ax.plot([x[edge[0]], x[edge[1]]],
                [y[edge[0]], y[edge[1]]],
                [z[edge[0]], z[edge[1]]], color='red')
    ax.set_title("Cubo 3D Vermelho")
    ax.view_init(elev=20, azim=angle)

ani = FuncAnimation(fig, update, frames=np.arange(0, 360, 2), interval=50)
plt.show()
