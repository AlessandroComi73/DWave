#%%
import dimod
import dwave.inspector
import dwave.system
from dwave.system import DWaveSampler, EmbeddingComposite
sampler_auto = EmbeddingComposite(DWaveSampler(solver={'topology__type': 'pegasus'}))
# %%
linear = {('a', 'a'): -1, ('b', 'b'): -1, ('c', 'c'): -1}
quadratic = {('a', 'b'): 2, ('b', 'c'): 2, ('a', 'c'): 2}
Q = {**linear, **quadratic}

sampleset = sampler_auto.sample_qubo(Q, num_reads=1000)
# %%
print(sampleset) 

# %%
dwave.inspector.show(sampleset)
