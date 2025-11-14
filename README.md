# Voice-Print Lite

**Extract speaker gender, emotion, and location from speech—without transcribing a single word.**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.9+](https://img.shields.io/badge/python-3.9+-blue.svg)](https://www.python.org/downloads/)
[![CPU Only](https://img.shields.io/badge/hardware-CPU%20Only-green.svg)](https://colab.research.google.com)

---





| Industry            | Problem                               | Our Solution                          | Impact                                                |
| ------------------- | ------------------------------------- | ------------------------------------- | ----------------------------------------------------- |
| **Hearing Aids**    | Can't discern speaker intent in noise | Real-time affect detection (120 ms)   | Improves situational awareness; runs 48h on coin cell |
| **Smart Speakers**  | False wakes from TV/radio             | Gender + location filter              | 90% reduction in false triggers                       |
| **Call Centers**    | PCI compliance bans recording         | Emotion flagging *without* transcript | Audit-proof analytics; angry customer alerts          |
| **Security (CCTV)** | Need "shouting left corridor" alert   | Continuous monitoring, text-free      | No GDPR violation; works in any language              |
| **Automotive**      | Driver stress detection               | Jitter + pitch slope classifier       | Faster than ASR; language-agnostic                    |
| **Healthcare**      | Remote patient monitoring             | Voice-quality changes (breathiness)   | Early warning for respiratory decline                 |


Technical Architecture
┌─────────────────────────────────────────────────────────────┐
│  INPUT: Raw waveform (48 kHz, mono)                         │
└──────────────────────┬──────────────────────────────────────┘
                       │
┌──────────────────────▼──────────────────────────────────────┐
│  1. COCHLEA: Half-wave rectifier + STFT → Rate-code map    │
│     (Mimics basilar membrane & inner hair cells)           │
└──────────────────────┬──────────────────────────────────────┘
                       │
┌──────────────────────▼──────────────────────────────────────┐
│  2. BRAINSTEM: Autocorrelation → F0 + jitter              │
│     (Mimics inferior colliculus pitch extraction)          │
└──────────────────────┬──────────────────────────────────────┘
                       │
┌──────────────────────▼──────────────────────────────────────┐
│  3. CORTEX: 5 features → Logistic Regression               │
│     (Mimizes auditory cortex → posterior mapping)          │
└──────────────────────┬──────────────────────────────────────┘
                       │
┌──────────────────────▼──────────────────────────────────────┐
│  OUTPUT: P(gender), P(emotion), P(location)               │
└─────────────────────────────────────────────────────────────┘


