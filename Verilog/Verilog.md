# Verilog 速成  
**Verilog模块结构**
![alt text](./images/image.png)  
![alt text](./images/image-1.png)
![alt text](./images/image-2.png)
![alt text](./images/image-3.png)
![alt text](./images/image-4.png)
![alt text](./images/image-5.png)
![alt text](./images/image-6.png)
![alt text](./images/image-7.png)
![alt text](./images/image-8.png)
![alt text](./images/image-9.png)
![alt text](./images/image-10.png)
![alt text](./images/image-11.png)
![alt text](./images/image-12.png)
![alt text](./images/image-13.png)
![alt text](./images/image-14.png)
![alt text](./images/image-15.png)
![alt text](./images/image-16.png)
![alt text](./images/image-17.png)
![alt text](./images/image-18.png)
![alt text](./images/image-19.png)
![alt text](./images/image-20.png)
![alt text](./images/image-21.png)
![alt text](./images/image-22.png)
![alt text](./images/image-23.png)
![alt text](./images/image-24.png)
![alt text](./images/image-25.png)
![alt text](./images/image-26.png)
![alt text](./images/image-27.png)
![alt text](./images/image-28.png)
![alt text](./images/image-29.png)
![alt text](./images/image-31.png)
![alt text](./images/image-32.png)
![alt text](./images/image-33.png)
![alt text](./images/image-34.png)
![alt text](./images/image-35.png)
![alt text](./images/image-36.png)
![alt text](./images/image-37.png)
![alt text](./images/image-38.png)
![alt text](./images/image-39.png)
![alt text](./images/image-40.png)
![alt text](./images/image-41.png)
![alt text](./images/image-42.png)
![alt text](./images/image-43.png)
![alt text](./images/image-44.png)
![alt text](./images/image-45.png)
最多的方式：
![alt text](./images/image-46.png)
![alt text](./images/image-47.png)
![alt text](./images/image-48.png)


好的，根据您提供的图片（特别是包含**自学测试**问题的图片），我将详细解答其中的四个问题，这些问题是 Verilog 语言的核心基础。

### 自学测试问题解答

#### 1\. 说明 `assign` 语句和 `always` 语句的特点。

| 语句 | `assign` (连续赋值) | `always` (过程块) |
| :--- | :--- | :--- |
| **电路类型** | **组合逻辑 (Combinational Logic)** | **组合逻辑 或 时序逻辑** |
| **执行机制** | **并行执行 (Concurrent)**。只要右侧 (RHS) 表达式的操作数发生变化，左侧 (LHS) 就会**立即**更新。 | **过程化执行 (Procedural)**。仅当敏感列表中的事件发生时，块内的语句才顺序执行一次。 |
| **应用场景** | 描述简单的组合逻辑，如连线、简单的逻辑门、多路选择器、基本的算术运算等。 | 描述复杂的组合逻辑（需使用 `always @(*)`），以及所有时序逻辑（如寄存器、计数器、状态机）。 |
| **赋值符号** | 只能使用 **`=`** (连续赋值操作符)。 | 块内可使用 **阻塞赋值 (`=`)** 或 **非阻塞赋值 (`<=`)**。 |
| **左值类型** | 只能对 **`wire`** 类型的信号赋值。 | 只能对 **`reg`** 或 **`logic`** 类型的信号赋值。 |

-----

#### 2\. 说明阻塞赋值和非阻塞赋值的特点。

| 特点 | 阻塞赋值 (`=`) | 非阻塞赋值 (`<=`) |
| :--- | :--- | :--- |
| **执行特性** | **顺序执行**。当前语句执行完成后，才执行下一条语句。它会“阻塞”同一过程块中后续语句的执行。 | **并行执行**。所有非阻塞赋值语句都在当前过程块**执行结束时**同时更新 LHS 的值。不会阻塞同一过程块中后续语句的执行。 |
| **赋值过程** | **立即更新** LHS 的值。 | LHS 的值在当前时钟周期（或过程块执行）**结束时才更新**。 |
| **应用场景** | **仅用于描述纯组合逻辑**（在 `always @(*)` 中）。或用于描述顺序软件行为（在 Testbench 中）。 | **严格用于描述时序逻辑**（在 `always @(posedge clk or ...)` 中），如寄存器、触发器和状态机。 |
| **硬件映射** | 映射为**组合逻辑**。 | 映射为**带有时钟控制的存储元件**（触发器/寄存器）。 |

-----

#### 3\. 说明 `wire` 和 `reg` 数据类型的特点。

| 特点 | `wire` (连线) | `reg` (寄存器) |
| :--- | :--- | :--- |
| **硬件映射** | 映射为**物理连线**或**组合逻辑输出**。 | 映射为**存储元件**（如触发器、寄存器）或过程赋值的**变量**。 |
| **存储功能** | **无存储能力**。它的值由驱动它的元件（`assign` 或另一个模块的输出）持续决定。 | **有存储能力**。在时序块中，它会保持上一个时钟周期或过程赋值的值，直到被新的赋值语句更新。 |
| **赋值来源** | 只能由 **`assign` 语句** 或**模块实例化**的输出端口驱动。 | 只能在 **`always` 块**、`initial` 块等**过程块**中赋值。 |
| **端口方向** | 可用于 `input`, `output`, `inout` 端口。 | 只能用于 `output` 端口（作为过程赋值的结果）或作为模块内部信号。 |

-----

#### 4\. 分别用 `assign` 语句和 `always` 语句设计四选一数据选择器。

假设输入信号为：

  * 选择信号：`sel [1:0]`
  * 数据输入：`d0, d1, d2, d3`
  * 输出信号：`y`

##### 方案一：使用 `assign` 语句（组合逻辑，推荐）

使用三目运算符 (`? :`) 实现，这是描述多路选择器最简洁的 RTL 方式。

```verilog
module mux4_1_assign (
    output wire y,
    input wire [1:0] sel,
    input wire d0, d1, d2, d3
);

    // 使用嵌套的三目运算符实现四选一选择逻辑
    assign y = (sel == 2'b00) ? d0 : 
               (sel == 2'b01) ? d1 : 
               (sel == 2'b10) ? d2 : 
               d3; // 默认 sel == 2'b11

endmodule
```

##### 方案二：使用 `always @(*)` 语句（组合逻辑，适用于复杂逻辑）

使用 `case` 语句实现，结构清晰，易于扩展。

```verilog
module mux4_1_always (
    output reg y, // 在 always 块中赋值，因此 y 必须是 reg 类型
    input wire [1:0] sel,
    input wire d0, d1, d2, d3
);

    // 敏感列表中的 '*' 确保任何输入变化时都重新计算，实现组合逻辑
    always @(*) begin
        // 使用阻塞赋值 '=' 描述组合逻辑
        case (sel)
            2'b00: y = d0;
            2'b01: y = d1;
            2'b10: y = d2;
            2'b11: y = d3;
            // 必须包含 default 或覆盖所有 sel 取值，否则可能生成不期望的锁存器(Latch)
            default: y = 1'b0; 
        endcase
    end

endmodule
```


**verilog 定义数组语法**
索引允许递增与递减：
* DataType [DataTop :DataBottom] ArraryName [ArrayBottom:ArrayTop];
* DataType [DataTop :DataBottom] ArraryName [ArrayTop:ArrayBottom];
