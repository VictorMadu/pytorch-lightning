# Multi-node examples
Use these templates for multi-node training

## Simplest example.   
1. Modify this script with your CoolModel file.   
2. Update and submit [this bash script](https://github.com/williamFalcon/pytorch-lightning/blob/master/examples/new_project_templates/multi_node_examples/minimal_multi_node_demo_script.sh)   
```bash
squeue minimal_multi_node_demo_script.sh
```

## Grid search on a cluster   

#### Option 1: Run on cluster using your own SLURM script    
The trainer and model will work on a cluster if you configure your SLURM script correctly.   

1. Update [this demo slurm script]().  
2. Submit the script   
```bash
$ squeue demo_script.sh
```

Most people have some way they automatically generate their own scripts.  
To run a grid search this way, you'd need a way to automatically generate scripts using all the combinations of 
hyperparameters to search over.   

#### Option 2: Use test-tube for SLURM script
With test tube we can automatically generate slurm scripts for different hyperparameter options.   

To run this demo:    
```bash
source activate YourCondaEnv

python multi_node_cluster_auto_slurm.py --email your@email.com --gpu_partition your_partition --conda_env YourCondaEnv
```

That will submit 6 jobs. Each job will have a specific combination of hyperparams. Each job will also run on 2 nodes
where each node has 8 gpus.   