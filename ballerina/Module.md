
## Overview

This is a generated connector for the [OpenAI Fine-tunes API](https://platform.openai.com/docs/api-reference/fine-tuning) OpenAPI specification. OpenAI is an American artificial intelligence research laboratory consisting of a non-profit corporation and a for-profit subsidiary. OpenAI conducts AI research with the declared intention of promoting and developing friendly AI. The OpenAI Fine-tunes API provides a way to customize new AI models developed by OpenAI for your specific needs.

## Setup guide

[//]: # (TODO: Add detailed steps to obtain credentials and configure the module.)

## Quickstart

To use the OpenAI Fine-tunes connector in your Ballerina application, update the `.bal` file as follows:

### Step 1: Import the connector
First, import the `ballerinax/openai.finetunes` module (along with the other required imports) as given below.

```ballerina
import ballerinax/openai.finetunes;
import ballerina/io;
```

### Step 2: Create a new connector instance
Create and initialize a `finetunes:Client` with the  obtained `apiKey`.
```ballerina
    finetunes:Client finetunesClient = check new ({
        auth: {
            token: "sk-XXXXXXXXX"
        }
    });
```

### Step 3: Invoke the connector operation
1. Now, you can use the operations available within the connector. 

   Following is an example on fine tuning the gpt-3.5-turbo model:

   ```ballerina
    public function main() returns error? {

        finetunes:CreateFileRequest req = {
            file: {fileContent: check io:fileReadBytes("sample.jsonl"), fileName: "sample.jsonl"},
            purpose: "fine-tune"
        };

        finetunes:OpenAIFile fileRes = check finetunesClient->/files.post(req);

        string fileId = fileRes.id;

        CreateFineTuningJobRequest fineTuneRequest = {
            model: "gpt-3.5-turbo",
            training_file: fileId
        };

        FineTuningJob fineTuneResponse = 
            check finetunesClient->/fine_tuning/jobs.post(fineTuneRequest);
        
        io:println(fineTuneResponse.id);
    }
   ``` 
2. Use the `bal run` command to compile and run the Ballerina program.

## Examples

The `OpenAI Finetunes` connector provides practical examples illustrating usage in various scenarios. Explore these [examples](https://github.com/module-ballerinax-openai-finetunes/tree/main/examples/), covering the following use cases:

[//]: # (TODO: Add examples)