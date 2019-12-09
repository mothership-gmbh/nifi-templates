# Abstract

Example to execute a simple query and then route if empty or not

# Solution

* Use ```ExecuteSQL``` processor in order to run filtering SQL query. The query was written to produce either a single record (match) or an empty record set (no match) in a way suggested by Shu.
* Connect ```ExecuteSQL``` to ```RouteOnAttribute``` processor in order to filter out unmatched flow files using the following value of routing property value ${executesql.row.count:replaceNull(0):gt(0)}


Notice, that the original content of a flow file will be lost after applying ExecuteSQL. It's not an issue in my case, because I do filtering before processing flow file content and my SQL query is based entirely on the flow file attributes and not on its content. Though in a more general scenario, when the flow file content is modified by the incoming part of the flow, one should save file content somewhere (e.g. file system) and restore it after the filtering part has applied.
