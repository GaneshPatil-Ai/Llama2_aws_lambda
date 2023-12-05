# llama-lambda
Deploying LLama 2 as AWS Lambda function for scalable serverless inference with the help of ECR

[llama.cpp](https://github.com/ggerganov/llama.cpp) is the solution to this problem, allowing us to run a quantized version of the model ported to C++ for even more efficient inference. We are going to use it in addition with [llama.cpp python bindings](https://github.com/abetlen/llama-cpp-python).
To use [llama.cpp](https://huggingface.co/TheBloke) you will need a quantized version of the model (TODO: which you can creating following this post) or a pre-quantized model provided by [TheBloke](https://huggingface.co/TheBloke)in HuggingFace.
