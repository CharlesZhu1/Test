import openai

# Set your API key
openai.api_key = "your-api-key"

def generate_responses(prompts, model="gpt-4"):
    responses = []
    for prompt in prompts:
        response = openai.ChatCompletion.create(
            model=model,
            messages=[
                {"role": "system", "content": "You are a helpful assistant."},
                {"role": "user", "content": prompt}
            ]
        )
        responses.append(response['choices'][0]['message']['content'])
    return responses

# Example usage
prompts = [
    "Explain the importance of photosynthesis.",
    "What are the causes of climate change?",
    "Describe the impact of artificial intelligence on society."
]
responses = generate_responses(prompts)
print(responses)
