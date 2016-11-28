

# Erlang UUID #


This module implements UUID v1, v3, v4, and v5 as of RFC 4122<br />
(UUID variant 1 0).

UUID v1 return a UUID generated by a timestamp and node id.<br />
UUID v3 return a UUID generated using MD5 and a given name within a namespace.<br />
UUID v4 return a UUID generated by a (pseudo) random number generator.<br />
UUID v5 return a UUID generated using SHA1 and a given name within a namespace.

Source tracking available at [http://github.com/avtobiff/erlang-uuid](http://github.com/avtobiff/erlang-uuid)

To clone the main developing repository invoke
```

git clone https://github.com/avtobiff/erlang-uuid.git

```



## BUILD AND INSTALL ##

Build by invoking

```

make

```

Include in your own project using Rebar. Add this to your rebar.config

```

{uuid, ".*",
 {git, "https://github.com/avtobiff/erlang-uuid.git", "master"}}

```


## LICENSE ##

Erlang UUID is free software: you can redistribute it and/or modify
it under the terms of the GNU Lesser General Public License as
published by the Free Software Foundation, either version 3 of the
License, or (at your option) any later version.

Erlang UUID is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU Lesser General Public License for more details.

You should have received a copy of the GNU Lesser General Public
License along with Erlang UUID.  If not, see
>http://www.gnu.org/licenses/>.


## USE ##

Example of usage

```

1> uuid:to_string(uuid:uuid1()).
"f412e400-c445-1131-bdc6-03f9e757eb34"
2> uuid:to_string(uuid:uuid3(dns, "fqdn.example.com")).
"06eaa791-8c2e-3b0d-8a07-c80979fd1b98"
3> uuid:to_string(uuid:uuid3(uuid:uuid4(), "my name")).
"fcf82b93-aa5e-3d79-b95e-726420f89e1b"
4> uuid:to_string(uuid:uuid4()).
"79f492f8-1337-4200-abcd-92bada1cacao"
5> uuid:to_string(uuid:uuid5(dns, "fqdn.example.com")).
"8fd7fa87-4c20-5809-a1b0-e07f5c224f02"
6> uuid:to_string(uuid:uuid5(uuid:uuid4(), "my name")).
"6ff58b11-e0b2-536c-b6be-bdccd38836a2"

```


## UUID v1 ##

UUID v1 uses the number of 100 nanosecond intervals since the west adopted the
gregorian calendar and the node id IEEE 802 (MAC) address. It is hackishly
implemented and improvements can be made.

Room for improvement:
* Timestamp resolution is one (1) second which should be improved.

* Clock sequence is random (simulating state is always unavailable).




## UUID v3 - UUID v5 ##

UUID v3 and UUID v5 uses MD5 and SHA1, respectivaly, to generate a UUID using a
name and a namespace as initializer. Valid namespaces are the atoms: url, dns,
oid, x500, nil or using a generated UUID either as a binary or as a UUID string
representation.


## UUID v4 ##

UUID v4 uses randomness to create a UUID, the six version and variant bits are
set all the other 122 bits are randomly generated.


## UTILITIES ##

There are several utility functions for introspection of UUIDs.

It is possible to extract variant and version with the functions with the same
names, both take a UUID binary or UUID string representation.

There are several predicate functions that takes a UUID binary or UUID string
representation and returns a thruth value. The predicate is_rfc4122/1 returns
true if the UUID implements RFC 4122 (variant 1 0, version 1, 3, 4, and 5). The
predicates is_vN/1, where N is either 1, 3, 4, or 5.

Example usage:

```

1> uuid:version(uuid:uuid4()).
4
2> uuid:is_v1(uuid:uuid4()).
false
3> uuid:is_v1(uuid:uuid1()).
true
4> uuid:is_rfc4122(uuid:uuid4()).
true
5> uuid:is_valid(uuid:uuid4()).
true
6> uuid:is_valid(<<1:128>>).
false

```
Per Andersson <avtobiff@gmail.com>

## Modules ##


<table width="100%" border="0" summary="list of modules">
<tr><td><a href="uuid.md" class="module">uuid</a></td></tr></table>
