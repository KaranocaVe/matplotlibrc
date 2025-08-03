# matplotlibrc

针对中文优化的多平台兼容 matplotlib 配置文件

## 项目简介

本项目提供了一个经过精心汉化注释和中文显示优化的 `matplotlibrc` 配置文件，适用于 Windows、macOS、Linux 等主流操作系统。旨在帮助中文用户获得更好的 matplotlib 绘图体验，解决中文乱码、字体不兼容、显示效果不佳等常见问题。

![matplotlib 中文显示预览](preview.png)

## 主要特色

- **全面汉化注释**：所有配置项均配有中文说明，便于理解和修改。
- **中文字体优先**：默认字体列表中优先包含常用中文字体，确保中文文本正常显示。
- **多平台兼容**：适配主流操作系统，自动规避平台差异导致的显示问题。
- **科学配色与美观布局**：内置多种配色方案和布局参数，适合学术、工程、商业等多种场景。
- **易于定制**：所有参数均可根据个人需求灵活调整。

## 使用方法

1. **下载配置文件**

   将本仓库中的 `matplotlibrc` 文件下载到本地。

2. **放置到合适位置**

   - 推荐放置在你的项目根目录或 matplotlib 用户配置目录（如 `~/.config/matplotlib/` 或 `~/.matplotlib/`）。
   - 也可在代码中通过 `matplotlib.rc_file_defaults('路径/matplotlibrc.txt')` 加载自定义配置。

3. **重启 Python 环境**

   修改配置后，需重启 Python 解释器或 Jupyter Kernel 以使设置生效。

4. **验证效果**

   使用如下代码测试中文显示：

   ```python
   import matplotlib.pyplot as plt
   plt.plot([1, 2, 3], [4, 5, 6])
   plt.title('中文标题测试')
   plt.xlabel('横轴')
   plt.ylabel('纵轴')
   plt.show()
   ```

## 字体预设说明

本配置文件已针对中文显示进行了详细字体预设，涵盖多种常用中英文字体，确保在不同平台下中文、英文及特殊字符均能正常显示。

- `font.family`：主字体族，推荐设置为 `serif` 或 `sans-serif`，根据个人喜好和场景选择。
- `font.serif`：衬线字体，优先包含 `Source Han Serif CN`、`Noto Serif CJK SC`、`SimSun`、`宋体`等，适合学术、出版等正式场合。
- `font.sans-serif`：无衬线字体，优先包含 `Source Han Sans CN`、`Noto Sans CJK SC`、`Microsoft YaHei`、`Arial` 等，适合报告、演示、网页等场合。
- `font.cursive`：手写体，包含 `STXinwei`、`KaiTi` 等中文手写字体及西文手写体。
- `font.fantasy`：装饰体，包含 Comic Sans MS 等。
- `font.monospace`：等宽字体，优先包含 `Source Code Pro`、`Noto Sans Mono CJK SC`、`Microsoft YaHei Mono` 等，适合代码、表格等场景。

如需根据系统或个人需求调整字体，只需修改 `matplotlibrc` 文件对应参数即可。
> 推荐优先安装思源黑体/宋体（Source Han Sans/Serif）、Noto 字体等开源字体，兼容性和显示效果最佳。

如遇字体未生效，可参考“常见问题”部分进行排查。

## 兼容性说明

- **操作系统**：支持 Windows、macOS、Linux。
- **matplotlib 版本**：建议使用 3.x 及以上版本。
- **Python 版本**：兼容 Python 3.6 及以上。

## 常见问题

### 1. 中文仍然显示为乱码？

如果你已经在 `matplotlibrc` 文件中预设了中文字体（如 SimHei、Microsoft YaHei 等），但中文仍显示为乱码，请按以下方法排查：

- 确认所选字体已正确安装在操作系统中。
- 检查字体名称拼写是否与系统字体一致。
- 使用如下代码查看 matplotlib 实际使用的字体：

  ```python
  import matplotlib.font_manager as fm
  print(fm.findSystemFonts(fontpaths=None, fontext='ttf'))
  print(fm.FontProperties(fname='/完整路径/SimHei.ttf'))
  ```
- 检查 matplotlib 是否能找到并加载你的字体。
- 有些平台（如 macOS）可能需要重启 Python 或 Jupyter Kernel。
- 如仍有问题，可尝试在代码中手动指定字体：

  ```python
  import matplotlib.pyplot as plt
  plt.rcParams['font.sans-serif'] = ['SimHei']
  plt.rcParams['axes.unicode_minus'] = False
  ```

如仍无法解决，请查阅官方文档或提交 issue。

### 2. 配置未生效？

- 检查配置文件路径是否正确。
- 确认没有其他 `matplotlibrc` 文件覆盖你的设置。
- 重启 Python 环境。

### 3. 如何自定义配色和样式？

直接编辑 `matplotlibrc.txt` 文件中的相关参数，如 `axes.color_cycle`、`figure.facecolor` 等，参考中文注释说明。

## 贡献方式

欢迎提交 issue 或 pull request，完善配置项、补充注释或优化兼容性。

## 许可证

MIT License

---

如需更多帮助，请查阅 [matplotlib 官方文档](https://matplotlib.org/stable/users/customizing.html) 或在本仓库提交问题。
