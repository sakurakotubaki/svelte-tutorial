# Svelte + TS + Vite

run server:
```shell
npm run dev
```

## Use Git
GitHubでスカッシュマージする手順を説明します：

1. **Pull Requestの作成**
- mainブランチから作成したf1, f2ブランチそれぞれでPull Request(PR)を作成

2. **マージ方法の選択**
- PRページの「Merge pull request」ボタンの横にある▼をクリック
- 3つのオプションから「Squash and merge」を選択：
  - `Create a merge commit` - 通常のマージ
  - `Squash and merge` - スカッシュマージ ← これを選択
  - `Rebase and merge` - リベースマージ

3. **コミットメッセージの編集**
- スカッシュマージを選択すると、コミットメッセージを編集できるウィンドウが表示
- デフォルトでは：
  - タイトル: PRのタイトル
  - 説明: PRの説明 + 全てのコミットログ

```bash
# 例：コミットメッセージの構成
feat: ログイン機能の実装 (#123)

- ログインフォームの作成
- バリデーション処理の追加
- エラーハンドリングの実装

# 元のコミット履歴
Co-authored-by: name <name@example.com>
```

4. **マージの実行**
- コミットメッセージを確認後、「Squash and merge」ボタンをクリック
- 確認ダイアログで「Confirm squash and merge」をクリック

5. **ブランチの削除**
- マージ完了後、「Delete branch」ボタンでブランチを削除可能

【重要な設定とヒント】：

1. **ブランチの保護設定**
```
リポジトリの Settings > Branches > Branch protection rules
- Require pull request reviews before merging
- Require status checks to pass before merging
- Include administrators
```

2. **デフォルトのマージ方法の設定**
```
リポジトリの Settings > Options > Merge button
- Allow merge commits
- Allow squash merging ← これをチェック
- Allow rebase merging
```

3. **コミットメッセージのテンプレート**
```
# PR Template (.github/pull_request_template.md)
## 変更内容
- 

## 関連Issue
- #

## チェックリスト
- [ ] テストは追加/更新しましたか？
- [ ] ドキュメントは更新しましたか？
- [ ] レビュワーは指定しましたか？
```

4. **レビューのポイント**
- コードの品質
- テストの有無
- コミットメッセージの適切さ
- コンフリクトの有無

5. **マージ後の確認**
```
git fetch origin
git checkout main
git log --oneline  # スカッシュされたコミットを確認
```

【注意点】：
1. スカッシュマージすると個別のコミット履歴は失われる
2. 共同作業者のコミットも1つにまとめられる
3. コンフリクトがある場合は事前に解決が必要

【ベストプラクティス】：
1. PRのタイトルは明確に
2. 関連するIssue番号を含める
3. レビュワーを適切に設定
4. CIチェックが全て通っていることを確認
5. コンフリクトは事前に解決

このようにGitHubのUIを使用することで、より簡単かつ安全にスカッシュマージを行うことができます。