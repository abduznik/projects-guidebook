---
{"dg-publish":true,"dg-path":"vhdl/state-machines.md","permalink":"/vhdl/state-machines/"}
---

# VHDL State Machines

This section covers the design and implementation of Finite State Machines (FSMs) in VHDL.

## 1. Overview

An FSM is a digital circuit that transitions between a finite number of states based on inputs and current state. Its output depends on both current input and past states.

### Key Concepts

*   **States:** Defined conditions or modes of operation.
*   **Transitions:** Movement between states, triggered by inputs or internal logic.
*   **Inputs:** Signals influencing state transitions and outputs.
*   **Outputs:** Signals or actions produced by the FSM.

### Types of FSMs

*   **Moore Machine:** Output is solely a function of the current state.
*   **Mealy Machine:** Output is a function of both the current state and current input.

## 2. VHDL Implementation

FSMs are typically implemented using a clocked process and a `case` statement.

### State Definition

States are defined using an enumerated type for clarity:

```vhdl
TYPE state_type IS (STATE_IDLE, STATE_A, STATE_B, STATE_DONE);
SIGNAL current_state, next_state : state_type;
```

### One-Process FSM Example

This style combines sequential (state register update) and combinational (next state and output determination) logic within a single clocked process.

```vhdl
LIBRARY ieee;
USE ieee.std_logic_1164.ALL;

ENTITY simple_fsm IS
    PORT (
        clk     : IN  STD_LOGIC;
        reset_n : IN  STD_LOGIC;
        start_i : IN  STD_LOGIC;
        done_o  : OUT STD_LOGIC
    );
END ENTITY simple_fsm;

ARCHITECTURE behavioral OF simple_fsm IS
    TYPE state_type IS (STATE_IDLE, STATE_S1, STATE_S2);
    SIGNAL current_state : state_type;
BEGIN
    PROCESS (clk, reset_n)
    BEGIN
        IF reset_n = '0' THEN
            current_state <= STATE_IDLE;
            done_o <= '0';
        ELSIF RISING_EDGE(clk) THEN
            done_o <= '0';
            CASE current_state IS
                WHEN STATE_IDLE =>
                    IF start_i = '1' THEN
                        current_state <= STATE_S1;
                    ELSE
                        current_state <= STATE_IDLE;
                    END IF;
                WHEN STATE_S1 =>
                    current_state <= STATE_S2;
                WHEN STATE_S2 =>
                    done_o <= '1';
                    current_state <= STATE_IDLE;
                WHEN OTHERS =>
                    current_state <= STATE_IDLE;
            END CASE;
        END IF;
    END PROCESS;
END ARCHITECTURE behavioral;
```

## Resources

*   [VHDLwhiz - Finite State Machines](https://vhdlwhiz.com/finite-state-machines/)
*   [All About Circuits - VHDL State Machine](https://www.allaboutcircuits.com/technical-articles/vhdl-state-machine-design-tutorial/)

## Video Tutorial

<iframe width="560" height="315" src="https://www.youtube.com/embed/your_vhdl_state_machine_video_id" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
