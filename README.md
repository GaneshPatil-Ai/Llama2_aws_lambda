## Why serverless?
AWS Lambda provides us with the ability to deploy our code without the need of setting up and hosting a server. This not only creates the advantage of fast deployment but also several other benefits for developers. Here are the three main advantages which are of our benefit:

#### Scalability: 
Serverless platforms automatically handle the scaling of your application. They can quickly adjust the number of resources allocated based on the load. As a result your application is ablet to handle sudden spikes in traffic without manual intervention.

#### Cost-efficient: 
Traditional server-based setups require you to provision and pay for fixed resources, even if they’re not fully utilized. Serverless automatically allocates cloud resources on demand and releases them when there is no traffic. In this way you pay only for the compute resources you actually use

#### Reduced Operations Overhead:
Serverless platforms hide the complexity of the infrastructure management. You don’t have to worry about provisioning, patching, or maintaining servers. This reduces the operational overhead and allows developers to focus more on writing code.
Those three points are important if we want to have a scalable and cost-efficient deployment of LLama 2.

Is a High-Grade GPU Required for LLama 2?
This is a question which probably comes to your mind, considering that AWS Lambda runs on a CPU and doesn’t provide GPU access. Generally speaking, all vanilla LLMs are resource-hungry and require high-end GPUs to run, however thanks to quantization approaches we are now able to run them also locally on CPUs.
In our case llama.cpp is the solution to this problem, allowing us to run a quantized version of the model ported to C++ for even more efficient inference. We are going to use it in addition with llama.cpp python bindings.
To use llama.cpp you will need a quantized version of the model (TODO: which you can creating following this post) or a pre-quantized model provided by TheBloke in HuggingFace.
Prerequisites
For this tutorial you will need:
An active AWS subscription (which could incur cost)
Docker
AWS CLI (configured for your AWS subscription)
(Optional) Terraform (for automatic deployment)
Assuming that you have everything installed and configured, lets get started.
Creating an AWS Lambda Image
AWS Lambda provides the option to upload your code as a zip or provide it as a Docker image. The former method has a memory limit of 250 MB which is of our concern because of the model size and the additional libraries needed. The latter is also limited, however, Docker Images can be up to 10 GB of size which will cover our needs. In the following, we will create a Docker image that contains the code, the needed libraries and the LLama 2 model itself.
In our case [llama.cpp](https://github.com/ggerganov/llama.cpp) is the solution to this problem, allowing us to run a quantized version of the model ported to C++ for even more efficient inference. We are going to use it in addition with [llama.cpp python bindings](https://github.com/abetlen/llama-cpp-python).
To use [llama.cpp](https://huggingface.co/TheBloke) you will need a quantized version of the model (TODO: which you can creating following this post) or a pre-quantized model provided by [TheBloke](https://huggingface.co/TheBloke) in HuggingFace.
