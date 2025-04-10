# FSDP vs DeepSpeed

# FSDPv1 vs FSDPv2

***FSDP v1***

    fsdpv1 module as a single FlatParameter which is a single 1D tensor that contains all of the module parameters,

    Layer 
    ├── linear 1 (100,256)
    ├── linear 2 (100,512)
    ├── linear 3 (100,512)
    
    FlatParameter
    
    Flattensor--> tensor (100，1280)
    
    rank0                                       rank1
    tensor0 (100,640)                           tensor1 (100,640) 
    linear1 (100,256) linear 2 (100,384)        linear2 (100,128) linear3(100,512)

***FSDP v2***

    fsdpv2 module uses DTensor 

    rank0                                                       rank1
    linear1 (50,256) linear2 (50,512) linear3 (50,512)          linear1 (50,256) linear2 (50,512) linear3 (50,512)
    DTensor                                                     DTensor