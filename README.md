import os
import random
import json
import requests
from PIL import Image
from io import BytesIO
import base64

# Function to generate a single NFT
def generate_nft(nft_id, base_description, base_prompt):
    metadata = {}
    description = base_description

    for trait, options in traits.items():
        selected_trait = random.choice(options)
        metadata[trait] = selected_trait
        description += f"{selected_trait}, "

    # Create prompt for Stable Diffusion
    prompt = f"{base_prompt}, {description.strip(', ')} in pixel art style, highly detailed, cyberpunk theme, full body, monkey"

    # Prepare the payload for the API request
    payload = {
        "prompt": prompt,
        "steps": 50,
        "cfg_scale": 7.5,
        "width": 512,
        "height": 512,
        "sampler_name": "Euler a",  # Choose the appropriate sampler
        "seed": random.randint(0, 2**32 - 1),  # Use a random seed for each image
        "negative_prompt": "",
        "batch_size": 1,
        "n_iter": 1,
        "save_images": False,
        "model": "aziibpixelmix_fastModeExperimental.safetensors"  # Ensure this model is loaded in the WebUI
    }

    # Make the API request to generate the image
    response = requests.post(api_url, json=payload)
    response.raise_for_status()
    response_data = response.json()

    # Get the generated image from the response
    image_data = response_data["images"][0]
    image = Image.open(BytesIO(base64.b64decode(image_data)))

    # Save the image and metadata
    image.save(os.path.join(output_path, f'nft_{nft_id}.png'))
    with open(os.path.join(metadata_path, f'nft_{nft_id}.json'), 'w') as meta_file:
        json.dump(metadata, meta_file, indent=4)

# Main script
if __name__ == "__main__":
    # Ask for user input
    collection_description = input("Enter the description for the collection: ")
    base_prompt = input("Enter the base prompt for Stable Diffusion: ")
    num_nfts = int(input("Enter the number of NFTs you want to generate: "))

    # Define paths
    output_path = 'output_nfts'
    metadata_path = 'metadata'

    # Create directories if they don't exist
    os.makedirs(output_path, exist_ok=True)
    os.makedirs(metadata_path, exist_ok=True)

    # Define traits and variations
    traits = {
        'backgrounds': ['cyberpunk city', 'neon grid', 'futuristic skyline'],
        'bodies': ['cyborg body', 'mechanical body', 'android body'],
        'eyes': ['laser eyes', 'robotic eyes', 'holographic eyes'],
        'arms': ['metal arms', 'bionic arms', 'hydraulic arms'],
        'accessories': ['visor', 'helmet', 'gadget'],
        'armors': ['titanium armor', 'carbon fiber armor', 'kevlar armor'],
        'armor_colors': ['red', 'blue', 'green', 'yellow', 'black', 'white']
    }

    # Stable Diffusion API endpoint
    api_url = "http://127.0.0.1:7860/sdapi/v1/txt2img"

    # Generate the collection
    for nft_id in range(1, num_nfts + 1):
        generate_nft(nft_id, collection_description, base_prompt)
