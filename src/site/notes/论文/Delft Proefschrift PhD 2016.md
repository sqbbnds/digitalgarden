---
{"dg-publish":true,"permalink":"/论文/Delft Proefschrift PhD 2016/","created":"2024-01-29T17:47:18.629+08:00","updated":"2024-02-05T11:27:17.549+08:00"}
---

#GaAs/AlGaAs
# 介绍
## 半导体技术

量子点形成的过程：
1. 通过异质结能带结构，抑制电子在生长方向（z方向）的动力学过程，形成了2DEG[^1]。一般采用相同晶体结构但不同能带结构的异质结，比如GaAs/AlGaAs和Si/SiGe。复合材料的x~0.3.
![能带结构产生2DEG.png|600](/img/user/Attachment/%E8%83%BD%E5%B8%A6%E7%BB%93%E6%9E%84%E4%BA%A7%E7%94%9F2DEG.png)
2. 通过depletion gate的静电势，限制电子在其他方向的运动，形成1D[^2] [^3]或0D[^4] [^5]的系统。这些系统因为尺寸与电子在半导体元素中的德布罗意波长可比拟[^6]，所以展现出了量子效应，可以通过调整栅压来单独调节系统哈密顿量的各个参数（能级结构、隧穿耦合、相干相位）
3. gate是[[实验/肖特基接触\|肖特基接触]]，利用电子束曝光制成（EBL，electron beam lithography，分辨率达10nm）。gate的电子只能从半导体到金属。如果往gate加负电压，如果没有肖特基接触，则电子会进入到2DEG。而肖特基接触阻挡了从gate到半导体的运输，因此可以限制2DEG在xy平方向上的运动。
4. source-drain是欧姆接触，利用金属合金的退火制成，比如GaAs结构中的Au、Ni、Ge。这些合金是沉淀在异质结表面、或给主半导体掺杂形成的。
> [!important]
> 栅极是肖特基接触，漏源是欧姆接触

## 量子计算
1980年代，Feynman提出量子模拟（quantum simulator），通过量子系统的自然演化来模拟任意量子哈密顿量的行为。这个概念导致了量子计算科学[^7]。
如今（2016年），晶体管的沟道尺寸约为15-25nm，因此量子力学变得必要以用于对晶体管行为的建模。然而，现在的晶体管仍然遵循经典的布尔逻辑。
qubit的应用潜力主要来源于两个量子特性：(i)任意两个基本态的叠加态都可以制备和使用。(ii)qubit之间的联系是纠错的非局域的。
> The incredible power of a qubit comes from two main characteristics, intimately related to its quantum nature: (i) every superpositions of the two basis states can be created and used; (ii) the correlation between qubits is non-local (entanglement).

实现量子计算的一项重要技术是纠错码[^7] [^8]，它用多个物理qubit代表为一个逻辑qubit，进而可以在不影响逻辑qubit的情况下检测误差。有文章证明，哪怕是在有退相干的情况下，只要单步操作的误码率低于某个阈值且希尔伯特空间可以任意大，则可以实现通用量子计算[^9]。据此，为了成功实现一套完整的量子算法，需要高保真度的快速幺正操作。
## DIVINCENZO标准
D.P. DiVincenzo提出[^10] [^11]，一个优秀的qubit物理载体候选应该满足5条通用且基本的标准：
1. 希尔伯特空间可控的：两个基本的qubit态能够在实验上被精确地识别。
2. 态可初始化：能够以高准确率识别到某一个态。实验上，一般利用足够长的耗散时间使得系统处于基态，这意味着系统的热能应该远低于qubit的跃迁能量。此外，readout过程也可以作为一种初始化态的协议。
3. 低的退相干：qubit的二能级系统和环境的耦合要足够地小，以至于可以在qubit完全失去他的相干性之前实现纠错码。然而，我们需要qubit与环境耦合，来实施幺正操作或者readout计算结果。所以这一个标准等价地要求manupulate和readout是高效的。
4. 幺正变化是可控的：基本量子门由单qubit或多qubit的幺正操作组成。
5. 支持特定态的readout：在量子计算过程的最后，我们需要高保真度地测量每一个qubit的**终态**。
电子自旋系统满足以上标准。
# 量子点中的自旋比特
## 自旋qubit的特点
1. **退相干时间短**。因为固体系统的自由度很高，所以qubits与环境的相互作用很强，进而很快地失去它的相干性[^12]。所以关键在于找到最优的一种在相干性的保护和manipulation/readout需求之间的权衡。
2. **噪声来源于间接耦合**。用自旋作为qubit的主要优势在于，系统的主要噪声源都有电起源，而电涨落并不会直接与自旋耦合。可是，后来人们发现虽然电噪声不会直接与自旋耦合，但可以通过自旋-轨道相互作用（[[spin-orbit interaction\|spin-orbit interaction]]）间接地耦合。此外，[[自旋退相干的主要成因\|自旋退相干的主要成因]]是核-自旋耦合，也称为超精细相互作用（[[hyperfine interaction\|hyperfine interaction]]）。
## 自旋qubit编码方式
编码方式指的是如何用多个物理量子比特编码为一个逻辑量子比特。在量子点的自旋体系中，已经有不同的编码方案被提出和开发，包括电荷qubit（Charge Qubit）、...
### Charge Qubit
**Charge Qubit由两个可以相互隧穿耦合的两个量子点组成**，也称为DQD（double quantum dot）。每个量子点都可以看成是二能级系统，最多只容纳一个电子。系统的基态是$|L>$或$|R>$，表示只有一个电子在左量子点或右量子点，而另外一个量子点无电子。
#### Initialization方法
态的初始化通过快速退相干过程或charge sensing的readout过程。
#### manipulation方法
无磁场的情况下，一对电子的基态时singlet态，第一激发态是triplet，相互作用的海森堡哈密顿量是$H_S(t)=J(t)S_L\cdot S_R$，其中$J(t)$描述左边和右边电子的耦合强度（coupling strength），这称为交换相互作用（[[exchange interaction\|exchange interaction]]）。交换相互作用实验上是通过控制BG实现的[^13] #TODO 。交换相互作用被用于manipulate qubit，具体而言，有三种manipulation方法???。
### ST0 Qubit
在外加磁场的情况下，DQD的总自旋可以在能量上被区分为$S_z=0$和$S_z=\pm 1$。logical qubit是$S_z=0$的triple（T<sub>0</sub>)和singlet（S），所以这种编码qubit也称为ST<sub>0</sub> qubit[^14] [^15]。
优点：高相干性。[[自旋退相干的主要成因\|自旋退相干的主要成因]]是核-自旋涨落产生的局域磁场涨落，但核自旋涨落是低频的，ST<sub>0</sub>可以相对简单地利用动态解耦协议（dynamical decoupling protocols）来降低核自旋涨落的影响[^16] [^17]。
#### manipulation方法
通用qubit操作：i）交换相互作用；ii）z方向加梯度磁场[^15] ，梯度磁场可以通过极化核自旋域（polarizing the nuclear spin bath）[^18]或微观磁铁（micro magnet）[^19]来实现。
两qubit门操作：电容耦合[^20]
#### readout方法
泡利不相容原理（Pauli spin-blockade）[^21]，把S和T0的自旋分量映射为DQD的电荷数。
#### Initialization方法
通过耗散过程初始化为S态，因为S态强烈地偏爱(2,0)和(0,2)的配置???[^22]
### Exchange-Only Qubit
用三个线性排列的量子点的**两个近邻隧穿耦合**编码为一个逻辑Qubit。
提出者：D. P. DiVincenzo[^23]
优点：只需要操纵exchange interaction，有通用的控制方法，而无需操纵磁场（磁场在实验上是很难控制的）。
进展：已经实现了<sup>28</sup>Si的实验[^24]。但至今(2016)没有实现两比特。
### Hybrid Qubit
三个电子放在两个量子点中[^25] [^26]。logical qubit是(1,2)或(2,1)，即$S=1/2$和$S_z=1/2$的三维自旋子空间。
优点：两个态之间具有更大的能量差，这个能量差是来自隧穿能量。
#### Initialization方法
从triple态到single态的能量relaxation
#### Manipulation方法
单qubit门：detuning方法[^25]。实验上已经实现[^26]。还有使用resonant a.c. microwave driving[^27]（ #TODO 了解微波探测量子点技术）。
两qubit门：理论上提出了用两个Hybrid Qubit之间的[[Coulomb interaction\|Coulomb interaction]]来实现两比特门[^28]，但目前(2016)没有实验实现。
### Loss-DiVincenzo Qubit
单电子限制在单个量子点[^12]。logical qubit是这颗单电子的自旋向上和自旋向下。这是本文的主要研究对象。
### 编码方式小节
| Encoding Schemes      | number of QDs | number of electrons | Logical Qubit          | Advantage             | Initialization Process | Manipulation Process                                                         | Readout Process     |
| :--------------------: | :-------------: | ------------------- | ---------------------- | --------------------- | ---------------------- | ---------------------------------------------------------------------------- | ------------------- |
| Charge Qubit          | 2             | 1                   | 电子在左QD或右QD       | -                     | 退相干或readout        | Exchange interaction                                                         | -                   |
| ST0 Qubit             | 2             | 2                   | single态或triple态     | 有方法提高相干性      | -                      | 通用qubit操作：i）交换相互作用；ii）z方向加梯度磁场；两qubit门操作：电容耦合 | Pauli spin-blockade |
| Exchange-Only Qubit   | 3             | -                   | 两个近邻隧穿耦合       | 门的实现 无需操纵磁场 | -                      | Exchange interaction                                                         | -                   |
| Hybrid Qubit          | 2             | 3                   | (1,2)或(2,1)电子数分配 | 能级差大              | -                      | -                                                                            | -                   |
| Loss-DiVincenzo Qubit | 1             | 1                   | 自旋朝上或朝下         | -                     | -                      | -                                                                            | -                    |
## QDs如何反映能级
**有趣的理解**：量子点是“人造原子（artificial atom）”。真实原子是电子受到原子核的库伦吸引势的限制，而“人造原子”是电子受到人造排斥势的限制。
**量子点定义**：量子点是尺寸远小于电子德布罗意波长的island。
**量子点如何用实现介观结构反映微观能谱**：通过控制depletion gate上的电压，控制电子从电子库到量子点上电子的量子态（能谱）的隧穿过程。
当前有两种source-drain的方式，分别叫做Depletion QDs和Accumulated QDs。
## 探测技术
自旋态的readout分为两步：
1. 把自旋态（如$|\uparrow\rangle$）转换到电荷态（如$|0\rangle$和$|1\rangle$），相当于是把自旋态转换为电子的位置。
	1. 单量子点：在点内和在点外
	2. 双量子点：在左边和在右边
2. 用charge sense探测电荷态。
> [!note]
> readout是指整个量子计算的最后一步，要把结果读出。而不是量子计算的每一步。

对于第一步有两种方法
- tunnel-selective readout：利用不同自旋态从量子点到漏源之间的隧穿率不同
- energy-selective readout：巧妙设计漏源化学势，使得只有自旋激发态的化学势满足隧穿，而自旋基态不满足

对于第二步charge sense
- charge sense是一种基于电子导电通道的探测周围静电环境的装置。因此可以利用它来反映量子点中电子的数目和位置。
- 可以利用低频或射频信号来放大charge sense的信号。
- 有两种charge sense，Quantum Point Contact (QPC)和QD-charge sensor，这篇文献比较了这两种charge sense的性能[^29] 。 #ToRead
- 然而，通过depetion技术在固态系统中创建的大多数电荷传感器显示出有限的灵敏度，特别是因为感测电荷在它和传感器通道（sensor channel，*我理解这是指待探测的量子点*）之间被金属门屏蔽。
- charge sense的带宽可以应用于获取运输的计数统计(acquiring counting statistics of transport)[^30]，隧穿谱(tunneling spectroscopy)[^31]，单发读出(single-shot read-out)[^32]。
## 实验配置
- PCB板
- copper powder filters
- 发光二极管，用于从traps释放电荷，重置[[实验/量子阱\|量子阱]]QW的电荷配置。波长780nm，最大发光强度5mW，最大工作电流35mA（但使用1mA来降低发热）
- copper can，芯片装在里面，屏蔽来自制冷机真空腔的4K液氦的热辐射，避免引起升温。
- 液氦杜瓦内装着two axis superconducting vector magnet，磁场横轴最大3T，杜瓦主轴7T。手动对齐PCB使得偏离不超过5°
### 冷却
- 为了限制温度的展宽效应，以及创建一个良好束缚的2DEG，我们需要冷却device到~20mK。品样的晶格温度接近于最低的制冷机温度~20mK，但2DEG的电子温度往往更热~150-250mK。这是因为在极低温度下，电子-声子相互作用急剧减少，以至于2DEG中的电子不能**通过与声子浴重新达到热平衡**来消耗电子额外的热量。电子额外的热量来自于三方面：热能、电噪声、从暖级来的宏观导线。
- 稀释制冷机冷却2DEG的电子主要是通过连接在欧米接触上的DC或RF线。
> The main cooling contribution to the electrons in the 2DEG comes from the DC/RF wires connected to the ohmic contacts of the device.
### 测量电设备
- LED和光电二极管：把样品与宏观设备（包括计算机）电隔离。
- DC电压源、DACs、电流放大器：==全部用电池供电battery-powered==
	- DACs：给gate加压。16位，电压范围-2V~+2V或0V~±4V，分辨率0.06mV（通过100倍的分压器可以提高分辨率至600nV），电压涨落有效值~4μV/hour
- 48条双绞线：有的用铜线（低电阻但高热导），有的用锰线（低热导但高电阻）。铜线用于快欧姆线，为的是高带宽的实时单电子隧穿测量。所有的线都热接触地通过*包扎方式*固定各个阶段的制冷机上（4K，1K，base temperature）。为了避免经过磁场线圈时引入的干扰，对每一个欧姆接触gate使用了双绞线。
- 4条高频线：在4K和1K区域通过*夹紧方式*与制冷机热接触
- 滤波器：降低DC/RF线的电噪声，噪声会导致电子剧烈震动，从而导致电子升温。我们采用了三个阶段的滤波：
	1. 中频滤波（10MHz~10GHz）：矩阵摆放的Pi滤波器（两个电容和一个电感组成），5~70dB衰减，50Ω载荷。室温。
	2. 高频滤波（1GHz~50GHz）：铜粉滤波器（copper powder，一个装满铜粉的铜管），铜粉可以通过涡流（eddy currents）吸收高频噪声，提供60dB的衰减。base temperature。铜管的输出直接接入到copper can，屏蔽来自4K层的热辐射。
	3. 低频噪声：两个RC滤波器，截止频率分别为30Hz和150kHz，尽可能一致gate电压噪声。
	快欧姆线（接漏源的线）不可能使用上面提到的而滤波器，否则会限制其带宽。因此，Pi滤波器用一个小电容100pF代替，第一级RC滤波电容270pF，所以从室温到样品的总电容~1nF，进而允许IV转换器带宽~50kHz。
- bias-tees：混合微波源（高频信号发生器）和脉冲源（也是DAC出来的），R=10MΩ，C=47nF，即时间常数~500ms脉冲电压源和微波源
![Pasted image 20240102160719.png](/img/user/Attachment/Pasted%20image%2020240102160719.png)
# 样品制备
## 迁移率与载流子浓度进展
迁移率是衡量半导体中杂质的表征指标之一
- 载流子迁移率越高，样品的可调性和稳定性就越高[^34]。2010~2016年实现的单电子自旋和双电子自旋的量子点的电子迁移率在$4\times 10^4-12\times 10^4\mathrm{cm^2/(Vs)}$.
- 用于量子计算的载流子密度越小越好，费米波长则会越大，更容易实现量子点。目标是小于$4\times 10^{11} \mathrm{cm^{-2}}$.
- GaAs材料的迁移率在$T<1\mathrm{K}$时达$3.2\times 10^7\mathrm{cm^2/(Vs)}$，电荷密度$3\times 10^{11} \mathrm{cm^{-2}}$。Si材料的迁移率却低两个数量级。

| 年份 | 关键技术 | 迁移率 cm²/(Vs) | 电荷密度 cm⁻² | 位错密度 cm⁻² | 优点 | 缺点 | 文献 | 备注 |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| 1966 | inversion layer of a Si MOS structure (Si/SiO₂) | 10³ | - | DC | - | 来自Si/SiO₂表面存在很多杂质，导致强散射 | A. B. Fowler, F. F. Fang,W. E. Howard, and P. J. Stiles, Phys. Rev. Lett. 16, 901 (1966).<br>K. v. Klitzing, G. Dorda, andM. Pepper Phys. Rev. Lett. 45, 494 (1980). | 用于验证量子霍尔效应 |
| 2004 | 同上 | 4×10⁴ | - | DC | - | 来自非结晶的SiO₂和晶体的Si界面上的粗糙限制了迁移率的提高 | S. V. Kravchenko andM. P. Sarachik, Reports on Progress in Physics 67, 1 (2004). | - |
| 2015 | vacuum gating of Si (111) | 3.5×10⁴ | - | DC | - | 制造困难 | B. Hu, M. M. Yazdanpanah, B. E. Kane, E. H. Hwang, and S. Das Sarma, Phys. Rev. Lett. 115, 036801 (2015). | - |
| 1985 | a strained Si layer sandwiched between<br>relaxed SiGe alloys | 3×10³ | - | 10⁹ | - | 恒组分的SiGe层与Si之间存在巨大的晶格常数失配，导致位错密度很大 | G. Abstreiter, H. Brugger, T.Wolf, H. Jorke, and H. J. Herzog, Phys. Rev. Lett. 54, 2441 (1985). |  |
| 1991 | virtual/relaxed substrate layers (constant composition Si₀₇Ge₀₃ relaxed buffer layer grown on top of a graded Si₀₇Ge₀₃ buffer) |  |  | 10⁵ |  |  | E. A. Fitzgerald, Y. H. Xie,M. L. Green, D. Brasen, A. R. Kortan, J.Michel, Y. J.Mii and B. E.Weir, Appl. Phys. Lett. 59, 811 (1991). |  |
| 1995 | 同上 | 5.35×10⁵ |  |  |  |  | K. Ismail,M. Arafa, K. L. Saenger, J. O. Chu, and B. S.Meyerson, Appl. Phys. Lett. 66, 1077 (1995). |  |
| 1998 | relaxed substrate  combinating of MBE and solid phase epitaxy | 8×10⁵ |  |  |  |  | N. Sugii, K. Nakagawa, Y. Kimura, S. Yamaguchi, andM.Miyao, Semiconductor Science and Technology 13, A140 (1998). |  |
| 2009 | 20% Ge insulated-gate field effect transistor, Al₂O₃ 150nm, strain Si 15nm, SiGe 66nm | 1.6×10⁶ | 1.5×10¹¹ |  |  |  | T.M. Lu, D. C. Tsui, C. H. Lee, and C.W. Liu, Appl. Phys. Lett. 94, 182102 (2009). |  |
| 2012 | strain Si 15nm, SiGe 530nm, 降低barrier layer和relative layer的Ge组分，进一步降低Si/SiGe界面的晶格失配 x=0.14 | 2×10⁶ |  |  |  |  | S. H. Huang, T. M. Lu, S. C. Lu, C. H. Lee, C. W. Liu, and D. C. Tsui, Appl. Phys. Lett. 101, 042111 (2012). | 当threading dislocation density lower than 10⁵ cm⁻², 迁移率提高的主要限制变成了远端杂质散射 |
| 2014 | strain Si(100) 15nm, SiGe 1000nm/100nm, x=0.18, Si-cap 1nm | 2.2×10⁶ | 1.8×10¹¹ |  |  |  | M. Yu. Melnikov, A. A. Shashkin, V. T. Dolgopolov, S. H. Huang, C. W. Liu and S. V. Kravchenko, JETP Letters 100, 114 (2014).<br>M. Yu. Melnikov, A. A. Shashkin, V. T. Dolgopolov, S. H. Huang, C. W. Liu and S. V. Kravchenko, Appl. Phys. Lett. 106, 092102 (2015). |  |
| 2015 | 低的Si QW层氧离子含量，实验发现少量的背景氧离子导致大的QW中的杂质电荷 | 1.6×10⁵ | 2.17×10¹¹ |  |  | 受远端杂质散射限制进一步的提高 | X.Mi, T.M. Hazard, C. Payette, K.Wang, D.M. Zajac, J. V. Cady, and J. R. Petta, Phys. Rev. B 92, 035304 (2015). |  |
| 2015 | 衬底换成完全松弛的SiGe单晶薄膜栅，消除位错 | 4×10⁴ | 4×10¹¹ |  |  | 与传统SiGe一样，主要限制在Si/介质界面栅的电荷杂质 | Y. S. Li, P. Sookchoo, X. Cui, R. T. Mohr, D. E. Savage, R. H. Foote, R. B. Jacobson, J. R. Sanchez-Perez, D. M. Paskiewicz, X. Wu, D. R. Ward, S. N. Coppersmith, M. A. Eriksson, andM. G. Lagally, ACS Nano 9, 4891 (2015). | 首次用SiGe薄膜作为衬底 |
## 杂质影响
主要由杂质引起的无序性（在结构表面或层与层之间的 doping impurities, dangling bonds, impurities and defects），会导致随机的“非预期的量子点”，这种量子点相比于目标的量子点来说是不可控的，所以需要避免。

杂质对迁移率的影响：
- 背景杂质散射$\mu \propto n$，背景杂质通过实体碰撞影响载流子
- 远端杂质散射 $\mu \propto n^{1.5}$，远处的杂质通过库伦场散射载流子，比如来自于 Si-Cap 的 fixed charge。一种降低远端杂质的方式是增加 SiGe spacing layer 厚度，但这会降低 lateral gate 器件的调制作用。

## 其他信息
[[张力硅晶技术\|张力硅晶技术]]
晶格常数适配度$\Delta=\frac{|a_{e}-a_{s}|}{a_{e}}$，其中$a_{e}$是外延层的晶格常数，$a_{s}$是衬底的晶格常数。
临界厚度：外延层中刚刚要出现位错时的外延层厚度，小于临界厚度时，外延层不会出现新的位错；大于临界厚度时，外延层肯定出现新的位错。
## 样品结构
![Pasted image 20240205112442.png|800](/img/user/Attachment/Pasted%20image%2020240205112442.png)

(i) Si₁₋ₓGeₓ graded buffer (0 < x < 0.3 for this work),
(ii) Si 0.7 Ge 0.3 relaxed buffer,
(iii) strained Si quantumwell (2 DEG),
(iv) relaxed Si 0.7 Ge 0.3 spacer,





---
# 参考文献

[^1]: C. Weisbuch and B. Vinter, ‘Quantum Semiconductor Structures’, Accademic Press, Inc., New York (1991).
[^2]: T. J. Thornton,M. Pepper, H. Ahmed, D. Andrews and G. J. Davies, Phys. Rev. Lett. 56, 1198 (1986).
[^3]: B. J. van Wees, H. van Houten, C. W. J. Beenakker, J. G. Williamson, L. P. Kouwenhoven, D. van derMarel and C. T. Foxon, Phys. Rev. Lett. 60, 848 (1988).
[^4]: L. P. Kouwenhoven, D. G. Austing and S. Tarucha, Rep. Prog. Phys. 64, 701 (2001).
[^5]: M. A. Kastner, Rev.Mod. Phys. 64, 849 (1992).
[^6]: T. Ihn, ‘Semiconductor Nanostructures: Quantum states and electronic transport’, Oxford Scholarship Online (2010).
[^7]: M. A. Nielsen and I. L. Chuang, ‘QuantumComputation and QuantumInformation’, Cambridge University Press (2000).
[^8]: A. R. Calderbank and P.W. Shor, Phys. Rev. A 54, 1098 (1996).
[^9]: D. Aharonov andM. Ben-Or, arXiv:quant-ph/9906129.
[^10]: D. P. DiVincenzo, Science 270, 255 (1995).
[^11]: D. P. DiVincenzo and D. Loss, Superlattices andMicrostructures 23, 419 (1998).
[^12]: R. Hanson, L. P. Kouwenhoven, J. R. Petta, S. Tarucha, and L. M. K. Vandersypen, Rev.Mod. Phys. 79, 1217 (2007).
[^13]: J. R. Petta, A. C. Johnson, J. M. Taylor, E. A. Laird, A. Yacoby, M. D. Lukin, C. M. Marcus,M. P. Hanson, and A. C. Gossard, Science 309, 2180 (2005).
[^14]: J. R. Petta, A. C. Johnson, J. M. Taylor, E. A. Laird, A. Yacoby, M. D. Lukin, C. M. Marcus,M. P. Hanson, and A. C. Gossard, Science 309, 2180 (2005).
[^15]: J. M. Taylor, J. R. Petta, A. C. Johnson, A. Yacoby, C. M. Marcus, and M. D. Lukin, Phys. Rev. B 76, 035315 (2007).
[^16]: S. Foletti, H. Bluhm, D. Mahalu, V. Umansky, and A. Yacoby, Nature Phys. 5, 903 (2009).
[^17]: H. Bluhm, S. Foletti, D. Mahalu, V. Umansky, and A. Yacoby, Phys. Rev. Lett. 105, 216803 (2010).
[^18]: H. Bluhm, S. Foletti, D. Mahalu, V. Umansky, and A. Yacoby, Phys. Rev. Lett. 105, 216803 (2010).
[^19]: X.Wu, D. R.Ward, J. R. Prance, D. Kim, J. K. Gamble, R. T.Mohr, Z. Shi, D. E. Savage, M. G. Lagally, Mark Friesen, S. N. Coppersmith, and M. A. Eriksson, Proceedings of the National Academy of Sciences 111, 11938 (2014).
[^20]: M. D. Shulman, O. E. Dial, S. P. Harvey, H. Bluhm, V. Umansky, A. Yacoby, Science 336, 202 (2012).
[^21]: F. H. L. Koppens, C. Buizert, K. J. Tielrooij, I. T. Vink, K. C. Nowack, T. Meunier, L. P. Kouwenhoven, and L.M. K. Vandersypen, Nature (London) 442, 766 (2006).
[^22]: A. C. Johnson, J. R. Petta, J. M. Taylor, A. Yacoby, M. D. Lukin, C. M. Marcus, M. P. Hanson, and A. C. Gossard, Nature (London) 435, 925 (2005).
[^23]: D. P. DiVincenzo, D. Bacon, J. Kempe, G. Burkard, and K. Whaley, Nature (London) 408, 339 (2000).
[^24]: K. Eng, et al., Sci. Adv. 1 e1500214.
[^25]: Z. Shi, C. B. Simmons, J. R. Prance, J. K. Gamble, T. S. Koh, Y. P. Shim, X. Hu, D. E. Savage,M. G. Lagally,M. A. Eriksson,M. Friesen, and S. N. Coppersmith, Phys. Rev. Lett. 108, 140503 (2012).
[^26]: D. Kim, Z. Shi, C. B. Simmons, D. R. Ward, J. R. Prance, T. S. Koh, J. K. Gamble, D. E. Savage, M. G. Lagally, Mark Friesen, S. N. Coppersmith, andM. A. Eriksson, Nature (London) 511, 70 (2014).
[^27]: D. Kim, D. R. Ward, C. B. Simmons, J. K. Gamble, R. B. Kohout, E. Nielsen, D. E. Savage, M. G. Lagally, Mark Friesen, S. N. Coppersmith, andM. A. Eriksson, Nature Nanotech. 10, 243 (2015).
[^28]: T. S. Koh, J. K. Gamble, Mark Friesen, M. A. Eriksson, and S. N. Coppersmith, Phys. Rev. Lett. 109, 250503 (2012).
[^29]: C. Barthel, M. Kjaergaard, J. Medford, M. Stopa, C. M. Marcus, M. P. Hanson, and A. C. Gossard, Phys. Rev. B 81, 161308(R) (2010).
[^30]: S. Gustavsson, R. Leturcq,M. Studer, I. Shorubalko, T. Ihn, K. Ensslin, D. C. Driscoll, A. C. Gossard, Surface Science Reports 64, 191 (2009).
[^31]: J. M. Elzerman, R. Hanson, L. H. Willems van Beveren, L. M. K. Vandersypen, and L. P. Kouwenhoven, Appl. Phys. Lett. 84, 4617 (2004).
[^32]: J.M. Elzerman, R. Hanson, L. H.Willems van Beveren, B.Witkamp, L.M. K. Vandersypen and L. P. Kouwenhoven, Nature 430, 431 (2004).
[^33]: D. Loss, and D. P. DiVincenzo, Phys. Rev. A 57, 120 (1998)
[^34]: C. B. Simmons, J. R. Prance, B. J. Van Bael, T. S. Koh, Z. Shi, D. E. Savage,M. G. Lagally, R. Joynt, Mark Friesen, S. N. Coppersmith, and M. A. Eriksson, Phys. Rev. Lett. 106, 156804 (2011).