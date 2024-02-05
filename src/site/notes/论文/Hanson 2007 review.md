---
{"dg-publish":true,"permalink":"/论文/Hanson 2007 review/","created":"2024-01-29T17:47:18.659+08:00","updated":"2024-02-03T19:52:08.000+08:00"}
---

# [[声子\|声子]]诱导[[自旋-轨道耦合\|自旋-轨道耦合]]的能级的跃迁
## 跃迁速率
由[[费马黄金率\|费马黄金率]]得耗散速率
$$
\Gamma=\frac{2\pi}\hbar\sum_{n,l}|^{(1)}\langle nl\uparrow|\mathcal{H}_{e,\mathrm{ph}}|nl\downarrow\rangle^{(1)}|^2D(\Delta E_Z^{(1)})
$$
其中$|nl\downarrow\rangle^{(1)}$是电子的自旋-轨道耦合一级[[微扰态\|微扰态]]，$D(E)$是在能级$E$上的声子数密度，$\mathcal{H}_{e,\mathrm{ph}}$是电子-声子耦合哈密顿量：
$$
\mathcal{H}_{e,\mathrm{ph}}^{\vec{q}j}=M_{\vec{q}j}e^{i\vec{q}\vec{r}}(b_{\vec{q}j}^{\dagger}+b_{\vec{q}j})
$$
其中$M_{\vec{q}j}$是波矢为$\vec{q}$的第$j$分支（一支纵向，两支横向）的声子的电场强度，$\vec{r}$是电子的位置矢量，$b_{\vec{q}j}^{\dagger}$和$b_{\vec{q}j}$是声子的产生和湮灭算符。
综上所述，耗散速率由以下因素决定：
1. 在spin-flip能量处的声子态密度 $D(\Delta E_Z^{(1)})$
2. 电子-声子耦合强度 $|^{(1)}\langle nl\uparrow|\mathcal{H}_{e,\mathrm{ph}}|nl\downarrow\rangle^{(1)}|$。这又由以下因素决定
	1. 自旋-轨道耦合的强度 (与态的作用）
	2. 单个声子的电场强度 $M_{\vec{q}j}$
	3. 声子对不同量子点轨道的有效性 $e^{i\vec{q}\vec{r}}$
	4. 声子布局数 $b_{\vec{q}j}^{\dagger}+b_{\vec{q}j}$
	5. 外部磁场
### 声子态密度
因为光学分支的能量远大于spin-flip能量[^1]，所以可以仅考虑声子的声学分支。由于声学分支具有线性的色散曲线，能量态密度是二次方类型的。
### 自旋-轨道混合的强度（degree of admixing）
根据微扰理论，分母是两能级的差，所以能级越靠近，则混合强度越大。混合程度可以由[[自旋-轨道耦合参数\|自旋-轨道耦合参数]]$\alpha$和$\beta$来描述。自旋-轨道耦合是各向异性的。
### 声子的电场强度
根据对波数$q$的依赖关系，单个声子的电场强度可以分为两类：
1. 压电声子（piezoelectric phonons），强度$\propto 1/\sqrt{q}$
2. 形变势声子（deformation potential phonons），强度$\propto \sqrt{q}$
在能量低的时候，压电声子占主导（$q=\omega/c=\hbar \omega/\hbar c$)。随着能量提高，形变势声子逐渐变成主导。
### 声子对不同量子点轨道的有效性
声子速度$c_{\mathrm{ph}}$~4000m/s，1meV的声子波长$hc_{\mathrm{ph}}/E_{\mathrm{ph}}$~16nm。
1. 当声子波长远大于量子点size，则电子-声子相互作用被平均掉。
2. 当声子波长远小于量子点size，则电子-声子相互作用低效，仅仅是在量子点势能添加或减小一个常数。
3. 当声子波长于量子点size相当，电子-声子相互作用很有效，自旋耗散速率很快。
![Zeeman能量与自旋耗散速率关系.png|300](/img/user/Attachment/Zeeman%E8%83%BD%E9%87%8F%E4%B8%8E%E8%87%AA%E6%97%8B%E8%80%97%E6%95%A3%E9%80%9F%E7%8E%87%E5%85%B3%E7%B3%BB.png)
上图实验是通过TR-RO测量的从三态到单态的耗散速率，横轴是三态的Zeeman能量，显示耗散速率存在一个最大值。
### 声子布局数
声子能导致电子受激辐射，从而在耗散速率中出现$1+N_{\mathrm{ph}}$的系数，且$N_{\mathrm{ph}}$满足玻色-爱因斯坦分布。



[^1]: Ashcroft, N. W., and N. D. Mermin, 1974, Solid State Physics (Saunders, New York).