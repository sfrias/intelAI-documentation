# Optimization

Requirements

- [Intel optimzed Python](https://software.intel.com/en-us/distribution-for-python)


## Tensorflow 
Requirements

- [Intel optimzed Tensorflow](https://software.intel.com/en-us/articles/intel-optimized-tensorflow-installation-guide)

Add this snippet on top of your code

`
os.environ["OMP_NUM_THREADS"] = "64"
os.environ["KMP_BLOCKTIME"] = "0"
os.environ["KMP_SETTINGS"] = "1"
os.environ["KMP_AFFINITY"]= "granularity=fine,verbose,compact,1,0"
FLAGS = tf.app.flags.FLAGS
tf.app.flags.DEFINE_integer('inter_op', 1, """Inter Op Parallelism Threads.""")
tf.app.flags.DEFINE_integer('intra_op', 64, """Intra Op Parallelism Threads.""") 
numactl --interleave=all python <script name>
` 

## Keras
Requirements

- [Intel optimzed Tensorflow](https://software.intel.com/en-us/articles/intel-optimized-tensorflow-installation-guide)

Add this snippet on top of your code

`
os.environ["OMP_NUM_THREADS"] = "64"
os.environ["KMP_BLOCKTIME"] = "0"
os.environ["KMP_SETTINGS"] = "1"
os.environ["KMP_AFFINITY"]= "granularity=fine,verbose,compact,1,0"
FLAGS = tf.app.flags.FLAGS
tf.app.flags.DEFINE_integer('inter_op', 1, """Inter Op Parallelism Threads.""")
tf.app.flags.DEFINE_integer('intra_op', 64, """Intra Op Parallelism Threads.""") 
numactl --interleave=all python <script name>
`
## Pytorch 
Add this snippet on top of your code

`
os.environ["OMP_NUM_THREADS"] = "64"
os.environ["KMP_BLOCKTIME"] = "0"
os.environ["KMP_SETTINGS"] = "1"
os.environ["KMP_AFFINITY"]= "granularity=fine,verbose,compact,1,0"
numactl --interleave=all python <script name> 
`

As of now, its almost same for Pytorch, only the tf flags have been removed. Benchmarks will be listed once Intel releases it.

To gather more knowledge you can refer to these resources:

- [Performance of Classic Matrix Multiplication Algorithm on Intel® Xeon Phi™ Processor System by Sergey Kostrov](https://software.intel.com/en-us/articles/performance-of-classic-matrix-multiplication-algorithm-on-intel-xeon-phi-processor-system)
