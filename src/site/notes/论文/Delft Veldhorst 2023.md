---
{"dg-publish":true,"permalink":"/论文/Delft Veldhorst 2023/","created":"2024-01-29T17:47:18.644+08:00","updated":"2024-02-03T19:52:08.000+08:00"}
---

#量子点 #Si/SiGe #栅调控
来源：Web of science检索
结构：$^{28}$Si/SiGe异质结

# 背景介绍
## 电势非均匀问题
理想的gate电压应该是均匀的（下图b），实际的确实非均匀的（下图c）。这是defects, charge traps, mechanical stress by the deposition of metallic gates引起的电势涨落。
![结构图.png](/img/user/Attachment/%E7%BB%93%E6%9E%84%E5%9B%BE.png)
导致potential landscape非均匀的原因：
1. 缺陷 defects
2. charge traps
3. 金属栅沉淀导致的机械应力 mechanical stress by the deposition of metallic gates [^1] [^2]
4. 材料生长 variations in material growth
5. 栅极的形状差异 the exact shape of the gates
## 滞回现象
半导体势垒和电介质界面上的电荷积累，改变了量子点的电场分布，从而导致滞回现象[^3] [^4]本文将要揭示滞回线性的本质，并利用其来稳定pinch-off电压数个小时。。

---
# 实验参数
source-dain电压：100 μV
pinch-off电压$V_\mathrm{thres}$：定义为源漏电流达到50 pA时的栅极电压。
结构：$^{28}$Si/SiGe异质结 或 Ge/SiGe异质结
环境温度：4.2 K
[[电子温度\|电子温度]]：140 mK（测试方案参考文献[^5] #TODO ）

---
# 实验结果
## 阈值的滞回
实验步骤：如下图a。首先，栅压维持在某个值$V_\mathrm{stress}$一分钟。然后增加栅压直到达到$V_\mathrm{thres}$。然后降压至新的$V_\mathrm{stress}$再等待一分钟，再升压……$V_\mathrm{stress}$电压先下降，直到某个值$V_\mathrm{stress}^\mathrm{rev}$后开始上升
![滞回现象.png](/img/user/Attachment/%E6%BB%9E%E5%9B%9E%E7%8E%B0%E8%B1%A1.png)

1. 上图b表明$V_\mathrm{thres}$确实与$V_\mathrm{stress}$有关，而且是成滞回循环。下图展示了结果的可重复性（reproducibility），为了省事，所以只做了电压变化明显的两翼，滞回循环中间的平台部分没做。
![滞回现象可重复性.png|400](/img/user/Attachment/%E6%BB%9E%E5%9B%9E%E7%8E%B0%E8%B1%A1%E5%8F%AF%E9%87%8D%E5%A4%8D%E6%80%A7.png)
2. 上图c表明，滞回循环中的平台高度与$V_\mathrm{stress}^\mathrm{rev}$有关。
## 阈值滞回的稳定性
实验步骤：如下图a，增加栅压使得sd电流达到$I_\mathrm{thres}+\Delta I$，然后减少栅压直到sd电流$I_\mathrm{thres}-\Delta I$，然后再增加栅压，再减少栅压……记录每一次加压或减压时的I-V关系，然后线性拟合出sd电流-栅压的关系$I_\mathrm{sd}=mV_\mathrm{gate}+b$，$m$和$b$是拟合系数，然后令$I_\mathrm{sd}=I_\mathrm{thres}$反解出栅压阈值$V_\mathrm{thres}=(I_\mathrm{thres}-b)/m$并绘制与图上
![Pasted image 20231212160614.png|600](/img/user/Attachment/Pasted%20image%2020231212160614.png)
图b是结果，展示了使用优化方案（增加$V_\mathrm{stress}$或不用$V_\mathrm{stress}$栅压）后具有持续3小时时间稳定性。但使用减少$V_\mathrm{stress}$的方案（见[[滞回现象.png]]图a）后，稳定性变差。
## 把方案用于对齐四个量子点的PG阈值
实验对象：如下图a，四个线性排列的量子点。蓝色是PG，黄色是BG，紫色是screening gates，橙色是accumulation。使用这种结构的文章[^12] [^13] [^14] [^15]。
实验步骤：如下图b或下下图。
1. 先把四个PG都加到一个开启的$V_\mathrm{stress}^1$
2. 降低P1直到$I_\mathrm{sd}=I_\mathrm{thres}$，然后提高一点P1的电压至$\Delta V_\mathrm{park}$（$\Delta V_\mathrm{park}=50 \mathrm{mV}$）使得P1维持在弱开启。
3. 降低P2直到$I_\mathrm{sd}=I_\mathrm{thres}$，然后提高一点P2的电压至$\Delta V_\mathrm{park}$使得P2维持在弱开启。
4. P3和P4同上操作。
5. 重复步骤1-4，其中第1步四个PG都加到一个更高的$V_\mathrm{stress}^2=V_\mathrm{stress}^1+\Delta V_\mathrm{stress}$（$\Delta V_\mathrm{stress}=25 \mathrm{mV}$）
6. 直到达到目标阈值，就不再对满足目标的栅进行操作
![Pasted image 20231212160558.png|600](/img/user/Attachment/Pasted%20image%2020231212160558.png)
![Pasted image 20231212160941.png|400](/img/user/Attachment/Pasted%20image%2020231212160941.png)
结果：上图c展示了全文最重要的效果，看到四个gate的开启曲线聚拢，$\Delta V_{thres}$随迭代次数逐渐变小。下图展示了经过上述方案调整后的pinch-off特性的时间稳定性，可以看到没有白调😄！最终$\Delta V_{thres}=20 \mathrm{mV}$与[[量子点的电荷电势\|量子点的电荷电势]]10~60mV相比[^6] [^7] [^8] [^9]，确实可以使得量子点的势能均匀化。
![Pasted image 20231212162647.png](/img/user/Attachment/Pasted%20image%2020231212162647.png)
## 化学势的滞回
实验对象：下图a的结构中的P4量子点
实验步骤：下图c。先给一个栅关闭的电压$V_\mathrm{stress}$，维持1分钟。然后抬压，会出现库伦峰，依次标上颜色并记为$V_t^i$，表示出现第$i$个峰时后的栅压。然后降压至更低的$V_\mathrm{stress}$，等待1分钟……
![Pasted image 20231212173838.png](/img/user/Attachment/Pasted%20image%2020231212173838.png)
上图d是阈值的滞回，操作方法与[[滞回现象.png]]一样。上图e是用的本实验的操作方法得到的图，表示库伦峰的位置（与化学势对应起来）也存在滞回地移动。作者还计算了滞回循环两翼的斜率，发现几乎差不多，所以认为两个滞回循环形状是一样的。

|                                                          | part II   | part IV   |
| ------------------------------------------------------------ | --------- | --------- |
| $\mathrm{d}V_{\mathrm{thres}}/\mathrm{d}V_{\mathrm{stress}}$ | 2.77±0.35 | 3.6±0.25  |
| $\mathrm{d}V_{\mathrm{t}}^2/\mathrm{d}V_{\mathrm{stress}}$   | 0.51±0.01 | 0.87±0.06 |
|                                                              |           |           |
![Pasted image 20231212174103.png](/img/user/Attachment/Pasted%20image%2020231212174103.png)


---
# 展望
作者认为后续还有以下工作可以进行：
1. 用这套方法调整全部gate，包括BG，使得整个量子点具有[[结构图.png]]图b的良好势能背景。
2. 继续优化方案中的参数，使得方案更加高效，比如$\Delta V_\mathrm{stress}$（原文是25mV）和时间步长（原文是1分钟）。甚至$\Delta V_\mathrm{stress}$可以不固定步长，根据[[滞回现象.png]]中的规律，用大步长尽快地渡过平台电压，再用小步长微调电压。
3. 原文是逐个gate调整，后续可以同时调好几个gate，来适应于大规模的量子点阵列。
4. 可用于设计可编程的逻辑器件（scalable device architectures）：
	1. 在crossbar gate architecture中[^10] [^11]，可以只调交叉点的阈值，还可以单独选中每一行来调整。
	2. 适当调整阈值，可以用于隔离量子阱的两个部分

---
# 参考文献

[^1]: Thorbeck, T.; Zimmerman, N. M. Formation of strain-induced quantum dots in gated semiconductor nanostructures. AIP Advances 2015, 5, 087107.
[^2]: Stein, R. M.; Barcikowski, Z. S.; Pookpanratana, S. J.; Pomeroy, J. M.; Stewart, M. D., Jr. Alternatives to aluminum gates for silicon quantum devices: Defects and strain. J. Appl. Phys. 2021, 130, 115102.
[^3]: Lu, T. M.; Lee, C.-H.; Huang, S.-H.; Tsui, D. C.; Liu, C. W. Upper limit of two-dimensional electron density in enhancementmode Si/SiGe heterostructure field-effect transistors. Appl. Phys. Lett. 2011, 99, 153510.
[^4]: Huang, C.-T.; Li, J.-Y.; Chou, K. S.; Sturm, J. C. Screening of remote charge scattering sites from the oxide/silicon interface of strained Si two-dimensional electron gases by an intermediate tunable shielding electron layer. Appl. Phys. Lett. 2014, 104, 243510.
[^5]: F. Borsoi, N. W. Hendrickx, V. John, S. Motz, F. van Riggelen, A. Sammak, S. L. de Snoo, G. Scappucci, and M. Veldhorst, Shared control of a 16 semiconductor quantum dot crossbar array, arXiv , 2209.06609 (2022).
[^6]: Lawrie, W. I. L.; Eenink, H. G. J.; Hendrickx, N. W.; Boter, J. M.; Petit, L.; Amitonov, S. V.; Lodari, M.; Paquelet Wuetz, B.; Volk, C.; Philips, S. G. J.; Droulers, G.; Kalhor, N.; van Riggelen, F.; Brousse, D.; Sammak, A.; Vandersypen, L. M. K.; Scappucci, G.; Veldhorst, M. Quantum dot arrays in silicon and germanium. Appl. Phys. Lett. 2020, 116, 080501.
[^7]: Zajac, D. M.; Hazard, T. M.; Mi, X.; Nielsen, E.; Petta, J. R. Scalable gate architecture for a one-dimensional array of semiconductor spin qubits. Physical Review Applied 2016, 6, 054013.
[^8]: Neyens, S. F.; MacQuarrie, E. R.; Dodson, J. P.; Corrigan, J.; Holman, N.; Thorgrimsson, B.; Palma, M.; McJunkin, T.; Edge, L. F.; Friesen, M.; Coppersmith, S. N.; Eriksson, M. A. Measurements of capacitive coupling within a quadruple-quantum-dot array. Physical Review Applied 2019, 12, 064049.
[^9]: Takeda, K.; Noiri, A.; Nakajima, T.; Yoneda, J.; Kobayashi, T.; Tarucha, S. Quantum tomography of an entangled three-qubit state in silicon. Nat. Nanotechnol. 2021, 16, 965.
[^10]: Li, R.; Petit, L.; Franke, D. P.; Dehollain, J. P.; Helsen, J.; Steudtner, M.; Thomas, N. K.; Yoscovits, Z. R.; Singh, K. J.; Wehner, S.; Vandersypen, L. M. K.; Clarke, J. S.; Veldhorst, M. A crossbar network for silicon quantum dot qubits. Science Advances 2018, 4, No. eaar3960.
[^11]: Borsoi, F.; Hendrickx, N. W.; John, V.; Motz, S.; van Riggelen, F.; Sammak, A.; de Snoo, S. L.; Scappucci, G.; Veldhorst, M. Shared control of a 16 semiconductor quantum dot crossbar array. arXiv, 2209.06609 (2022).
[^12]: Noiri, A.; Takeda, K.; Nakajima, T.; Kobayashi, T.; Sammak, A.; Scappucci, G.; Tarucha, S. Fast universal quantum gate above the fault-tolerance threshold in silicon. Nature 2022, 601, 338.
[^13]: Philips, S. G. J.; Mądzik, M. T.; Amitonov, S. V.; de Snoo, S. L.; Russ, M.; Kalhor, N.; Volk, C.; Lawrie, W. I. L.; Brousse, D.; Tryputen, L.; Paquelet Wuetz, B.; Sammak, A.; Veldhorst, M.; Scappucci, G.; Vandersypen, L. M. K. Universal control of a six-qubit quantum processor in silicon. Nature 2022, 609, 919−924.
[^14]: Zajac, D. M.; Hazard, T. M.; Mi, X.; Nielsen, E.; Petta, J. R. Scalable gate architecture for a one-dimensional array of semiconductor spin qubits. Physical Review Applied 2016, 6, 054013.
[^15]: Neyens, S. F.; MacQuarrie, E. R.; Dodson, J. P.; Corrigan, J.; Holman, N.; Thorgrimsson, B.; Palma, M.; McJunkin, T.; Edge, L. F.; Friesen, M.; Coppersmith, S. N.; Eriksson, M. A. Measurements of capacitive coupling within a quadruple-quantum-dot array. Physical Review Applied 2019, 12, 064049.