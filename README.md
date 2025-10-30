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

function 'Remove Componenet And Colliders(in list)', 'Remove Colliders(in list)', 'Remove *ALL* MeshColliders':

basically, the component doesn't remove the colliders it created when the component itself is removed.

you can use these functions to remove them.

meanwhile, created convex meshes used to create colliders are not automatically deleted from the Project.

you can delete them without worry.

.

TIP 1: 'preprocess mode' has three modes: auto, on, off.

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

.

TIP 2: if you are using unity Probuilder, make the first MeshCollider component exists for Probuilder's auto collider generator.

Probuilder replaces the sharedmesh of first meshcollider component to its mesh automatically - just leave it. all you have to do is uncheck the first meshcollider.

.

TIP 3: if you are generating colliders for a prefab, use prefab editing mode.

double-click your prefab in the Project.

the target object you want to generate colliders in prefab(including itself) should be selected in the Hierachy, not Project. no more explanation.

