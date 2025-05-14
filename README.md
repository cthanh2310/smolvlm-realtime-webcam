# SmolVLM real-time camera demo

![image](https://github.com/user-attachments/assets/1777d6e0-0a38-4f74-9afc-50242db8b59a)


This repository is a simple demo for how to use llama.cpp server with SmolVLM 500M to get real-time object detection

## How to setup

### ✅ Step 1: Install Required Dependencies

```bash
sudo apt update
sudo apt install -y build-essential cmake python3 python3-pip
```

---

### ✅ Step 2: Clone and Build `llama.cpp`

```bash
git clone https://github.com/ggml-org/llama.cpp.git
cd llama.cpp

# Create build directory and compile
mkdir build
cd build
cmake ..
cmake --build . --config Release
```

---

### ✅ Step 3: Run `llama-server` with GPU Acceleration

```bash
./build/bin/llama-server -hf ggml-org/SmolVLM-500M-Instruct-GGUF -ngl 99
```

> 📌 `-ngl 99` enables GPU acceleration (works if you have a supported NVIDIA/AMD/Intel GPU).

---

### ✅ Step 4: Access the Server

By default, the server is available at:

```
http://localhost:8080
```

---

### ✅ Step 5: Test the Server with a Prompt

Send a simple completion request using `curl`:

```bash
curl http://localhost:8080/completion \
  -d '{"prompt":"Tell me a joke.","n_predict":50}'
```

