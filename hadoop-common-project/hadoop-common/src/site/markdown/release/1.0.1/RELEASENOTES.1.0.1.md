
<!---
# Licensed to the Apache Software Foundation (ASF) under one
# or more contributor license agreements.  See the NOTICE file
# distributed with this work for additional information
# regarding copyright ownership.  The ASF licenses this file
# to you under the Apache License, Version 2.0 (the
# "License"); you may not use this file except in compliance
# with the License.  You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
-->
# Apache Hadoop  1.0.1 Release Notes

These release notes cover new developer and user-facing incompatibilities, important issues, features, and major improvements.


---

* [MAPREDUCE-3184](https://issues.apache.org/jira/browse/MAPREDUCE-3184) | *Major* | **Improve handling of fetch failures when a tasktracker is not responding on HTTP**

The TaskTracker now has a thread which monitors for a known Jetty bug in which the selector thread starts spinning and map output can no longer be served. If the bug is detected, the TaskTracker will shut itself down. This feature can be disabled by setting mapred.tasktracker.jetty.cpu.check.enabled to false.


---

* [HADOOP-7470](https://issues.apache.org/jira/browse/HADOOP-7470) | *Minor* | **move up to Jackson 1.8.8**

**WARNING: No release note provided for this change.**


---

* [HADOOP-8037](https://issues.apache.org/jira/browse/HADOOP-8037) | *Blocker* | **Binary tarball does not preserve platform info for native builds, and RPMs fail to provide needed symlinks for libhadoop.so**

This fix is marked "incompatible" only because it changes the bin-tarball directory structure to be consistent with the source tarball directory structure.  The source tarball is unchanged.  RPMs and DEBs now use an intermediate bin-tarball with an "${os.arch}" tag (like the packages themselves). The un-tagged bin-tarball is now multi-platform and retains the structure of the source tarball; it is in fact generated by target "tar", not by target "binary". Finally, in the 64-bit RPMs and DEBs, the native libs go in the "lib64" directory instead of "lib".


---

* [HADOOP-8009](https://issues.apache.org/jira/browse/HADOOP-8009) | *Critical* | **Create hadoop-client and hadoop-minicluster artifacts for downstream projects**

Generate integration artifacts "org.apache.hadoop:hadoop-client" and "org.apache.hadoop:hadoop-minicluster" containing all the jars needed to use Hadoop client APIs, and to run Hadoop MiniClusters, respectively.  Push these artifacts to the maven repository when mvn-deploy, along with existing artifacts.



