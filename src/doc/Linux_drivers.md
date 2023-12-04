# Linux drivers

Device types:
* char module
* block module
* network module

 
## Snipeds 
All drivers should begin with 

```
module_init(<init_function>);
module_exit(<end_function>);
```
**modprobe**  or **insmod**  should call this functions to start the driver operation.
To utilize function reffered to the initialization, there is a special macro in linux called **__init**. This is an example of an init function, utilizing 







