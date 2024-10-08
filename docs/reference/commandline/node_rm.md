# node rm

<!---MARKER_GEN_START-->
Remove one or more nodes from the swarm

### Aliases

`docker node rm`, `docker node remove`

### Options

| Name                                | Type   | Default | Description                        |
|:------------------------------------|:-------|:--------|:-----------------------------------|
| [`-f`](#force), [`--force`](#force) | `bool` |         | Force remove a node from the swarm |


<!---MARKER_GEN_END-->

## Description

Removes the specified nodes from a swarm.

> [!NOTE]
> This is a cluster management command, and must be executed on a swarm
> manager node. To learn about managers and workers, refer to the
> [Swarm mode section](https://docs.docker.com/engine/swarm/) in the
> documentation.

## Examples

### Remove a stopped node from the swarm

```console
$ docker node rm swarm-node-02

Node swarm-node-02 removed from swarm
```

### Attempt to remove a running node from a swarm

Removes the specified nodes from the swarm, but only if the nodes are in the
down state. If you attempt to remove an active node you will receive an error:

```console
$ docker node rm swarm-node-03

Error response from daemon: rpc error: code = 9 desc = node swarm-node-03 is not
down and can't be removed
```

### <a name="force"></a> Forcibly remove an inaccessible node from a swarm (--force)

If you lose access to a worker node or need to shut it down because it has been
compromised or is not behaving as expected, you can use the `--force` option.
This may cause transient errors or interruptions, depending on the type of task
being run on the node.

```console
$ docker node rm --force swarm-node-03

Node swarm-node-03 removed from swarm
```

A manager node must be demoted to a worker node (using `docker node demote`)
before you can remove it from the swarm.

## Related commands

* [node demote](node_demote.md)
* [node inspect](node_inspect.md)
* [node ls](node_ls.md)
* [node promote](node_promote.md)
* [node ps](node_ps.md)
* [node update](node_update.md)
