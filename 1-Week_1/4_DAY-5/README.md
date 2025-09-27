# 🌟 DAY 5: IF / CASE Constructs & Looping in Verilog

This session focuses on **decision-making constructs (IF / CASE)** and **looping constructs (FOR / Generate)** in Verilog.
It also covers **common pitfalls** (like inferred latches) and demonstrates them through labs.

---

## 🧩 1. IF and CASE Constructs

### 🔹 IF Statement

✅ **Usage**: Inside `always` block
✅ **Purpose**: Implements **priority logic**
⚠️ **Caution**:

* Incomplete IF → **inferred latch** (bad coding style).
* Always close with `else`.

```verilog
// BAD: Incomplete IF (latch inferred)
always @(a or b) begin
  if (a)
    y = b;   // What if a = 0? y holds its value -> latch
end

// GOOD: Complete IF
always @(a or b) begin
  if (a)
    y = b;
  else
    y = 0;
end
```

---

### 🔹 CASE Statement

✅ **Usage**: Inside `always` block
✅ **Purpose**: Implements **parallel logic** (mutually exclusive)

⚠️ **Caveats**:

1. Incomplete CASE → inferred latch (fix: add `default`)
2. Partial assignments → unintended storage
3. Overlapping cases → ambiguity

```verilog
// BAD: Missing default
always @(sel or a or b) begin
  case(sel)
    2'b00: y = a;
    2'b01: y = b;
    // sel=10 or 11? -> latch
  endcase
end

// GOOD: With default
always @(sel or a or b) begin
  case(sel)
    2'b00: y = a;
    2'b01: y = b;
    default: y = 0;
  endcase
end
```

---

### ⚖️ IF vs CASE

| Feature          | IF             | CASE              |
| ---------------- | -------------- | ----------------- |
| Priority?        | ✅ Yes          | ❌ No              |
| Usage            | Priority logic | Parallel logic    |
| Overlap allowed? | Yes            | No (bad practice) |

👉 Use **IF** when priority matters.
👉 Use **CASE** when conditions are mutually exclusive.

---

## 🧪 2. Labs on IF

* `D5SK2 L1` → Incomplete IF (part 1)
* `D5SK2 L2` → Incomplete IF (part 2)
  🔍 **Focus**: Inferred latches due to missing else conditions.

---

## 🧪 3. Labs on CASE

* `D5SK3 L1` → Incomplete/Overlapping CASE (part 1)
* `D5SK3 L2` → Incomplete/Overlapping CASE (part 2)
* `D5SK3 L3` → Incomplete/Overlapping CASE (part 3)
* `D5SK3 L4` → Incomplete/Overlapping CASE (part 4)

🔍 **Focus**: Missing defaults & overlapping conditions → simulation vs synthesis mismatch.

---

## 🔄 4. Looping Constructs

### 🔹 FOR Loop

* Inside `always` block
* Used for evaluating expressions / repetitive assignments

```verilog
// FOR loop inside always
always @(posedge clk) begin
  for (i = 0; i < 8; i = i + 1)
    sum[i] = a[i] & b[i];
end
```

---

### 🔹 Generate Loop

* **Outside** `always` block
* Used for **instantiating hardware**

```verilog
// Generate loop for multiple instantiations
genvar j;
generate
  for (j = 0; j < 4; j = j + 1) begin : GEN_BLOCK
    DFF dff_inst (.clk(clk), .d(data[j]), .q(q[j]));
  end
endgenerate
```

---


---

## 📌 Key Takeaways

✨ Always complete IF/CASE to avoid **latches** <br/>
✨ Add `default` in CASE <br/>
✨ Avoid overlapping CASE branches <br/>
✨ IF → **priority**, CASE → **parallel** <br/>
✨ FOR → inside `always` (behavioral) <br/>
✨ Generate → outside `always` (structural) <br/>

---

