# Parallelization Experiments

Here's a fun test case for parallelization.  In essence we're populating a
matrix by simulation, with each row corresponding to one simulation of a given
firm's inventory process.

The firm's inventory process is of (s, S) type with stochastic IID demand.

The notebook "inventory_dynamics.ipynb" is just for background.  I (jstac)
wrote it for a workshop.

The notebook "efficient_inventory_dynamics.ipynb" runs the simulation
described above.

I parallelize the task with `numba.prange`.  Numba does a great job of
parallelizing this task efficiently --- which is non-trivial, because the
execution time of each round of the loop is very small (firm's inventory is
simulated for only 400 periods).

Question: How do Matlab and Julia's simple parallelization implementations do
on this task?

I'm mainly interested in naive implementations that essentially leave the
logic unchanged.  That is, I want to know how good each of the parallelization
interfaces is for collecting low hanging fruit.
