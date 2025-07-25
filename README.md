# **CangjieCorpus**

本语料库聚焦 **仓颉编程语言** 核心知识体系，整合官方开发指南、API 文档、典型代码示例及语法规范等多维度资源，经结构化处理与专业标注，构建为支持 
**RAG（检索增强生成）技术** 的高质量知识基座。涵盖 **分布式开发、多端协同、元编程** 等鸿蒙生态核心场景案例，适配智能编码助手、学习辅助工具等应用开发需求。

语料以 **Markdown** 标准化格式存储，保留完整层级结构与语义标签，便于快速接入向量数据库与知识图谱系统。

欢迎开发者基于本语料库构建仓颉语言智能应用，推动鸿蒙开发生态智能化升级！ 

## 语料库结构

当前语料库适配 **仓颉编程语言 v1.0.0**（对应官网文档发布日期：2025-07-01），完整覆盖该版本核心知识体系，结构说明如下：    

###  `extra`

- **功能定位**：存放项目团队基于仓颉语言特性自主设计的扩展功能库，贴合鸿蒙生态分布式开发、设备协同等典型场景。
- **内容说明**： 包含自定义工具类、场景化代码模板及最佳实践示例，**仅供学习研究参考**，不代表官方标准实现。

### `libs`

- **对应范围**：完整映射仓颉官网 [API 库文档](https://cangjie-lang.cn/docs?url=%2F0.53.18%2Flibs%2Flibs_overview.html)，涵盖全量内置库与标准接口。
- **核心内容**：
  - 各模块 API 定义与参数说明
  - 典型调用示例与异常处理指南

### `manual`

- **对应范围**：同步仓颉官网 [用户开发指南](https://cangjie-lang.cn/docs?url=%2F0.53.18%2Fuser_manual%2Fsource_zh_cn%2Ffirst_understanding%2Fbasic.html)，聚焦开发者核心知识需求。
- **核心内容**：
  - 语言基础语法与编程范式详解
  - 多端应用开发流程与工程化实践
  - 性能优化、调试技巧与最佳实践总结

### `tools`

- **对应范围**：同步仓颉官网 [工具指南](https://cangjie-lang.cn/docs?url=/1.0.0/tools/source_zh_cn/IDE/ide_plug-in_overview_community.html)，覆盖工具集官方标准用法。
- **核心内容**：
  - 系统化整合仓颉语言全生命周期开发工具链
  - IDE 插件使用指南, 包括安装、创建仓颉工程、编译构建、调试等
  - 命令行工具使用指南


### 版本一致性说明

所有目录内容对齐仓颉官方文档结构，保留原文标题层级与技术术语定义，确保与 **v1.0.0** 编译器及工具链完全兼容。开发者可通过目录结构快速定位官方文档对应章节，实现知识检索与应用开发的高效衔接。