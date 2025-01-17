_Authors_: @kanishkagu  \
_Created_: 2024/08/05 \
_Updated_: 2024/08/05 \
_Edition_: Swan Lake

# Sanitation for OpenAPI specification

This document records the sanitation done on top of the official OpenAPI specification from OpenAI Finetune. The OpenAPI specification is obtained from the [OpenAPI specification for the OpenAI API](https://github.com/openai/openai-openapi/blob/master/openapi.yaml). These changes are implemented to enhance the overall usability and readability of the generated client.

1. **Changed the `status_details` property parameters of the `OpenAIFile` object**:
   - **Original**:
      - Deprecated: `true`
      - Nullable parameter: Not included

   - **Updated**:
      - Removed the `deprecated` parameter
      - Added the `nullable` parameter as `true`

   - **Reasons**: The original configuration was generated successfully, but it caused a compile-time error. Updating the parameters resolved this error, enhancing the overall functionality and ensuring smooth compilation.


2. **Removed the `default:null` property from the below schemas**:

   - **Changed Schemas**: `CreateCompletionRequest`,`ChatCompletionStreamOptions`,`CreateChatCompletionRequest`

   - **Original**:
      - default: `null`

   - **Updated**:
      - Removed the `default` parameter 

   - **Reason**: This change is done as a workaround for ballerina openapi tool not allowing to generate the client.

## OpenAPI cli command

The following command was used to generate the Ballerina client from the OpenAPI specification. The command should be executed from the repository root directory.

```bash
bal openapi -i docs/spec/openapi.yaml --mode client --license docs/license.txt -o ballerina --tags 'Fine-tuning','Files','Models'
```
Note: The license year is hardcoded to 2024, change if necessary.
