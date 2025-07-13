---
{"dg-publish":true,"dg-path":"vhdl/loops.md","permalink":"/vhdl/loops/"}
---

# VHDL Loops

This section describes various loop constructs in VHDL, differentiating between simulation-only and synthesizable applications.

## 1. For Loop

Executes a block of code a fixed number of times. Applicable in both testbenches and synthesizable designs.

**Syntax:**
```vhdl
[loop_label :] for parameter in range loop
    -- Code block
end loop [loop_label];
```
*   `loop_label` (optional): Loop identifier.
*   `parameter`: Implicitly declared constant representing the current iteration value. Non-modifiable within the loop.
*   `range`: Specifies iteration count (e.g., `0 to 7`, `7 downto 0`).

**Example:**
```vhdl
process (all)
begin
    for i in 0 to 7 loop
        my_signal(i) <= some_other_signal(i);
    end loop;
end process;
```

**Synthesizability:**
Synthesizable. Used for unrolling replicated logic into multiple hardware instances. The loop range must be static (compile-time known).

## 2. While Loop

Executes a code block as long as a specified condition remains true. Condition evaluated prior to each iteration.

**Syntax:**
```vhdl
[loop_label :] while condition loop
    -- Code block
end loop [loop_label];
```
*   `loop_label` (optional): Loop identifier.
*   `condition`: Boolean expression controlling loop continuation.

**Example:**
```vhdl
process
    variable counter : integer := 0;
begin
    while counter < 10 loop
        report "Counter: " & integer'image(counter);
        counter := counter + 1;
        wait for 10 ns;
    end loop;
    wait;
end process;
```

**Synthesizability:**
Generally **not synthesizable**. Primarily used in testbenches for stimulus generation or behavioral simulation models due to dynamic execution count.

## 3. Simple Loop (Infinite Loop)

An unconditional `loop` statement creates an infinite loop, executing continuously.

**Syntax:**
```vhdl
[loop_label :] loop
    -- Code block
end loop [loop_label];
```

**Exiting:**
Utilize the `exit` statement, often with a `when` condition, to terminate an infinite loop.

**Example:**
```vhdl
process
    variable done : boolean := false;
begin
    loop
        report "Running...";
        wait for 5 ns;
        if some_condition = true then
            exit;
        end if;
    end loop;
    report "Loop exited.";
    wait;
end process;
```

**Synthesizability:**
Generally **not synthesizable**. Primarily used in testbenches.

## 4. Generate Statement

A concurrent construct for iterative or conditional instantiation of hardware blocks. Distinct from sequential loops.

**Syntax (For Generate):**
```vhdl
[generate_name :] for variable in range generate
    -- Concurrent statements
end generate [generate_name];
```
*   `generate_name`: Mandatory label.
*   `variable`: Implicitly declared constant for iteration.
*   `range`: Specifies generation count.

**Syntax (If Generate):**
```vhdl
[generate_name :] if condition generate
    -- Concurrent statements
end generate [generate_name];
```

**Example (For Generate):**
```vhdl
architecture Behavioral of my_entity is
    component AND_GATE
        port (A, B : in std_logic;
              Y    : out std_logic);
    end component;
    signal and_outputs : std_logic_vector(3 downto 0);
begin
    G_AND_GATES: for i in 0 to 3 generate
        AND_INST: AND_GATE
            port map (A => input_a(i),
                      B => input_b(i),
                      Y => and_outputs(i));
    end generate G_AND_GATES;
end architecture Behavioral;
```

**Synthesizability:**
Fully synthesizable. Evaluated at compile time, physically replicating hardware blocks.

**Distinction from `for` loop:**
*   **Context:** `for` loops are sequential (within processes/subprograms); `generate` statements are concurrent (within architecture body).
*   **Execution:** `for` loops execute sequentially during simulation; `generate` statements create concurrent hardware instances during synthesis.

## Resources

*   [VHDLwhiz - VHDL Loops](https://vhdlwhiz.com/vhdl-loops/)
*   [FPGA Tutorial - VHDL Loops](https://fpgatutorial.com/vhdl-loops/)

## Video Tutorial

<iframe width="560" height="315" src="https://www.youtube.com/embed/your_vhdl_loops_video_id" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
