# Building_Systems_with_ChatGPT_API-
Building a ChatGpt system with open ai

For Documentation check the official pafe - https://platform.openai.com/docs/api-reference/making-requests

### How to get OpenAI Api_key
The OpenAI API uses API keys for authentication. You can create API keys at a user or service account level. Service accounts are tied to a "bot" individual and should be used to provision access for production systems. Each API key can be scoped to one of the following,

Project keys - Provides access to a single project (preferred option); access Project API keys by selecting the specific project you wish to generate keys against.
User keys - Our legacy keys. Provides access to all organizations and all projects that user has been added to; access API Keys to view your available keys. We highly advise transitioning to project keys for best security practices, although access via this method is currently still supported.
Remember that your API key is a secret! Do not share it with others or expose it in any client-side code (browsers, apps). Production requests must be routed through your own backend server where your API key can be securely loaded from an environment variable or key management service.

### Code for open ai
import os
import openai
import tiktoken
from dotenv import load_dotenv, find_dotenv
_ = load_dotenv(find_dotenv()) # read local .env file

openai.api_key  = os.environ['OPENAI_API_KEY']

def get_completion(prompt, model="gpt-3.5-turbo"):
    messages = [{"role": "user", "content": prompt}]
    response = openai.ChatCompletion.create(
        model=model,
        messages=messages,
        temperature=0, # this is the degree of randomness of the model's output 
    )
    return response.choices[0].message["content"]

response = get_completion("What is the capital of France?")

print(response)


