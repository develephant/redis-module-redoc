# RM_Utils API

### RMUtil_ArgExists
```
int RMUtil_ArgExists(const char *arg, RedisModuleString **argv, int argc, int offset);
```
 Return the offset of an arg if it exists in the arg list, or 0 if it's not there


### RMUtil_ParseArgs
```
int RMUtil_ParseArgs(RedisModuleString **argv, int argc, int offset, const char *fmt, ...);
```
Automatically conver the arg list to corresponding variable pointers according to a given format.
You pass it the command arg list and count, the starting offset, a parsing format, and pointers to the variables.
The format is a string consisting of the following identifiers:

    c -- pointer to a Null terminated C string pointer.
    s -- pointer to a RedisModuleString
    l -- pointer to Long long integer.
    d -- pointer to a Double
    * -- do not parse this argument at all

Example: If I want to parse args[1], args[2] as a long long and double, I do:
    double d;
    long long l;
    RMUtil_ParseArgs(argv, argc, 1, "ld", &l, &d);


### RMUtil_ParseArgsAfter
```
int RMUtil_ParseArgsAfter(const char *token, RedisModuleString **argv, int argc, const char *fmt, ...);
```
Same as RMUtil_ParseArgs, but only parses the arguments after `token`, if it was found.
This is useful for optional stuff like [LIMIT [offset] [limit]]


### RMUtil_GetRedisInfo
```
RMUtilInfo *RMUtil_GetRedisInfo(RedisModuleCtx *ctx);
```
 Get redis INFO result and parse it as RMUtilInfo.
 Returns NULL if something goes wrong.
 The resulting object needs to be freed with RMUtilRedisInfo_Free


### RMUtil_CreateFormattedString
```
RedisModuleString *RMUtil_CreateFormattedString(RedisModuleCtx *ctx, const char *fmt, ...);
```
 Create a new RedisModuleString object from a printf-style format and arguments.
 Note that RedisModuleString objects CANNOT be used as formatting arguments.


### RMUtil_StringEquals
```
int RMUtil_StringEquals(RedisModuleString *s1, RedisModuleString *s2);
```
 Return 1 if the two strings are equal. Case *sensitive*


### RMUtil_StringEqualsC
```
int RMUtil_StringEqualsC(RedisModuleString *s1, const char *s2);
```
 Return 1 if the string is equal to a C NULL terminated string. Case *sensitive*


### RMUtil_StringToLower
```
void RMUtil_StringToLower(RedisModuleString *s);
```
 Converts a redis string to lowercase in place without reallocating anything


### RMUtil_StringToUpper
```
void RMUtil_StringToUpper(RedisModuleString *s);
```
 Converts a redis string to uppercase in place without reallocating anything


### Vector_Get
```
int Vector_Get(Vector *v, size_t pos, void *ptr);
```
 get the element at index pos. The value is copied in to ptr. If pos is outside
 the vector capacity, we return 0
 otherwise 1


### Vector_Pop
```
int Vector_Pop(Vector *v, void *ptr);
```
 Get the element at the end of the vector, decreasing the size by one


### Vector_Resize
```
int Vector_Resize(Vector *v, size_t newcap);
```
 resize capacity of v


### Vector_Size
```
int Vector_Size(Vector *v);
```
 return the used size of the vector, regardless of capacity


### Vector_Cap
```
int Vector_Cap(Vector *v);
```
 return the actual capacity


### Vector_Free
```
void Vector_Free(Vector *v);
```
 free the vector and the underlying data. Does not release its elements if
 they are pointers