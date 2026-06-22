# BrakeLedBlinker

`BrakeLedBlinker` is included in the motorcycle electronics superproject as a future or recovered brake-light controller project.

## Current Status

The repository currently contains only `.gitattributes`. There is no sketch, schematic, pin assignment, or protocol implementation to build or test yet.

The project name suggests that it was intended to control a brake LED blinking pattern, but that is only an inference from the name. The behavior must not be reconstructed from guesswork because brake lighting is safety-critical and legally regulated.

## Information Needed

Before firmware is added, document:

- The motorcycle model and applicable brake-light regulations
- Whether the controller drives an existing lamp, an added lamp, or a relay/MOSFET stage
- Input source: mechanical switch, existing 12 V brake circuit, or an RS-485 command
- Required steady and blinking behavior
- Maximum blink duration and conditions that force a steady brake light
- Lamp voltage, current, and inrush characteristics
- Selected microcontroller and supply voltage
- Automotive input protection and output-driver schematic
- Whether loss of controller power must leave the normal brake light operational
- Whether this node will join the shared RS-485 bus

## Safety Direction

A future design should fail toward a normal steady brake light. The microcontroller should not be the only current path between the original brake switch and mandatory lighting unless the hardware provides a safe bypass state.

The output stage will need protection appropriate for a motorcycle electrical system, including reverse polarity, transients, ESD, inductive loads when applicable, and thermal/current limits.

## Superproject Role

This repository remains a separate submodule so its eventual firmware, hardware revision, and legal/safety decisions have an independent history. It should use `MotorcycleProtocol` only if a real bus-connected use case is confirmed.

There is currently no build command or automated test suite.
