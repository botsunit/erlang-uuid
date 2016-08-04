

# Module uuid #
* [Description](#description)
* [Data Types](#types)
* [Function Index](#index)
* [Function Details](#functions)

Erlang UUID.

Copyright (c) 2010-2013 Per Andersson

__Authors:__ Per Andersson ([`avtobiff@gmail.com`](mailto:avtobiff@gmail.com)).

__References__* See [RFC 4122](http://www.ietf.org/rfc/rfc4122.txt)
for more information.
-----------------------------------------------------------------------------

<a name="description"></a>

## Description ##

Currently implements UUID v1, v3, v4, and v5 as of RFC 4122.

Example usage

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

<a name="types"></a>

## Data Types ##




### <a name="type-urn">urn()</a> ###


<pre><code>
urn() = string()
</code></pre>




### <a name="type-uuid">uuid()</a> ###


<pre><code>
uuid() = binary()
</code></pre>




### <a name="type-uuid_string">uuid_string()</a> ###


<pre><code>
uuid_string() = string()
</code></pre>

<a name="index"></a>

## Function Index ##


<table width="100%" border="1" cellspacing="0" cellpadding="2" summary="function index"><tr><td valign="top"><a href="#get_node-0">get_node/0</a></td><td>Get node id (IEEE 802 (MAC) address).</td></tr><tr><td valign="top"><a href="#is_v1-1">is_v1/1</a></td><td>Predicate for checking that supplied UUID is version 1.</td></tr><tr><td valign="top"><a href="#is_v3-1">is_v3/1</a></td><td>Predicate for checking that supplied UUID is version 3.</td></tr><tr><td valign="top"><a href="#is_v4-1">is_v4/1</a></td><td>Predicate for checking that supplied UUID is version 4.</td></tr><tr><td valign="top"><a href="#is_v5-1">is_v5/1</a></td><td>Predicate for checking that supplied UUID is version 5.</td></tr><tr><td valign="top"><a href="#is_valid-1">is_valid/1</a></td><td>Predicate for checking that supplied UUID is valid.</td></tr><tr><td valign="top"><a href="#to_binary-1">to_binary/1</a></td><td>Format UUID binary from string.</td></tr><tr><td valign="top"><a href="#to_string-1">to_string/1</a></td><td> Format UUID string from binary.</td></tr><tr><td valign="top"><a href="#to_string-2">to_string/2</a></td><td></td></tr><tr><td valign="top"><a href="#to_uuid_urn-1">to_uuid_urn/1</a></td><td> Create UUID URN from UUID binary or string.</td></tr><tr><td valign="top"><a href="#uuid1-0">uuid1/0</a></td><td>Create a UUID v1 (timebased).</td></tr><tr><td valign="top"><a href="#uuid1-2">uuid1/2</a></td><td></td></tr><tr><td valign="top"><a href="#uuid3-2">uuid3/2</a></td><td> Create a UUID v3 (name based, MD5 is hashing function) as a binary.</td></tr><tr><td valign="top"><a href="#uuid4-0">uuid4/0</a></td><td> Create a UUID v4 (random) as a binary.</td></tr><tr><td valign="top"><a href="#uuid5-2">uuid5/2</a></td><td> Create a UUID v5 (name based, SHA1 is hashing function) as a binary.</td></tr><tr><td valign="top"><a href="#variant-1">variant/1</a></td><td>Return variant for supplied UUID.</td></tr><tr><td valign="top"><a href="#version-1">version/1</a></td><td>Return version for supplied UUID.</td></tr></table>


<a name="functions"></a>

## Function Details ##

<a name="get_node-0"></a>

### get_node/0 ###

<pre><code>
get_node() -&gt; binary()
</code></pre>
<br />

Get node id (IEEE 802 (MAC) address). Create random node id if hardware
address can't be found.

<a name="is_v1-1"></a>

### is_v1/1 ###

<pre><code>
is_v1(Uuid::<a href="#type-uuid">uuid()</a> | <a href="#type-uuid_string">uuid_string()</a>) -&gt; true | false
</code></pre>
<br />

Predicate for checking that supplied UUID is version 1.

<a name="is_v3-1"></a>

### is_v3/1 ###

<pre><code>
is_v3(Uuid::<a href="#type-uuid">uuid()</a> | <a href="#type-uuid_string">uuid_string()</a>) -&gt; true | false
</code></pre>
<br />

Predicate for checking that supplied UUID is version 3.

<a name="is_v4-1"></a>

### is_v4/1 ###

<pre><code>
is_v4(Uuid::<a href="#type-uuid">uuid()</a> | <a href="#type-uuid_string">uuid_string()</a>) -&gt; true | false
</code></pre>
<br />

Predicate for checking that supplied UUID is version 4.

<a name="is_v5-1"></a>

### is_v5/1 ###

<pre><code>
is_v5(Uuid::<a href="#type-uuid">uuid()</a> | <a href="#type-uuid_string">uuid_string()</a>) -&gt; true | false
</code></pre>
<br />

Predicate for checking that supplied UUID is version 5.

<a name="is_valid-1"></a>

### is_valid/1 ###

<pre><code>
is_valid(Uuid::<a href="#type-uuid">uuid()</a> | <a href="#type-uuid_string">uuid_string()</a>) -&gt; true | false
</code></pre>
<br />

Predicate for checking that supplied UUID is valid.

<a name="to_binary-1"></a>

### to_binary/1 ###

<pre><code>
to_binary(UuidStr::<a href="#type-uuid_string">uuid_string()</a>) -&gt; <a href="#type-uuid">uuid()</a>
</code></pre>
<br />

Format UUID binary from string.

<a name="to_string-1"></a>

### to_string/1 ###

<pre><code>
to_string(Uuid::<a href="#type-uuid">uuid()</a>) -&gt; <a href="#type-uuid_string">uuid_string()</a>
</code></pre>
<br />

Format UUID string from binary

<a name="to_string-2"></a>

### to_string/2 ###

<pre><code>
to_string(X1::simple | pretty, Uuid::<a href="#type-uuid">uuid()</a>) -&gt; <a href="#type-uuid_string">uuid_string()</a>
</code></pre>
<br />

<a name="to_uuid_urn-1"></a>

### to_uuid_urn/1 ###

<pre><code>
to_uuid_urn(UuidOrUrn::<a href="#type-uuid">uuid()</a> | <a href="#type-uuid_string">uuid_string()</a>) -&gt; <a href="#type-urn">urn()</a>
</code></pre>
<br />

Create UUID URN from UUID binary or string.

<a name="uuid1-0"></a>

### uuid1/0 ###

<pre><code>
uuid1() -&gt; <a href="#type-uuid">uuid()</a>
</code></pre>
<br />

Create a UUID v1 (timebased).

<a name="uuid1-2"></a>

### uuid1/2 ###

<pre><code>
uuid1(NodeArg::binary() | null, ClockSeqArg::binary() | null) -&gt; <a href="#type-uuid">uuid()</a>
</code></pre>
<br />

<a name="uuid3-2"></a>

### uuid3/2 ###

<pre><code>
uuid3(NamespaceOrUuid::atom() | <a href="#type-uuid_string">uuid_string()</a> | <a href="#type-uuid">uuid()</a>, Name::string()) -&gt; <a href="#type-uuid">uuid()</a>
</code></pre>
<br />

Create a UUID v3 (name based, MD5 is hashing function) as a binary.
Magic numbers are from Appendix C of the RFC 4122.

<a name="uuid4-0"></a>

### uuid4/0 ###

<pre><code>
uuid4() -&gt; <a href="#type-uuid">uuid()</a>
</code></pre>
<br />

Create a UUID v4 (random) as a binary

<a name="uuid5-2"></a>

### uuid5/2 ###

<pre><code>
uuid5(NamespaceOrUuid::atom() | <a href="#type-uuid_string">uuid_string()</a> | <a href="#type-uuid">uuid()</a>, Name::string()) -&gt; <a href="#type-uuid">uuid()</a>
</code></pre>
<br />

Create a UUID v5 (name based, SHA1 is hashing function) as a binary.
Magic numbers are from Appendix C of the RFC 4122.

<a name="variant-1"></a>

### variant/1 ###

<pre><code>
variant(Uuid::<a href="#type-uuid">uuid()</a> | <a href="#type-uuid_string">uuid_string()</a>) -&gt; reserved_microsoft | reserved_ncs | resered_future | rfc4122
</code></pre>
<br />

Return variant for supplied UUID.

<a name="version-1"></a>

### version/1 ###

<pre><code>
version(Uuid::<a href="#type-uuid">uuid()</a> | <a href="#type-uuid_string">uuid_string()</a>) -&gt; integer()
</code></pre>
<br />

Return version for supplied UUID.

