# Blogs

## vex snippet, crowd, python and workflow

http://www.tokeru.com/cgwiki/index.php?title=HoudiniGettingStarted

http://lex.ikoon.cz/

## hdk houdini 12 introduction

http://www.deborahrfowler.com/C++Resources/HDK/HDK12_Intro.pdf

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
### example using numpy

https://www.sidefx.com/docs/hdk/_h_d_k__s_o_p__h_o_m__c_p_p__v_e_x.html

   41 import numpy
   42 
   43 geo = hou.pwd().geometry()
   44 positions = numpy.frombuffer(
   45     geo.pointFloatAttribValuesAsString("P"), dtype="f4,f4,f4").copy()
   46 positions.dtype.names = ("x", "y", "z")
   47 
   48 positions["y"] = numpy.sin(
   49     positions["x"] * 0.2 + positions["z"] * 0.3 + hou.frame() * 0.03)
   50 geo.setPointFloatAttribValuesFromString("P", positions)
