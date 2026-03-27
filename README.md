# Sandbox Tool Exec

![security](https://img.shields.io/badge/security-blue?style=flat-square) ![sandbox](https://img.shields.io/badge/sandbox-blue?style=flat-square) ![tool-use](https://img.shields.io/badge/tool--use-blue?style=flat-square)

A secure Docker-based environment for agents to execute arbitrary generated code safely.

## Overview
Sandbox Tool Exec provides a robust execution layer designed specifically for LLM agents that need to run untrusted, generated code. By leveraging Docker containers, the tool ensures that code execution is isolated from the host system, mitigating risks associated with arbitrary scripts. This project simplifies the "tool-use" loop by providing a clean API for spinning up, executing, and tearing down ephemeral environments.

## Features
*   **Docker Isolation:** Executes all code within ephemeral containers to ensure host system integrity.
*   **Multi-Language Support:** Pre-configured environments for Python and other common runtimes.
*   **Resource Constraints:** Ability to limit CPU and Memory usage to prevent denial-of-service via infinite loops.
*   **Automatic Cleanup:** Automatically removes containers and temporary volumes after execution is complete.

## Installation
Ensure you have [Docker](https://www.docker.com/) installed and running on your system. Then, clone the repository and install the dependencies:

```bash
git clone https://github.com/yourusername/sandbox-tool-exec.git
cd sandbox-tool-exec
pip install -r requirements.txt
```

## Usage
You can run the sandbox directly via the CLI to execute Python scripts.

```bash
python main.py --code "print('Hello from the sandbox!')"
```

To use it within your agentic workflow:

```python
from sandbox import SandboxExecutor

executor = SandboxExecutor()
result = executor.run(code="import math; print(math.sqrt(16))")
print(result.output) # Output: 4.0
```

## Contributing
Contributions are welcome! Please feel free to submit a Pull Request. For major changes, please open an issue first to discuss what you would like to change. Ensure that your code adheres to the existing style and includes passing tests.

## License
This project is licensed under the [MIT License](LICENSE).