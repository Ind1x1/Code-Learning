<pre><code>Pytorch/ 
├── DeviceMesh.py/
</code></pre>

### DeviceMesh.py
***torch.distributed.device_mesh.py***

    In the first example:
    Calling mesh_2d["tp"] on rank 0, 1, 2, 3 returns a 1D submesh of DeviceMesh:([0, 1, 2, 3]).
    Calling mesh_2d["tp"] on rank 4, 5, 6, 7 returns a 1D submesh of  DeviceMesh:([4, 5, 6, 7]).
    Calling mesh_2d["dp"] on rank 0, 4 returns a 1D submesh of  DeviceMesh:([0, 4]).
    Calling mesh_2d["dp"] on rank 1, 5 returns a 1D submesh of  DeviceMesh:([1, 5]).
    Calling mesh_2d["dp"] on rank 2, 6 returns a 1D submesh of  DeviceMesh:([2, 6]).
    Calling mesh_2d["dp"] on rank 3, 7 returns a 1D submesh of  DeviceMesh:([3, 7]).

    In the second example:
    Calling mesh_3d["dp", "cp"] on rank 0, 1, 4, 5 returns a 2D submesh of DeviceMesh:([[0, 1], [4, 5]]).
    Calling mesh_3d["dp", "cp"] on rank 2, 3, 6, 7 returns a 2D submesh of DeviceMesh:([[2, 3], [6, 7]]).
    Calling mesh_3d["cp", "dp"] on rank 0, 1, 4, 5 returns a 2D submesh of DeviceMesh:([[0, 4], [1, 5]]).
    Calling mesh_3d["cp", "dp"] on rank 2, 3, 6, 7 returns a 2D submesh of DeviceMesh:([[2, 6], [3, 7]]).

    ***example2***
    Machine：0，1，2，3，4，5，6，7 init_device_mesh(2,2,2)
           dp0     dp1
    pp0    0,1 --- 4,5
    pp1    2,3 --- 6,7
                                                        dp
    mesh_3d["cp", "dp"] =[[2,6], ======> dim0 -- cp -->[2,6]
                          [3,7]]                       [3,7]

