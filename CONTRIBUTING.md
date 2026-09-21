# 贡献指南

感谢你愿意为 Echi Storyboard Director 出力！

## 你可以贡献什么

- **新的情绪表情卡**：在 `skill/references/action-library.md` 的"表情五官拆解卡"一节补充新的情绪；
- **新的动作拆解**：补充近身搏斗、兵器、异能动作的四层拆解；
- **新的平台适配**：比如 Runway / Pika / Luma 的参数表；
- **新的示例**：在 `examples/` 下加一个完整分镜样例；
- **文档改进**：错别字、表述不清、安装步骤错误。

## 提交前检查清单

- [ ] 你的修改符合 AGPL-3.0，同意以同样协议分发；
- [ ] 新增的规则在 `skill/references/` 里，不要把细节塞进 `SKILL.md`（保持主文件 < 500 行）；
- [ ] 新增的示例能通过 `skill/references/output-template.md` 里的 9 条自检；
- [ ] 没有引入任何需要联网或安装依赖的脚本（本项目保持纯 Markdown）；
- [ ] 更新了 `CHANGELOG.md`。

## 提交方式

1. Fork 本仓库；
2. 新建分支：`git checkout -b feat/your-feature`；
3. 提交：`git commit -m "feat: add xxx"`；
4. 推到你的 fork：`git push origin feat/your-feature`；
5. 开 Pull Request，描述你改了什么、为什么。

## 行为准则

参与本项目即表示你同意遵守 [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md)。
