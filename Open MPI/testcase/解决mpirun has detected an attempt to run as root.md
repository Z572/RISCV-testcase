# 解决mpirun has detected an attempt to run as root

## 摘要

在运行脚本的时候，经常会出现以下警告：

```mpirun has detected an attempt to run as root.```

这是在警告你，你在 root 上运行这个脚本。

## 操作步骤

以通过如下方式定义两个环境变量来允许 root 下也可以用 mpirun 。

```export OMPI_ALLOW_RUN_AS_ROOT=1```

```export OMPI_ALLOW_RUN_AS_ROOT_CONFIRM=1```

## 预期结果

成功运行脚本。

## 实际结果

与预期效果一致

```
ubuntukylin@ubuntukylin:~/git/mpitutorial/tutorials/mpi-send-and-receive/code$ sudo mpirun -n 5 ping_pong
[sudo] password for ubuntukylin: 
--------------------------------------------------------------------------
mpirun has detected an attempt to run as root.

Running as root is *strongly* discouraged as any mistake (e.g., in
defining TMPDIR) or bug can result in catastrophic damage to the OS
file system, leaving your system in an unusable state.

We strongly suggest that you run mpirun as a non-root user.

You can override this protection by adding the --allow-run-as-root option
to the cmd line or by setting two environment variables in the following way:
the variable OMPI_ALLOW_RUN_AS_ROOT=1 to indicate the desire to override this
protection, and OMPI_ALLOW_RUN_AS_ROOT_CONFIRM=1 to confirm the choice and
add one more layer of certainty that you want to do so.
We reiterate our advice against doing so - please proceed at your own risk.
--------------------------------------------------------------------------
```

设置环境变量之后

```
root@ubuntukylin:/home/ubuntukylin/git/mpitutorial/tutorials/mpi-send-and-receive/code# OMPI_ALLOW_RUN_AS_ROOT=1 OMPI_ALLOW_RUN_AS_ROOT_CONFIRM=1 mpirun -n 2 ping_pong
No protocol specified
No protocol specified
0 sent and incremented ping_pong_count 1 to 1
1 received ping_pong_count 1 from 0
1 sent and incremented ping_pong_count 2 to 0
0 received ping_pong_count 2 from 1
1 received ping_pong_count 3 from 0
1 sent and incremented ping_pong_count 4 to 0
0 sent and incremented ping_pong_count 3 to 1
1 received ping_pong_count 5 from 0
1 sent and incremented ping_pong_count 6 to 0
0 received ping_pong_count 4 from 1
0 sent and incremented ping_pong_count 5 to 1
0 received ping_pong_count 6 from 1
1 received ping_pong_count 7 from 0
1 sent and incremented ping_pong_count 8 to 0
1 received ping_pong_count 9 from 0
0 sent and incremented ping_pong_count 7 to 1
0 received ping_pong_count 8 from 1
0 sent and incremented ping_pong_count 9 to 1
0 received ping_pong_count 10 from 1
1 sent and incremented ping_pong_count 10 to 0
```


## 其他说明

该方法仅适用于 4.0 版本后的 Open MPI ，不适用于以往版本的 Open MPI 。
