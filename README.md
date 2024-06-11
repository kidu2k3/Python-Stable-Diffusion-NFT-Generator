<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Automatic 1111 NFT Script Guide</title>
  <style>
    body {
      font-family: sans-serif;
      line-height: 1.5;
      margin: 0;
      padding: 20px;
    }
    pre {
      overflow: auto; /* Enable horizontal scrolling if needed */
      white-space: pre-wrap; /* Wrap long lines within the pre tag */
      font-size: 0.8rem; /* Adjust font size for better fit */
    }
  </style>
</head>
<body>
  <h1>Automatic 1111 NFT Script Guide</h1>
  <p>This guide explains how to use a script for generating NFT images with Automatic 1111 WebUI.</p>

  <h2>Requirements</h2>
  <pre>
    pip install transformers
    pip install torch diffusers pillow
  </pre>

  <h3>Running Automatic 1111 WebUI</h3>
  <p>Ensure the WebUI is running on http://127.0.0.1:7860. Adjust the URL if necessary.</p>

  <h3>Model Setup</h3>
  <p>Make sure the "aziibpixelmix_fastModeExperimental.safetensors" model is loaded properly in the WebUI.</p>

  <h3>Running the Script</h3>
  <ol>
    <li>Save the script as <code>main.py</code>.</li>
    <li>Run the script in your terminal:</li>
    <pre>python main.py</pre>
  </ol>

  <h3>Entering Details</h3>
  <p>Follow the prompts to enter details about your NFT collection:</p>
  <ul>
    <li>Collection Description (e.g., NFT Collection)</li>
    <li>Base Prompt (e.g., in pixel art style, highly detailed, SciFy theme!)</li>
    <li>Number of NFTs to Generate (e.g., 10)</li>
  </ul>
</body>
</html>

![nft_3](https://github.com/kidu2k3/Python-Stable-Diffusion-NFT-Generator/assets/64930683/12d9e461-72bb-40c0-8ee7-5bad81611f03)
![nft_2](https://github.com/kidu2k3/Python-Stable-Diffusion-NFT-Generator/assets/64930683/0d9128de-ff3e-4dec-ab76-1e121b97e845)
![nft_1](https://github.com/kidu2k3/Python-Stable-Diffusion-NFT-Generator/assets/64930683/48d9df05-fc45-4598-a23a-f218cbbfbb58)

[nft_2.json](https://github.com/user-attachments/files/15780407/nft_2.json)
[nft_1.json](https://github.com/user-attachments/files/15780406/nft_1.json)
[nft_3.json](https://github.com/user-attachments/files/15780404/nft_3.json)
