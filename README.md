# ModuleQNN
ModuleQNN Code Description
========
ModuleQNN is a codebase used for automatically designing convolutional neural network architectures outlined in the paper: 

Y. Chen, Z. Wang, Z. J. Wang, X. Kang,“Automated Design of Neural Network Architectures with Reinforcement Learning for Detection of Global Manipulations”, IEEE Journal of Selected Topics in Signal Processing, vol. 20, no. 5, pp. 997-1011, Aug. 2020. 

## Example 

This is a quick example to design neural network architectures by sequentially selecting optimal modules with fixed parameters by using Q-Learning. The variable parameters 
can be set as needed. 

Experiment configurations are stored in the `models` folder. Each experiment contains a `hyper_parameters.py` file that contains 
optimization hyperparameters, data paths, etc., and a `state_space_parameters.py` file that contains state space specifications.

Program implementation:
1. Create database and the corresponding txt files on server you plan to use for training 
 In this example, the database and txt files are stored in the `forensic_data` folder.
2. set `TRAIN_FILE`,`VAL_FILE`,`CAFFE_ROOT`, `CHECKPOINT_DIR` 
 in the `hyper_parameters.py`
3. Create directory `forensics_logs` to store Q-values and replay database
4. Start Q-Learning Server

    ```bash 
    python q_server.py forensics forensics_logs
    ```
5. On each server you want to use for training start a Q-Learning Client
If you want to use a specific gpu, for example GPU 0
    ```bash
    python caffe_client.py forensics unique_client_identifier server_ip_addr -gpu 0
    ```

The top CNN (ModuleQNN-A) for multi-purpose forensics and detection of processing history are stored in the `ModuleQNN-A_CNN` folder. 

## Citation

If our code or paper helps your research or project, please cite us:

Y. Chen, Z. Wang, Z. J. Wang, X. Kang,“Automated Design of Neural Network Architectures with Reinforcement Learning for Detection of Global Manipulations”, IEEE Journal of Selected Topics in Signal Processing, vol. 20, no. 5, pp. 997-1011, Aug. 2020. 
