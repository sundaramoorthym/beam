<!--
    Licensed to the Apache Software Foundation (ASF) under one
    or more contributor license agreements.  See the NOTICE file
    distributed with this work for additional information
    regarding copyright ownership.  The ASF licenses this file
    to you under the Apache License, Version 2.0 (the
    "License"); you may not use this file except in compliance
    with the License.  You may obtain a copy of the License at

      http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing,
    software distributed under the License is distributed on an
    "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
    KIND, either express or implied.  See the License for the
    specific language governing permissions and limitations
    under the License.
-->

# HDFS IO

This library provides HDFS sources and sinks to make it possible to read and
write Apache Hadoop file formats from Apache Beam pipelines.

Currently, only the read path is implemented. A `HDFSFileSource` allows any
Hadoop `FileInputFormat` to be read as a `PCollection`.

A `HDFSFileSource` can be read from using the
`org.apache.beam.sdk.io.Read` transform. For example:

```java
HDFSFileSource<K, V> source = HDFSFileSource.from(path, MyInputFormat.class,
  MyKey.class, MyValue.class);
PCollection<KV<MyKey, MyValue>> records = Read.from(mySource);
```

Alternatively, the `readFrom` method is a convenience method that returns a read
transform. For example:

```java
PCollection<KV<MyKey, MyValue>> records = HDFSFileSource.readFrom(path,
  MyInputFormat.class, MyKey.class, MyValue.class);
```
