# 第三方参考项目清单（REFERENCES.md）

> 维护规则：所有第三方项目只读，不修改源码；复用代码前必须核对 License；本文件随仓库入库。
> 引入方式分两类：本地只读目录（默认也随仓库入库，重新下载/克隆覆盖更新；需排除的单独在 .gitignore 追加）与 Git Submodule（固定 commit，gitlink 入库）。
> 引入日期：逐条在表格登记时记录。

| ID | 项目 | 仓库 | 本地路径 | 固定 commit | License | 复用策略 | 研究目的 |
|---|---|---|---|---|---|---|---|
| REF-001 | reference-to-game | https://github.com/gokayfem/reference-to-game | thirdparties/reference-to-game | 6a00e491f578bbfcbdba45f0c7bddf4693016e61 | MIT | 方法论参考，按需提炼进自有文档；复用代码前核对 License | 研究参考素材（图像、视频、草图等）转化为可玩游戏的工作流：风格锁定、表现选型、实机玩法构建与验收证据链 |
| REF-002 | guizang-game-skill | https://github.com/op7418/guizang-game-skill | thirdparties/guizang-game-skill | 6001e56e1eaa60be49e5aa4ef81d08b746a1b4e2 | AGPL-3.0 | 方法论参考，按需提炼进自有文档；AGPL 强传染，未集成方案前禁止复制任何代码进自有产品 | 研究 AI 编程助手用 Skill 工作流从零产出浏览器可玩 3D 动作游戏的全流程：需求澄清、素材生成工具链（即梦 Tripo）、three.js 渲染、截图自检与单文件打包（演示作雾锁山门） |
| REF-003 | novel-to-game | https://github.com/zenstory-ai/novel-to-game | thirdparties/novel-to-game | 9017526be7778a66bb1118db820ead17c89f3f3b | MIT | 方法论参考，按需提炼进自有文档；复用代码前核对 License | 研究把小说做成可玩游戏的 5 个 Agent 技能流水线：通读拆书、玩法与美术策划、用本机工具构建、新玩家盲玩验收 |

## Submodule 引入与登记流程

1. 引入：`git submodule add <仓库地址> thirdparties/<项目名>`，克隆后固定到目标 commit。
2. 忽略规则：`.gitignore` 默认不忽略 `thirdparties/`，无需白名单；如某个本地只读目录不入库，单独追加该目录的 ignore 条目。
3. 登记：在本文件表格新增一行，固定 commit 用 `git -C thirdparties/<项目名> rev-parse HEAD` 获取；License 读取仓库内 LICENSE 文件，无 LICENSE 的仓库填「未发现 LICENSE 文件」并将复用策略标为「只读研究，禁止复制任何代码」。
4. 一并提交：`.gitmodules`、submodule gitlink、本文件。
5. 本地只读目录：无 gitlink，其余流程相同（登记、提交清单）；不入库的单独追加 ignore 条目。

## 说明

1. Submodule 只作为源码研究与方法论参考，不代表全部集成进最终产品；集成决策记录在 `dev-docs/research/`。
2. 更新方式：本地目录用重新下载/克隆覆盖；Submodule 用 `git submodule update --remote <path>` 固定新 commit 并更新本表。
3. 复用第三方代码前核对其 License 与版权声明；复用思想则把提炼后的内容写进本仓库自己的文档并标注来源。
