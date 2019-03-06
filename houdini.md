# Vex

http://www.tokeru.com/cgwiki/index.php?title=HoudiniGettingStarted

# Python

### Profiling
```python
def cook():
    poly = geo.createPolygon()
    for position in (0,0,0), (1,0,0), (0,1,0):
        point = geo.createPoint()
        point.setPosition(position)
        poly.addVertex(point)
 
cook()
 
 
# or Import cProfile and use cProfile.runctx to call your function instead of calling it directly:
  
def cook():
    poly = geo.createPolygon()
    for position in (0,0,0), (1,0,0), (0,1,0):
        point = geo.createPoint()
        point.setPosition(position)
        poly.addVertex(point)
 
cProfile.runctx('cook()', globals(), locals())
 
 
#This will print a summary of your script’s run time to the Python shell when the node cooks.
```

### Making the SOP interruptible
```python
geo = hou.pwd().geometry()
 
# Evaluate the "t" parameter to see how much to translate each point.
translation = hou.Vector3(hou.parmTuple("t").eval())
 
for point in geo.points():
    # Set the new position for each point.
    point.setPosition(point.position() + translation)
 
    # Check if the user pressed Escape.
    if hou.updateProgressAndCheckForInterrupt():
        break
```        
