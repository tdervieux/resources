Usd example

### Example that select all boundable prims 

```python
def GetConstantJointDataFromUsd (usdpath):
    dataDict = dict()
    stage = Usd.Stage.Open(usdpath)
    
    
    startPrim = stage.GetPrimAtPath(GetPrimPath())
    PREDICATE = Usd.TraverseInstanceProxies(Usd.PrimIsActive & Usd.PrimIsDefined & ~Usd.PrimIsAbstract)    
    boundables = [prim for prim in Usd.PrimRange(startPrim, PREDICATE) if prim.IsA(UsdGeom.Boundable)]
    
    for prim in boundables:
        print "prim",prim
        binding = UsdSkel.BindingAPI.Apply(prim)

        ji=binding.GetJointIndicesPrimvar()
        if ji.GetInterpolation() == UsdGeom.Tokens.constant:
            dataDict[prim.GetPath().pathString] = {"jointIndices":ji.Get(),
                "jointWeights":binding.GetJointWeightsPrimvar().Get()}
    return dataDict
```            
