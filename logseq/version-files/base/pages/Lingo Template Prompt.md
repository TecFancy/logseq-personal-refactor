type:: [[SOP]]

- ```
  请你扮演英语词汇老师。我需要生成一份完全适配 Anki 导入格式的 CSV 数据。
  请严格按照以下 **16 个字段** 的顺序输出，不可跳过任何一列。
  
  ### ⚠️ 关键格式要求：
  1.  **占位符**：对于 `Word Audio`、`Example Sentence Audio`、`Original Text` 这三列，请务必输出空内容（即两个逗号之间不填内容）。
  2.  **分隔符**：必须使用英文逗号 `,`。
  3.  **防错包裹**：内容中若包含逗号，必须用英文双引号 `"` 包裹。
  4.  **换行**：字段内换行请使用 `<br>`。
  
  ### 字段顺序与生成逻辑（严格对应 Anki 模板）：
  
  1.  **Word**: 单词本身。
  2.  **Word Audio**: （留空，不要填任何内容）
  3.  **Phonetic Symbol**: IPA 音标。
  4.  **Definition**: 中文简明释义。
  5.  **English Definition**: 英文简明释义。
  6.  **Example Sentence**: 经典英文例句。
  7.  **Example Sentence Audio**: （留空，不要填任何内容）
  8.  **Translation of Example Sentence**: 例句中文翻译。
  9.  **Phrase Collocation**:
      * 格式：`• 英文短语: 中文解释 (简短例句)<br>• 第二个短语...`
  10. **Special Inflection**:
      * 格式：一段中文描述变形规则及例句。
  11. **Derivation**:
      * 格式：`1. 派生词 (词性): 中文义<br>2. 派生词...`
  12. **Synonym**:
      * 格式：`word1: 辨析说明<br>word2: 辨析说明`
  13. **Antonym**:
      * 格式：`word1: 中文义<br>word2: 中文义`
  14. **Expansion**: 简短的词源或背景。
  15. **Original Text**: （留空，不要填任何内容）
  16. **Tags**: Lingo
  
  ### 输出 CSV 示例（表头）：
  Word,Word Audio,Phonetic Symbol,Definition,English Definition,Example Sentence,Example Sentence Audio,Translation of Example Sentence,Phrase Collocation,Special Inflection,Derivation,Synonym,Antonym,Expansion,Original Text,Tags
  
  ### 我要学习的单词是：
  [在此输入单词]
  ```