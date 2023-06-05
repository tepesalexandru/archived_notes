#azure #az-204 #dp-900 

`Azure Blob Storage` is a service that enables you to store massive amounts of unstructured data as binary large objects (*blobs*), in the cloud. Applications can read and write them by using the Azure Blob Storage API.

Blobs are stored in `containers`. You can control who can read and write blobs inside a container.

There are three types of blobs in Azure Blob Storage:

`Block blobs` - Can contain up to 50,000 blocks, giving a maximum size of over 4.7 TB. (each block has an upper limit of 100 MB). The best use for this type of blob is for very large data that changes very rarely or not at all.

`Page blobs` - They're a collection of 512-byte pages. They're optimized to support random read and write operations. They have an upper limit of 8 TB of data. This type of blob is used to implement `virtual disks` for `virtual machines`.

`Append blobs` - They're optimized for append operations. You can only add blocks to the end of an append blob. You cannot update or delete existing blocks. Each block has a maximum size of 4M, and the overall maximum space is over 195 GB.

---

Azure Blob Storage also provides three `access tiers`:
- Hot - The default, for data accessed frequently.
- Cool - Has lower performance, but reduced cost compared to the Hot tier. Mainly used for data that is accessed infrequently.
- Archive - Has the lowest cost, but that needs to be `rehydrated`. Only after the blob is rehydrated, the data from it can be read.

#### Examples:
You need to store data in Azure Blob storage for seven years to meet your company's compliance requirements. The retrieval time of the data is unimportant. The solution must minimize storage costs. Which storage tier should you use? `Archive`