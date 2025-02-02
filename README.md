<p align="center">
<!-- Link to tutorials badge using shields.io -->
<!-- Follow on twitter badge using shields.io -->
  <a href="https://yuchenlin.xyz/swiftsage/">
    <img src="https://img.shields.io/badge/Website-💻-red">
  </a>
  <a href="https://arxiv.org/abs/2305.17390">
    <img src="https://img.shields.io/badge/Paper-📝-blue">
  </a> 
</p>



# SwiftSage

* We introduce **SwiftSage**, a novel agent framework inspired by the [dual-process theory](https://en.wikipedia.org/wiki/Dual_process_theory) of human cognition, designed to excel in action planning for complex interactive reasoning tasks. SwiftSage integrates the strengths of behavior cloning and prompting large language models (LLMs) to enhance task completion performance.
* The framework comprises two primary modules: the **Swift** module, representing fast and intuitive thinking, and the **Sage** module, emulating deliberate thought processes. The Swift module is a small encoder-decoder LM fine-tuned on the oracle agent's action trajectories (i.e., [imitation learning / behavior cloning](https://sites.google.com/view/icml2018-imitation-learning/)), while the Sage module employs LLMs such as [GPT-4](https://openai.com/research/gpt-4) for subgoal planning and grounding. We develop a heuristic method to harmoniously integrate the two modules, resulting in a more efficient and robust problem-solving process.
* In 30 tasks from the [ScienceWorld](https://sciworld.apps.allenai.org) benchmark, **SwiftSage** significantly outperforms other methods such as [SayCan](https://say-can.github.io), [ReAct](https://react-lm.github.io), and [Reflexion](https://arxiv.org/abs/2303.11366), demonstrating its effectiveness in solving complex real-world tasks.

### Authors: 
Bill Yuchen Lin, Yicheng Fu, Karina Yang, Prithviraj Ammanabrolu, Faeze Brahman, Shiyu Huang, Chandra Bhagavatula, Yejin Choi, Xiang Ren.  ([AI2-Mosaic](https://mosaic.allenai.org) and  [USC-INK](http://inklab.usc.edu/)).

## Comparisons  
![](https://yuchenlin.xyz/swiftsage/methods.png)
## Framework 
![](https://yuchenlin.xyz/swiftsage/ss_pipeline.png)



## Installation


```bash
conda create -n sw python=3.8 pip
conda activate sw
pip install scienceworld==1.1.3
pip install -r requirements.txt
conda install -c conda-forge openjdk # if needed 
```





## Imitation learning 

<p>
<a href="https://huggingface.co/yuchenlin/swift_sw">
    <img src="https://img.shields.io/badge/Swift-🤗-green">
  </a>
</p>
You can skip this step by simply using our checkpoint here: https://huggingface.co/yuchenlin/swift_sw
It is based on Flan-t5-large (770m).

### Generating data for imitation learning (behavior cloning)

```bash
cd  fast_slow_agent/data_utils/
# unzip goldpaths-all.zip 
python data_convert.py 
```



### Train Swift Module 

```
cd fast_agent
bash ds_train.sh  
```


## The SwiftSage Agent

Note that we name SwiftSage as `fast_slow_agent` in the codebase. 

```bash 
bash run_eval_fast_slow.sh
```

The logs will be saved and the scripts for showing results and doing analysis are in the `analysis` folder.

## Evaluation  

### SayCan, ReAct, Reflexion 



Please check the `baselines` folder for the scripts and code.

### Other baseline methods

Check out: https://github.com/allenai/ScienceWorld
