# RAG Ansible Storage Protect

This Google Colab notebook demonstrates a Retrieval-Augmented Generation (RAG) approach to generate optimized Ansible playbooks. It leverages the contents of role-specific README files from an external Ansible repository and uses IBM WatsonX AI to produce a valid, complete YAML playbook based on a user-provided request.

## Overview

The notebook performs the following steps:
- **Install Dependencies:** Uses `pip` to install required packages such as `faiss-cpu`, `sentence-transformers`, `ansible`, and the IBM WatsonX AI client.
- **Clone Repository:** Clones the [IBM Ansible Storage Protect](https://github.com/IBM/ansible-storage-protect) repository, which contains a set of Ansible roles.
- **Extract Role Contents:** Traverses the repository’s `roles` directory to extract the content of each role’s `README.md`.
- **Build FAISS Index:** Encodes the extracted role information into embeddings using Sentence Transformers and builds a FAISS index to facilitate similarity search.
- **Generate Ansible Playbook:** Accepts a user prompt (e.g., “Create a playbook to install a client on remote VMs…”) and uses the WatsonX AI model to generate an optimized playbook that uses only the necessary roles.

## Prerequisites

- **Google Colab Account:** The notebook is designed to run on Google Colab.
- **IBM WatsonX AI Account:** You need valid credentials (API key and Project Id) for IBM WatsonX AI.
- **Internet Access:** The notebook clones an external GitHub repository and installs packages from PyPI.

## Setup and Usage

1. **Open the Notebook in Google Colab:**
   - Click on the [Google Colab link](https://colab.research.google.com/) and load the notebook file `RAG_Ansible_Storage_Protect.ipynb`.

2. **Install Required Packages:**
   - The first cell in the notebook installs all necessary dependencies. Make sure it runs successfully.

3. **Clone the Repository and Extract Roles:**
   - The notebook clones the IBM Ansible Storage Protect repository and extracts each role's README content to build a knowledge base.

4. **Build the FAISS Index:**
   - The notebook encodes the role contents and creates a FAISS index for similarity-based retrieval.

5. **Enter Your IBM WatsonX Credentials:**
   - When prompted, input your IBM WatsonX API key and Project Id.

6. **Provide a User Request:**
   - Modify the `user_input` variable (or use the default) to specify the playbook requirements.

7. **Generate the Playbook:**
   - Run the cell to generate the Ansible playbook. The output is printed directly in the notebook.

## Customization

- **User Request:** You can update the `user_input` string to tailor the playbook generation to your specific requirements.
- **Model Selection:** The notebook uses a model (e.g., `meta-llama/llama-3-1-70b-instruct`) for text generation. You may change this model based on your needs and availability.
- **Role Filtering:** The script extracts only the necessary roles by comparing the user prompt against the role README contents using a FAISS index.

## Troubleshooting

- **Dependency Issues:** Ensure that all dependencies install correctly in your Colab environment.
- **API Credentials:** Make sure your IBM WatsonX credentials are valid and that you have access to the specified model.
- **Repository Access:** The notebook automatically clones the repository. Verify that the repository URL is accessible and that your Colab environment has the necessary permissions.

## Contributing

Contributions are welcome! If you have suggestions or improvements, please open an issue or submit a pull request.

## Acknowledgments

- [IBM Ansible Storage Protect](https://github.com/IBM/ansible-storage-protect) for the role definitions.
- [IBM WatsonX AI](https://www.ibm.com/cloud/watsonx) for the model inference service.
- Open-source packages: FAISS, Sentence Transformers, and Ansible.

---
