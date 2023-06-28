---
jupytext:
  formats: md:myst
  text_representation:
    extension: .md
    format_name: myst
    format_version: 0.13
    jupytext_version: 1.11.5
kernelspec:
  display_name: Python 3
  language: python
  name: python3
---
```{code-cell} ipython3
import numpy as np
import matplotlib.pyplot as plt
```
```{code-cell} ipython3
from allensdk.core.brain_observatory_cache import BrainObservatoryCache
boc = BrainObservatoryCache()
```

# Visual stimuli

As we saw in the [overview](vc2p-dataset.md), there were a range of visual stimuli presented to the mice in these experiments. 

```{code-cell} ipython3
boc.get_all_stimuli()
```

Here we will look at each stimulus, and what information we have about its presentation.

## Drifting gratings

The drifting gratings stimulus consists of a sinusoidal grating that is presented on the monitor that moves orthogonal to the orientation of the grating, moving in one of 8 directions (called <b>orientation</b>) and at one of 5 <b>temporal frequencies</b>. The grating has a spatial frequency of 0.04 cycles per degree and a contrast of 80%.

Let's find the session in the experiment container we're exploring that contains the drifting gratings stimulus.

```{code-cell} ipython3
experiment_container_id = 511510736
session_id = boc.get_ophys_experiments(experiment_container_ids=[experiment_container_id], stimuli=['drifting_gratings'])[0]['id']
data_set = boc.get_ophys_experiment_data(ophys_experiment_id=session_id)
```

Let's look at the stimulus table for the drifting gratings stimulus

```{code-cell} ipython3
drifting_gratings_table = data_set.get_stimulus_table('drifting_gratings')
drifting_gratings_table.head()
```

## Static gratings

## Natural scenes

## Natural movies

## Locally sparse noise

## Spontaneous activity