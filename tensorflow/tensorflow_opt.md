## Add this snippet on top of your code
os.environ["OMP_NUM_THREADS"] = "64"
os.environ["KMP_BLOCKTIME"] = "0"
os.environ["KMP_SETTINGS"] = "1"
os.environ["KMP_AFFINITY"]= "granularity=fine,verbose,compact,1,0"
FLAGS = tf.app.flags.FLAGS
tf.app.flags.DEFINE_integer('inter_op', 1, """Inter Op Parallelism Threads.""")
tf.app.flags.DEFINE_integer('intra_op', 64, """Intra Op Parallelism Threads.""") 
numactl --interleave=all python <script name>
