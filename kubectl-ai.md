# 🤖 kubectl-ai with Gemini, Ollama, and Local LLMs — On a kind Cluster

This repository documents my hands-on experience using [`kubectl-ai`](https://github.com/sozercan/kubectl-ai)—an AI-powered CLI assistant for Kubernetes—on a local `kind` (Kubernetes in Docker) cluster. I used **Gemini** via the official API, and also explored its support for other models including **local LLMs via Ollama**.

---

## ✨ What is `kubectl-ai`?

`kubectl-ai` is a CLI plugin that allows you to interact with your Kubernetes cluster using natural language. It uses large language models (LLMs) under the hood to convert prompts like *"create a namespace and deploy Argo CD"* into actual `kubectl` commands.

---

## ⚙️ Installation Guide

### 🔧 Step 1: Install `kubectl-ai`

Download the latest release from the ![releases page](https://github.com/GoogleCloudPlatform/kubectl-ai/releases/tag/v0.0.10) for your target machine.

Untar the release, make the binary executable and move it to a directory in your $PATH (as shown below).

    tar -zxvf kubectl-ai_Darwin_arm64.tar.gz
    chmod a+x kubectl-ai
    sudo mv kubectl-ai /usr/local/bin/

### Step 2: Choose Your Backend (Model Support)

kubectl-ai supports the following backends:

    🔹 OpenAI (e.g. GPT-3.5 / GPT-4)

    🔹 Anthropic (Claude)

    🔹 Gemini (Google's LLM)

    🔹 Ollama (for local models like LLaMA, Mistral, etc.)

    🔹 LM Studio, LocalAI, and other local runners

✅ Gemini Setup Example

    export GEMINI_API_KEY=your_api_key_here

✅ Ollama Setup (Local Models)

Install Ollama

Run a model:

    ollama run mistral

Configure kubectl-ai:

    export KUBECTL_AI_BACKEND=ollama
    export KUBECTL_AI_OLLAMA_MODEL=mistral

### Step 3: Create a Kubernetes Cluster with kind

Install kind:

    brew install kind

Create your local cluster:

    kind create cluster

### Interacting with the Cluster using kubectl-ai

Once setup is complete, you can start issuing natural language commands:

    kubectl ai

### Example Commands I Tried

Create a namespace called argocd and install Argo CD in it.

✅ It created the namespace and applied Argo CD manifests.

Expose the Argo CD server service using NodePort.

✅ It exposed the service with a NodePort.

Give me the URL to access the Argo CD dashboard.

✅ It returned a working URL, which I opened in my browser to access the Argo CD UI.

### Key Features I Explored

  🧠 Used Gemini (via API) for natural language prompts

  🧪 Tested kind as a lightweight, local Kubernetes environment

  🌍 Exposed services and accessed Argo CD via NodePort

  💻 Confirmed support for Ollama and local models

  🛠️ Model-agnostic design: Switch backends with simple environment variables

📸 Bonus: Try These Yourself

  kubectl ai
  > Deploy a sample nginx app in the default namespace
    
  kubectl ai
  > Scale the nginx deployment to 3 replicas
    
  kubectl ai
  > Delete the argocd namespace

📚 Resources

  kubectl-ai GitHub

  Google Gemini API Docs

  Ollama (Local LLMs)

  kind (Kubernetes in Docker)

  Argo CD

### ✅ Conclusion

kubectl-ai brings the power of LLMs into Kubernetes management. Whether you're using cloud-hosted models like Gemini or running local LLMs with Ollama, this tool adds incredible productivity and accessibility to DevOps workflows.

I was amazed at how effortlessly I could manage namespaces, deployments, and services—all through simple natural language.
