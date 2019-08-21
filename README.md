# fast-serialization-note

- **Serialization** is the process of translating data structures or object state into a format that can be stored (for example, in a file or memory buffer) or transmitted (for example, across a network connection link) and reconstructed later (possibly in a different computer environment).When the resulting series of bits is reread according to the serialization format, it can be used to create a semantically identical clone of the original object.

  - A method of transferring data through the wires (messaging).
  - A method of storing data (in databases, on hard disk drives).
  - A method of remote procedure calls, e.g., as in SOAP.
  - A method for distributing objects, especially in component-based software engineering such as COM, CORBA, etc.
  - A method for detecting changes in time-varying data.

- When VM "Full GC", is need 'offload' parts of the objects to the non-java heap (directly allocated from the OS) ('unmanaged' memory).  In order to save arbitrary objects into unmanaged memory,the most viable solution is the use of Serialization. This means the application serializes objects into the offheap memory, later on the object can be read using deserialization.

- **Features**

  - ***Json serialization*** use Jackson-core to parse/generate Json. Other than existing solutions (e.g. Jackson Databind or Boon) it is fully precise (Object Graph is identical after deserialization) and supports/restores cyclic and interlinked object graphs same as serialization.
  
  - ***Minbin*** a second layer to provide the foundation to create structured binary streams.
  
    A MinBin stream consists of primitives, and tags which signal start+end of more complex composed data structures.
  
  - ***Offheapmap - persistent map*** (not meant as an IPC mechanism and do not support concurrent access from several processes.)
  
  - ***Serialization***
  
  - ***Structs*** enable storage of structured data in a continuous block of memory. The memory can be allocated on the heap using a byte[] array or can be allocated off the java heap in native memory.
  
    Store/cache huge amounts of data records without impact on GC duration
    
    Highperformance data transfer in a cluster or inbetween processes
  
