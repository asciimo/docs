---
acl_categories:
- '@write'
- '@slow'
- '@scripting'
arguments:
- display_text: library-name
  name: library-name
  type: string
arity: 3
command_flags:
- write
- noscript
complexity: O(1)
description: Deletes a library and its functions.
group: scripting
hidden: false
hints:
- request_policy:all_shards
- response_policy:all_succeeded
linkTitle: FUNCTION DELETE
since: 7.0.0
summary: Deletes a library and its functions.
syntax_fmt: FUNCTION DELETE library-name
syntax_str: ''
title: FUNCTION DELETE
---
Delete a library and all its functions.

This command deletes the library called _library-name_ and all functions in it.
If the library doesn't exist, the server returns an error.

For more information please refer to [Introduction to Redis Functions](/topics/functions-intro).

## Examples

```
redis> FUNCTION LOAD Lua mylib "redis.register_function('myfunc', function(keys, args) return 'hello' end)"
OK
redis> FCALL myfunc 0
"hello"
redis> FUNCTION DELETE mylib
OK
redis> FCALL myfunc 0
(error) ERR Function not found
```