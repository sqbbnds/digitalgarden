---
{"dg-publish":true,"permalink":"/论文/Oxford Gonzalez RF-review 2023/","created":"2024-03-04T15:17:51.139+08:00","updated":"2024-03-04T09:25:34.000+08:00"}
---

限制：本文只考虑微波信号的光子能量远小于量子系统的能级间隔，所以可以用半经典理论来描述（经典的电场与量子系统相互作用）。对于光子能量与量子能级间隔相比拟的情况，需要用全量子理论[^1]。
# 基本原理
## 三种类型的 RF 测量电路
测量量子器件的图。
我的理解使用了[[实验/锁相放大器\|锁相放大器]]原理：$V_\text{out}$ 是待测信号，$V_\text{LO}$ 是参考信号，从 $V_\text{IF}$ 可以读出参考信号 $V_\text{out}$ 的振幅（可以算出负载阻抗 $Z_\text{load}$，进而包含了待测器件的信息）。*为什么 $V_\text{LO}$ 在论文中也被称为解调信号？*
![Pasted image 20240202175559.png|400](/img/user/Attachment/Pasted%20image%2020240202175559.png)
### 反射型
传输线的终端看作是二端口网络，测量反射系数
![Pasted image 20240204120110.png](/img/user/Attachment/Pasted%20image%2020240204120110.png)
### 透射型
-传输线的终端看作是四端口网络，测量透射系数
![Pasted image 20240204115518.png](/img/user/Attachment/Pasted%20image%2020240204115518.png)
对于串联透射型，透射系数为
$$
T = \frac{2Z_{0}}{2Z_{0}+Z_\text{load}}
$$
对于并联透射型，透射系数为
$$
T = \frac{2Z_\text{load}}{2Z_\text{load}+Z_{0}}
$$
### 发射型 
待测器件被看作是电压源，所以不需要注入电路。

## 传输线理论
反射系数
$$
\Gamma_\text{L}(\omega)=\frac{Z_\text{L}(\omega)-Z_{0}}{Z_\text{L}(\omega)+Z_{0}}
$$
论文给出了下图
![Pasted image 20240204111243.png](/img/user/Attachment/Pasted%20image%2020240204111243.png)
实际上这是一个原点偏移到(-1,1)的反比例函数的绝对值
$$
|\Gamma _\text{L}(\omega)|=\left|\frac{\frac{Z_\text{L}(\omega)}{Z_{0}}-1}{\frac{Z_\text{L}(\omega)}{Z_{0}}+1}\right|=\left|\frac{x+1-2}{x+1}\right|=\left|1-\frac{2}{x+1}\right|
$$
![Pasted image 20240204111725.png|400](/img/user/Attachment/Pasted%20image%2020240204111725.png)
以上分析的重点是，如果 $|Z_\text{L}|\gg|Z_{0}|$，则反射系数趋于 1，而与 $Z_\text{L}$ 无关。这种情况广泛存在于量子器件的测量中，比如典型的 SET 器件 $Z_\text{L}\simeq \frac{h}{e^{2}}\simeq 25.8 \mathrm{k\Omega}$，而商业同轴线的标准特征阻抗 $Z_{0}=50\mathrm{\Omega}$
# 参考文献

[^1]: A. Blais, A. L. Grimsmo, S. M. Girvin, and A. Wallraff, “Circuit quantum electrodynamics,” Rev. Mod. Phys. 93, 025005 (2021).