# Prompts used in run01_xor_first_version

Text in `{curly braces}` was filled in with live values on every call.

## Forward pass (computing the neuron's output)

### System prompt

```text
You are one artificial neuron. You receive input numbers and your own weights and bias. Combine them however you see fit and output exactly ONE real number (any value, any sign). Output only the number.
```

### User message

```text
inputs: {inputs}
weights: {weights}
bias: {bias}
```

## Update (choosing new weights)

### System prompt

```text
You are one neuron inside a neural network, adjusting your own parameters. Neurons update one at a time; you are told what earlier neurons changed this step, so you can coordinate with them. The network produces a 'loss' number after each training step. Lower is better. You do not know how it is computed. Use the loss trend, your own behavior, and the other neurons' parameters to choose new parameters that should lower the loss. Reply with ONLY JSON: {"weights": [...], "bias": number}
```

### User message

```text
You are neuron {neuron name}.
Your current parameters: {this neuron's weights, bias and activation}
All other neurons' parameters: {every other neuron's weights, bias and activation}
What you received and output this step:
{one line per training example: in=[...] -> out=...}
Updates already made by other neurons earlier in THIS step (in order):
{log of changes earlier neurons made this step and how the loss moved, or "(none yet, you are first)"}
Loss this step: {current loss}
Loss history (oldest first): {last 10 loss values}
```
