**Packed primitive primintrimsic trick**

It's slidely modified example from well known cgwiki, here is a [link](http://www.tokeru.com/cgwiki/index.php?title=HoudiniDops#Emit_packed_prims_into_RBD_sim).

What I want to show is technique of changing packed primitives on copies with very little overhead. What we need for this?
Just a little hack on mysterious primitive imtrimsic attributes. There is several types of packed prims for diffrent usage, but
one of them **packed fragments** have some special abilities that will helpful for this trick. **Packed fragments** prims are created
for rigib body sims, so they privide primitive imtrimsic attribute named: **fragmentname** to identify inviduals chunks.

In case if you already don't know that. How we can create those **packed fragmetns**, simplest way is just usual workflow with
assemle sop. Now you should understant everything in example files. Here is code for easy copy and pasting:

```cpp
int randomNumber = int(floor(fit01(random(@Frame + @primnum + 7), 0, 4))); //random num for every prim in every frame
string strRandomNumber = itoa(randomNumber);

setprimintrinsic(geoself(), "fragmentname", @primnum, "piece" + strRandomNumber); //here magic happends
```