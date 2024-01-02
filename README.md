# Wave Geometry

The following code will cover different geometrical wave shapes.

Similar to traditional shapes but where waves propagate throughout the geometry.

The code will cover the following wave based shapes: sphere, half sphere, cylinder, cone, cube, cuboid, pyramids and torus.


# Wave Geometric animation

fig = plt.figure()
ax = plt.axes(projection='3d')

Nbody2 = 100  # number of particles

lamb = 1E-5  # wavelength

phi = np.linspace(0, 4 * np.pi, Nbody2)  #  parameter

xyz = np.linspace(-1,1,Nbody2)

B = 10  # amplitude

def frame(w):
  ax.clear()
  global lamb, B

  A = B*np.cos(2*np.pi/lamb * xyz) # changing amplitude

  # Generate points

  points = structures.torus(None, A, 1, Nbody2, 0,0,0)

  #x, y, z = slice(x,y,z, -20, 20, -10, 10, -10, 10)
  
  plot = ax.scatter3D(points[0],points[1],points[2], c=points[2], cmap='viridis', marker='.')

  #ax.set_xlim(-1.5, 1.5)
  #ax.set_ylim(-1.5, 1.5)
  #ax.set_zlim(-1.5, 1.5)
  
  
  lamb*=0.9  # change wavelength

  B *= 1  # change ampltude

  return plot

plt.close()

anim = animation.FuncAnimation(fig, frame, frames=25, blit=False, repeat=True)
#anim.save('cubic.gif')
anim
