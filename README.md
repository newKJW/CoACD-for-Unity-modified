ORIGINAL WORK: (c) <Xinyue Wei/UCSD, 2025>  — Apache-2.0.

https://github.com/SarahWeiii/CoACD


Please refer to the original author's GitHub for usage instructions.

if you read already, you can understand what i'm saying below.

git URL for Unity Package Manager: https://github.com/newKJW/CoACD-for-Unity-modified.git

.

How to use function 'Calculate Colliders from FBXfile':

drag the FBX file from Project(== file explorer of unity editor) to 'targetFBX' box.

then run 'Calculate Colliders from FBXfile'.

.

function 'Remove all MeshColliders': you can use this function if something went wrong.

basically, when the CoACD script is removed, the colliders it created are also removed.

meanwhile, created convex meshes used to create colliders are not automatically deleted from the Project.

you can delete them without worry.

.

TIPS: 'preprocess mode' has three modes: auto, on, off.

'auto' decides whether do preprocess by its own algorithm. (in my opinion, not recommended)

'on' preprocesses regardless of mesh's property.

'off' doesn't preprocess regardless of mesh's property.

.

'mesh's property' can be broadly classified into two categories.

.

1: concave. in this case, 'off' is highly recommended - much faster, much more accurate.

however, you have to sure your mesh is concave. if you run 'off' mode with non-concave mesh

((has non-manifold) || (has self-intersecting) || (has loose parts are stored in a single mesh data)),

process will return error or will stuck in infinity-loop.

.

2: non-concave. in this case, you can use 'auto' or 'on' mode.

to get high quality convex meshes, i recommend you increase 1:'preprocess resolution', 2:'threshold' rather than other options. 

however, you may not be satisfied with the output.

if you are, consider editing the mesh(FBX file) using third-party modeling program(s) to run with 'off' mode.

'Calculate Colliders from FBXfile' calculates all mesh datas in single FBX file. therefore,

if the FBX file you editing is difficult to merge loose concave mesh parts into a single concave mesh,


You can try this function by creating each loose part with its own mesh data.

