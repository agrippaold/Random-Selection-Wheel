# Random Selection Wheel - Technical Documentation

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Accessibility](https://img.shields.io/badge/WCAG-2.1%20AA-green.svg)](https://www.w3.org/WAI/WCAG21/quickref/)

## Overview

This repository documents the technical implementation and fairness principles behind cryptographically secure random selection wheels. The methodology ensures unbiased outcomes through the Web Crypto API.

## How It Works

### Cryptographic Randomness

Unlike `Math.random()` which uses a Pseudo-Random Number Generator (PRNG), this implementation leverages `crypto.getRandomValues()` for true cryptographic randomness:

```javascript
// Cryptographically secure random number generation
function getSecureRandom(max) {
  const array = new Uint32Array(1);
  crypto.getRandomValues(array);
  return array[0] % max;
}
```

### Why Cryptographic Randomness Matters

| Method | Type | Predictability | Use Case |
|--------|------|----------------|----------|
| `Math.random()` | PRNG | Theoretically predictable | Games, animations |
| `crypto.getRandomValues()` | CSPRNG | Unpredictable | Fair selection, giveaways |

## Fairness Principles

1. **Equal Probability**: Each entry has mathematically equal chances
2. **No Seed Manipulation**: Random seed cannot be influenced by users
3. **Transparent Process**: Selection logic is open and verifiable
4. **Weighted Options**: Support for custom probability distributions

## Use Cases

### Education
- Classroom random student selection
- Group assignment generators
- Quiz question randomizers

### Events & Giveaways
- Contest winner selection
- Prize wheel implementations
- Raffle systems

### Decision Making
- Meeting facilitator selection
- Task assignment
- Tie-breaking mechanisms

## Accessibility (WCAG 2.1 AA)

- Full keyboard navigation support
- Screen reader compatible with ARIA labels
- High contrast mode available
- Reduced motion preferences respected
- Touch-friendly for mobile devices

## Internationalization

Supports 21 languages with RTL (Right-to-Left) layout for Arabic:

`en` `es` `de` `fr` `it` `pt-BR` `ja` `ko` `zh-CN` `ru` `ar` `hi` `nl` `pl` `tr` `vi` `th` `sv` `cs` `el` `id`

## Live Implementation

A reference implementation demonstrating these principles is available at [wheel.expert](https://wheel.expert).

## Technical Specifications

- **Frontend**: React 18 with Hooks
- **Randomness**: Web Crypto API
- **Animation**: CSS transforms with GPU acceleration
- **Storage**: LocalStorage for offline capability
- **PWA**: Service Worker for offline functionality

## Contributing

Contributions focused on improving fairness algorithms or accessibility are welcome. Please read the contribution guidelines before submitting PRs.

## License

MIT License - See LICENSE file for details.

---

*This documentation is maintained for educational purposes regarding fair random selection methodologies.*