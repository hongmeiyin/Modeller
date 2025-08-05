# 使用Modeller构建蛋白质Loop结构指南

## 引言

蛋白质结构中的loop区域通常是高度可变的，在晶体结构中可能因为灵活性而缺失或结构不清晰。这些区域往往对蛋白质的功能至关重要，例如酶的活性位点或与配体结合的区域。Modeller是一款强大的蛋白质结构建模软件，提供了专门的loop建模功能，可以帮助研究人员预测和优化这些关键区域的结构。

本指南将详细介绍如何使用Modeller软件构建蛋白质loop结构，包括软件安装、理论基础、操作步骤和实例演示。

## 目录

1. Modeller软件简介
2. 安装和环境配置
3. Loop建模的理论基础
4. Loop建模的步骤
   - 准备输入文件
   - 编写Loop建模脚本
   - 参数设置和优化选项
   - 结果分析和验证
5. 实例演示
6. 常见问题和解决方案
7. 参考资源

## 1. Modeller软件简介

Modeller是一款用于蛋白质三维结构同源建模的软件，由Andrej Sali开发。它通过满足空间约束的方法进行蛋白质结构建模，除了基本的同源建模功能外，还可以执行多种任务，包括：

- 蛋白质结构中loop区域的从头建模
- 根据灵活定义的目标函数优化各种蛋白质结构模型
- 蛋白质序列和/或结构的多重比对
- 聚类分析
- 序列数据库搜索
- 蛋白质结构比较等

Modeller的当前版本是10.7（截至2025年5月29日发布）。

## 2. 安装和环境配置

### 2.1 获取许可证

Modeller对学术非营利机构免费提供，但需要注册获取许可证。商业用户可以通过BIOVIA获取许可。

1. 访问Modeller官方网站：https://salilab.org/modeller/
2. 点击"Registration"进行注册
3. 填写相关信息并提交
4. 通过电子邮件接收许可证密钥

### 2.2 下载和安装

Modeller支持多种操作系统，包括Windows、Mac和Linux。以下是各系统的安装步骤：

#### Windows系统

1. 从官方网站下载Windows版本的安装包
2. 运行安装程序，按照向导进行安装
3. 安装过程中需要输入许可证密钥
4. 安装完成后，将Modeller的bin目录添加到系统PATH环境变量中

#### Mac系统

Mac用户可以通过Homebrew安装：

```bash
brew install modeller
```

或者下载Mac安装包手动安装：

1. 下载Mac版本的安装包
2. 解压并运行安装脚本
3. 配置许可证密钥

#### Linux系统

Linux用户可以使用包管理器或手动安装：

**使用包管理器（Debian/Ubuntu）**：

```bash
sudo apt-get install modeller
```

**手动安装**：

1. 下载适合您Linux发行版的安装包（RPM或DEB格式）
2. 对于RPM包：
   ```bash
   sudo rpm -i modeller-10.7-1.x86_64.rpm
   ```
3. 对于DEB包：
   ```bash
   sudo dpkg -i modeller_10.7-1_amd64.deb
   ```

### 2.3 环境变量配置

安装后，需要设置以下环境变量：

1. **KEY_MODELLER**：设置为您的许可证密钥
2. **MODINSTALL**：指向Modeller安装目录

在Linux/Mac系统中，可以在~/.bashrc或~/.bash_profile文件中添加：

```bash
export KEY_MODELLER=your_license_key
export MODINSTALL=/path/to/modeller
export PATH=$PATH:$MODINSTALL/bin
```

在Windows系统中，通过系统属性->高级->环境变量设置这些变量。

### 2.4 验证安装

安装完成后，可以通过运行以下命令验证安装是否成功：

```bash
mod10.7 -h
```

如果安装正确，将显示Modeller的帮助信息。

## 3. Loop建模的理论基础

### 3.1 Loop区域的概念和重要性

Loop区域是蛋白质结构中连接二级结构元素（如α螺旋和β折叠）的不规则区段。这些区域通常位于蛋白质表面，具有较高的灵活性和可变性。Loop区域在蛋白质功能中扮演重要角色：

- 形成酶的活性位点
- 参与配体结合
- 介导蛋白质-蛋白质相互作用
- 影响蛋白质的动力学特性

由于loop区域的高度灵活性，它们在晶体结构中可能缺失或结构不清晰，因此需要通过计算方法进行预测和建模。

### 3.2 Modeller的Loop建模算法原理

Modeller的loop建模方法基于满足空间约束的原理，主要包括以下步骤：

1. **初始构象生成**：首先，Modeller从现有模型中选择需要建模的loop区域，并生成一个初始构象。这个初始构象通常是通过在N端和C端锚定区域之间均匀分布原子来创建的。

2. **构象采样**：Modeller会生成多个loop模型，每个模型首先将初始构象在笛卡尔坐标系中随机化（±5Å），然后进行优化。

3. **能量优化**：优化过程分两个阶段进行：
   - 首先只考虑loop原子
   - 然后考虑loop原子与系统其余部分的相互作用

4. **统计势能函数**：loop优化依赖于一个原子级别的距离依赖统计势能函数，该函数将所有氨基酸原子分类为40种原子类型，并应用MODELLER立方样条约束。

5. **模型评估**：生成的多个loop模型通过DOPE（Discrete Optimized Protein Energy）评分函数进行评估，选择能量最低的模型作为最终结果。

与传统的同源建模不同，loop建模过程中不使用同源性派生的约束，而是完全依赖统计势能函数。

### 3.3 评估模型质量的方法

Modeller提供了多种评估loop模型质量的方法：

1. **DOPE评分**：离散优化蛋白质能量，是一种基于统计的评分函数，用于评估蛋白质结构的整体质量。

2. **Profile评分**：评估模型与序列特征的兼容性。

3. **GA341评分**：结合多种评分方法的复合评分。

4. **Ramachandran图分析**：检查主链二面角的合理性。

5. **RMSD分析**：如果有已知的参考结构，可以计算均方根偏差来评估模型的准确性。

### 3.4 Loop建模的局限性和挑战

Loop建模面临的主要挑战包括：

1. **构象空间大**：随着loop长度的增加，可能的构象数量呈指数增长。

2. **长loop的准确性降低**：一般来说，超过12个残基的loop预测准确性显著降低。

3. **环境依赖性**：loop的构象受周围环境的强烈影响，包括蛋白质其他部分、配体、溶剂等。

4. **晶体接触影响**：实验结构中的loop可能受到晶体接触的影响，与溶液中的构象不同。

5. **多构象状态**：许多loop在生理条件下可能存在多种构象状态。

## 4. Loop建模的步骤

### 4.1 准备输入文件

Loop建模需要以下输入文件：

1. **初始模型文件**：包含需要优化loop区域的蛋白质结构模型（PDB格式）
2. **序列文件**：目标蛋白质的氨基酸序列（PIR格式）

#### 示例PIR格式序列文件（target.ali）：

```
>P1;target
sequence:target:1:A:333:A:::
MKGPVRVAVTGAAGQIGYSLLFRIAAGEEQGKDQPVILQLLEIPQAMKALEGVVMELEDCAFPLLA
GLEATDDPKVAFKDADYALLVGAAPRLQVNGKIFTEQGRALAEVAKKDVKVLVVGNPANTNALIAK
NAPGLNPRNFTAMTRLDHNRAKAQLAKKTGTGVDRIRRMTVWGNHSSTMFPDLFHAEVDGRPALEL
VDMEWYEKVFIPTVAQRGAAIIQARGASSAASAANAAIEHIRDWALGTPEGDWVSMAVPSQGEYGI
PEGIVYSFPVTAKDGAYRVVEGLEINEFARKRMEITAQELLDEMEQVKALGLI*
```

### 4.2 编写Loop建模脚本

以下是一个基本的loop建模Python脚本示例：

```python
from modeller import *
from modeller.automodel import *

# 创建环境
env = Environ()
env.io.atom_files_directory = ['.', '../atom_files/']

# 创建一个继承自LoopModel的类，以便自定义loop选择
class MyLoop(LoopModel):
    # 这个方法选择需要通过loop建模优化的残基
    def select_loop_atoms(self):
        # 选择残基93-100作为loop区域
        return Selection(self.residue_range('93:', '100:'))

# 使用初始模型和目标序列创建模型
a = MyLoop(env, 
           inimodel='initial_model.pdb',  # 初始模型文件
           sequence='target')              # 目标序列名称

# 设置loop建模参数
a.loop.starting_model = 1      # 第一个loop模型的索引
a.loop.ending_model = 5        # 最后一个loop模型的索引
a.loop.md_level = refine.very_fast  # loop优化方法

# 评估方法
a.loop_assess_methods = assess.DOPE  # 使用DOPE评分函数评估loop质量

# 开始建模
a.make()
```

### 4.3 参数设置和优化选项

Modeller提供了多种参数来控制loop建模过程：

#### 4.3.1 Loop选择

通过重写`select_loop_atoms()`方法来指定需要建模的loop区域：

```python
def select_loop_atoms(self):
    # 单个loop区域
    return Selection(self.residue_range('93:', '100:'))
    
    # 多个loop区域
    # return Selection(self.residue_range('93:', '100:'),
    #                 self.residue_range('150:', '160:'))
```

#### 4.3.2 优化级别

Modeller提供不同级别的优化方法，可以通过`md_level`参数设置：

```python
# 快速但质量较低
a.loop.md_level = refine.very_fast

# 较慢但质量更高
# a.loop.md_level = refine.slow
```

优化级别从快到慢（质量从低到高）依次为：
- `refine.very_fast`
- `refine.fast`
- `refine.medium`
- `refine.slow`
- `refine.very_slow`

#### 4.3.3 模型数量

通过设置`starting_model`和`ending_model`参数控制生成的模型数量：

```python
a.loop.starting_model = 1  # 起始模型索引
a.loop.ending_model = 10   # 结束模型索引（将生成10个模型）
```

#### 4.3.4 评估方法

可以选择不同的评分函数来评估loop模型质量：

```python
# 使用DOPE评分
a.loop_assess_methods = assess.DOPE

# 使用多种评分方法
# a.loop_assess_methods = [assess.DOPE, assess.GA341]
```

### 4.4 结果分析和验证

Loop建模完成后，Modeller会生成多个模型文件：

1. **初始loop模型**：扩展名为`.IL`
2. **优化后的loop模型**：扩展名为`.BL`，后跟模型编号

#### 4.4.1 评估模型质量

可以使用以下脚本计算所有模型的DOPE评分：

```python
from modeller import *
from modeller.scripts import complete_pdb

env = Environ()
env.libs.topology.read(file='$(LIB)/top_heav.lib')
env.libs.parameters.read(file='$(LIB)/par.lib')

# 读取所有生成的模型
model_files = ['model.BL00010001.pdb', 'model.BL00010002.pdb', 
               'model.BL00010003.pdb', 'model.BL00010004.pdb', 
               'model.BL00010005.pdb']

# 计算每个模型的DOPE评分
for file in model_files:
    # 读取模型
    mdl = complete_pdb(env, file)
    
    # 选择所有原子
    s = Selection(mdl)
    
    # 计算DOPE评分
    score = s.assess_dope()
    
    print(f"Model {file}: DOPE score = {score}")
```

#### 4.4.2 可视化分析

可以使用PyMOL、Chimera或VMD等分子可视化软件对生成的模型进行分析：

1. 加载所有模型进行比较
2. 检查loop区域的构象
3. 分析loop与周围残基的相互作用
4. 检查主链和侧链的合理性

#### 4.4.3 Ramachandran图分析

可以使用PROCHECK或MolProbity等工具分析模型的Ramachandran图，检查主链二面角的合理性。

## 5. 实例演示

以下是一个完整的实例，演示如何使用Modeller对乳酸脱氢酶（LDH）中的活性位点loop进行建模。

### 5.1 问题描述

在这个例子中，我们将对LDH蛋白质中的活性位点loop（残基93-100）进行建模。这个loop在晶体结构中因为高度灵活性而缺失。

### 5.2 准备输入文件

1. **初始模型**：使用同源建模得到的LDH模型（`TvLDH.B99990001.pdb`）
2. **目标序列**：LDH序列文件（`TvLDH.ali`）

### 5.3 编写Loop建模脚本

创建文件`loop_model.py`：

```python
from modeller import *
from modeller.automodel import *

# 创建环境
env = Environ()
env.io.atom_files_directory = ['.', '../atom_files/']

# 创建一个继承自LoopModel的类
class MyLoop(LoopModel):
    # 选择需要建模的loop区域
    def select_loop_atoms(self):
        # 选择残基93-100作为loop区域
        return Selection(self.residue_range('93:', '100:'))

# 使用初始模型和目标序列创建模型
a = MyLoop(env, 
           inimodel='TvLDH.B99990001.pdb',  # 初始模型文件
           sequence='TvLDH')                # 目标序列名称

# 设置loop建模参数
a.loop.starting_model = 1      # 第一个loop模型的索引
a.loop.ending_model = 5        # 最后一个loop模型的索引
a.loop.md_level = refine.slow  # 使用较高质量的优化方法

# 评估方法
a.loop_assess_methods = assess.DOPE  # 使用DOPE评分函数评估loop质量

# 开始建模
a.make()
```

### 5.4 运行Loop建模

执行脚本：

```bash
python loop_model.py
```

脚本将生成5个loop模型，并使用DOPE评分函数评估它们的质量。

### 5.5 分析结果

创建文件`evaluate_models.py`来分析生成的模型：

```python
from modeller import *
from modeller.scripts import complete_pdb

env = Environ()
env.libs.topology.read(file='$(LIB)/top_heav.lib')
env.libs.parameters.read(file='$(LIB)/par.lib')

# 读取所有生成的模型
model_files = ['TvLDH.BL00010001.pdb', 'TvLDH.BL00010002.pdb', 
               'TvLDH.BL00010003.pdb', 'TvLDH.BL00010004.pdb', 
               'TvLDH.BL00010005.pdb']

# 计算每个模型的DOPE评分
results = []
for file in model_files:
    # 读取模型
    mdl = complete_pdb(env, file)
    
    # 选择所有原子
    s = Selection(mdl)
    
    # 计算DOPE评分
    score = s.assess_dope()
    
    results.append((file, score))
    print(f"Model {file}: DOPE score = {score}")

# 按DOPE评分排序（越低越好）
results.sort(key=lambda x: x[1])
print(f"\nBest model: {results[0][0]} with DOPE score = {results[0][1]}")
```

执行评估脚本：

```bash
python evaluate_models.py
```

### 5.6 结果可视化

使用PyMOL可视化最佳模型：

```bash
pymol TvLDH.BL00010001.pdb
```

在PyMOL中，可以使用以下命令高亮显示loop区域：

```
select loop, resi 93-100
color red, loop
show sticks, loop
```

## 6. 常见问题和解决方案

### 6.1 Loop建模失败或崩溃

**问题**：Loop建模过程中程序崩溃或报错。

**解决方案**：
- 检查输入文件格式是否正确
- 确保loop区域的选择合理，不要选择过长的loop
- 增加环境变量中的内存限制
- 尝试使用更简单的优化级别（如`refine.very_fast`）

### 6.2 Loop模型质量差

**问题**：生成的loop模型质量不佳，DOPE评分高或结构不合理。

**解决方案**：
- 增加生成的模型数量（如从5个增加到20个）
- 使用更高级别的优化方法（如`refine.slow`或`refine.very_slow`）
- 考虑使用多模板建模方法
- 如果有配体，考虑在建模过程中包含配体

### 6.3 长Loop的建模挑战

**问题**：长度超过12个残基的loop难以准确建模。

**解决方案**：
- 增加生成的模型数量（如50-100个）
- 使用更高级别的优化方法
- 考虑使用其他专门的loop建模软件（如Rosetta Loop Modeling）
- 如果可能，使用实验约束来指导建模

### 6.4 许可证问题

**问题**：运行Modeller时出现许可证错误。

**解决方案**：
- 确保正确设置了`KEY_MODELLER`环境变量
- 检查许可证是否过期，如果过期则需要重新申请
- 确保使用的是与安装版本匹配的许可证

## 7. 参考资源

### 7.1 官方文档和教程

- [Modeller官方网站](https://salilab.org/modeller/)
- [Modeller教程](https://salilab.org/modeller/tutorial/)
- [Modeller手册](https://salilab.org/modeller/manual/)

### 7.2 学术论文

1. Fiser, A., Do, R.K., & Sali, A. (2000). Modeling of loops in protein structures. *Protein Science*, 9(9), 1753-1773.
2. Sali, A., & Blundell, T.L. (1993). Comparative protein modelling by satisfaction of spatial restraints. *Journal of Molecular Biology*, 234(3), 779-815.
3. Webb, B., & Sali, A. (2016). Comparative protein structure modeling using MODELLER. *Current Protocols in Bioinformatics*, 54, 5.6.1-5.6.37.

### 7.3 在线资源

- [ModLoop服务器](https://modbase.compbio.ucsf.edu/modloop/) - 基于Modeller的在线loop建模服务
- [ModBase数据库](https://modbase.compbio.ucsf.edu/) - 包含大量使用Modeller生成的蛋白质结构模型

### 7.4 相关软件

- [PyMOL](https://pymol.org/) - 用于分子可视化和分析
- [UCSF Chimera](https://www.cgl.ucsf.edu/chimera/) - 用于交互式可视化和分析分子结构
- [MolProbity](http://molprobity.biochem.duke.edu/) - 用于验证蛋白质结构质量

## 结论

Modeller的loop建模功能是预测蛋白质结构中缺失或不确定区域的强大工具。通过遵循本指南中的步骤和最佳实践，研究人员可以生成高质量的loop模型，从而更好地理解蛋白质的结构和功能。随着计算方法和力场的不断改进，loop建模的准确性将继续提高，为结构生物学和药物设计等领域提供更有价值的信息。

