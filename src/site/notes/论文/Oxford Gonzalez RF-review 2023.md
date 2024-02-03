---
{"dg-publish":true,"permalink":"/论文/Oxford Gonzalez RF-review 2023/"}
---

限制：本文只考虑微波信号的光子能量远小于量子系统的能级间隔，所以可以用半经典理论来描述（经典的电场与量子系统相互作用）。对于光子能量与量子能级间隔相比拟的情况，需要用全量子理论[^1]。
# 基本原理
## 三种类型的RF测量电路
- 反射型
- 透射型
- 发射型：待测器件被看作是电压源，所以不需要注入电路。
![Pasted image 20240202175559.png|400](/img/user/Attachment/Pasted%20image%2020240202175559.png)
我的理解：上图使用了[[实验/锁相放大器\|锁相放大器]]原理：$V_\text{out}$是待测信号，$V_\text{LO}$是参考信号，从$V_\text{IF}$可以读出参考信号$V_\text{out}$的振幅（可以算出负载阻抗$Z_\text{load}$，进而包含了待测器件的信息）。*为什么$V_\text{LO}$在论文中也被称为解调信号？*

# 参考文献

[^1]: A. Blais, A. L. Grimsmo, S. M. Girvin, and A. Wallraff, “Circuit quantum electrodynamics,” Rev. Mod. Phys. 93, 025005 (2021).