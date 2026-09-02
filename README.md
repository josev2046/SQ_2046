# SQ-2046 Analog Groovebox — Operating Manual

## Table of Contents

1. [Introduction](#1-introduction)
2. [Master Controls & Architecture](#2-master-controls--architecture)
3. [Synthesizer Tracks (A & B)](#3-synthesizer-tracks-a--b)
4. [Rhythm Generator](#4-rhythm-generator)
5. [Technical Specifications](#5-technical-specifications)
6. [Credits & Copyright](#credits--copyright)

---

## 1. Introduction

Welcome to the **SQ-2046 Analog Groovebox**, a comprehensive 16-step sequencing environment that fuses two independent monophonic synthesisers with a three-part analog-style drum machine.

Built entirely on the Web Audio API, the SQ-2046 delivers punchy, hardware-accurate sound shaped by a master brickwall compressor and a lush, tape-style delay. Whether you're generating squelchy acid basslines or programming driving techno rhythms, this groovebox offers an immediate, tactile workflow designed for modern widescreen and tablet displays.

---

## 2. Master Controls & Architecture

The top panel governs global playback, transposition, and spatial effects for the entire unit.

<img width="2280" height="400" alt="sq2046-master-controls" src="https://github.com/user-attachments/assets/034527e6-6b4b-4f4b-84b7-052d2a823b19" />

### 2.1 Routing & Keys

| Control | Options | Function |
| :--- | :--- | :--- |
| **Master Play Mode** | `FORWARD` · `REVERSE` · `PING-PONG` · `RANDOM` | Overrides the sequence direction for all three tracks globally. |
| **Keyboard** | 13-key (C to C) | Transposes the root note of Track A and Track B simultaneously. Tapping a key while stopped auditions the current Track A patch. |

### 2.2 Clock & Groove

| Control | Function |
| :--- | :--- |
| **BEND** | Shifts the global pitch of both synthesisers by up to ±2 semitones. Snaps back to `0` when released. |
| **BPM** | Sets the master tempo, from a sluggish 80 BPM to a blistering 180 BPM. |
| **SWING** | Introduces classic groovebox shuffle by progressively delaying the even 16th notes (steps 2, 4, 6, etc.). |

### 2.3 Delay FX

A global tape-style delay unit fed by the master bus.

| Control | Function |
| :--- | :--- |
| **TIME** | Synchronises delay repeats to the master clock: `1/4`, `1/8`, `1/8D` (dotted), or `1/16`. |
| **F.BACK** | Controls the number of delay repeats, from a single slapback to endless, saturated oscillation. |
| **MIX** | Blends the dry signal with the wet delay output. |

### 2.4 Transport

| Control | Function |
| :--- | :--- |
| **SYNC** | Instantly resets all tracks to step 1 (or step 16 if in reverse), keeping polyrhythms and sequence playheads perfectly aligned. |
| **PLAY / STOP** | Toggles the sequencer on and off. |

---

## 3. Synthesizer Tracks (A & B)

The SQ-2046 features two identical monophonic synth voices — **Track A** in red, **Track B** in blue. Each has its own 16-step matrix, track-specific playback mode, and sound-shaping parameters.

<img width="2640" height="800" alt="sq2046-synth-track" src="https://github.com/user-attachments/assets/431b22d4-b5a7-4520-9bd5-6e94c9056d59" />

### 3.1 Voice Parameters

| Control | Function |
| :--- | :--- |
| **WAVE** | Selects the oscillator shape: sawtooth, square, triangle, or sine. |
| **NOISE** | Injects white noise into the filter stage, for breathy, percussive, or aggressive tones. |
| **CUTOFF** | Sets the base low-pass filter frequency (50Hz–2,500Hz). |
| **DECAY** | Controls how quickly the filter and volume drop after a note triggers (0.05s–0.5s). |
| **ACCENT** | Determines the intensity of the volume and filter boost applied to accented steps. |
| **GLIDE** | Sets the portamento time between notes when a slide is active. |
| **OCTAVE** | Shifts the entire track up or down by two octaves. |

Each track also has its own **MUTE**, **RAND** (randomise), and per-track **play-mode** selector, independent of the global Master Play Mode.

### 3.2 The 16-Step Synth Grid

Each step in the synth tracks contains four interactive elements:

- **Pitch Display** — A draggable LED numerical readout. Tap and drag up or down to set the semitone value (0–24). Doing so instantly auditions the pitch.
- **S (Slide)** — Activating this toggles portamento, gliding the previous pitch into the current one without re-triggering the envelope.
- **A (Accent)** — Boosts the step's peak volume and filter cutoff, based on the track's `ACCENT` control.
- **Filter Slider** — A vertical fader that independently raises the cutoff frequency for that specific step, ideal for creating rhythmic motion and acid squelches.

---

## 4. Rhythm Generator

The drum module provides three synthesised percussive elements — Kick, Snare, and Hi-Hat — running on their own independent 16-step matrix.

<img width="2640" height="720" alt="sq2046-rhythm-generator" src="https://github.com/user-attachments/assets/72501610-8ab6-487e-a49f-7eee0f841d7c" />

### 4.1 Global Drum Parameters

| Control | Function |
| :--- | :--- |
| **N. DECAY** | Adjusts the decay time of the white noise element, determining the "tail" length of both the Snare and the Hi-Hats. |
| **K. TUNE** | Sets the fundamental pitch of the Kick drum oscillator (100Hz–250Hz). |

As with the synth tracks, the Rhythm Generator has its own **MUTE**, **RAND**, and play-mode selector, independent of the global Master Play Mode.

### 4.2 The 16-Step Drum Grid

- **BD (Bass Drum)** — A tactile pad that toggles the kick on or off for that step. Clicking instantly auditions the kick.
- **SD (Snare Drum)** — A tactile pad that toggles the noise-based snare. Clicking instantly auditions the snare.
- **Hat Slider** — A vertical fader controlling the volume of the high-pass filtered hi-hat on that step. Sliding above `0` instantly auditions the hat.

---

## 5. Technical Specifications

- **Sequencer Architecture:** 3 independent 16-step tracks (2 synth, 1 drum), each with independent play direction (Forward, Reverse, Ping-Pong, Random).
- **Audio Engine:** Web Audio API, with a master `DynamicsCompressorNode` (brickwall limiting) to prevent clipping during high-resonance filter sweeps.
- **Synthesizer Voices:** 4 selectable waveforms, independent filter envelopes, variable step-level cutoff offsets, step-level accent, and slide (TB-303-style portamento).
- **Rhythm Voices:** Sine-sweep kick drum, band-pass noise snare, high-pass noise hats.
- **Delay FX:** Tempo-synced ping-pong delay with a 2kHz low-pass dampening filter in the feedback loop.
- **Interface:** Hardware-locked 1,280px widescreen chassis, optimised for touch displays with Pointer Event draggable elements and overscroll protection.

---

## Credits & Copyright

**SQ-2046 Analog Groovebox**
Created & Developed by **Jose Velazquez MA**
Published by **Voltage & Wave**
Website: [voltageandwave.co.uk](https://voltageandwave.co.uk/)

Copyright © 2026 Jose Velazquez MA / Voltage & Wave. All rights reserved.
