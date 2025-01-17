# Alternative Model Providers


## Usage

GPTScript can be used against alternative models that expose an OpenAI compatible API or have a provider shim available.

To use a model with an OpenAI compatible API:

```gptscript
model: mistral-large-latest from https://api.mistral.ai/v1

Say hello world
```

To use a model that requires a provider shim:

```gptscript
model: claude-3-haiku-20240307 from github.com/gptscript-ai/anthropic-provider

Say hello world
```

### Authentication

For OpenAI compatible providers, GPTScript will look for an API key to be configured with the prefix `GPTSCRIPT_PROVIDER_`, the base domain converted to environment variable format, and a suffix of `_API_KEY`.
As an example if you are using `mistral-large-latest from https://api.mistral.ai/v1`, the environment variable would be `GPTSCRIPT_PROVIDER_API_MISTRAL_AI_API_KEY`

Each provider shim has different requirements for authentication. Please check the readme for the provider you are trying to use.

## Available Model Providers

The following shims are currently available:
* [github.com/gptscript-ai/azure-openai-provider](https://github.com/gptscript-ai/azure-openai-provider)
* [github.com/gptscript-ai/azure-other-provider](https://github.com/gptscript-ai/azure-other-provider)
* [github.com/gptscript-ai/anthropic-provider](https://github.com/gptscript-ai/anthropic-provider)
* [github.com/gptscript-ai/gemini-aistudio-provider](https://github.com/gptscript-ai/gemini-aistudio-provider)
* [github.com/gptscript-ai/gemini-vertexai-provider](https://github.com/gptscript-ai/gemini-vertexai-provider)

## Listing available models

For any provider that supports listing models, you can use this command:

```bash
# With a shim
gptscript --list-models github.com/gptscript-ai/anthropic-provider

# To OpenAI compatible endpoint
gptscript --list-models https://api.mistral.ai/v1
```


## Compatibility

While the shims provide support for using GPTScript with other models, the effectiveness of using a
different model will depend on a combination of prompt engineering and the quality of the model. You may need to change
wording or add more description if you are not getting the results you want. In some cases, the model might not be
capable of intelligently handling the complex function calls.
