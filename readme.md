# github-notion-star

GithubのStarをNotionとGithub Actionsで同期して管理します。


## 特徴

- (オプション) すべてのスターとノーションの完全同期をサポート。
- (オプション) Github Actionsを利用した、インクリメンタルスターとノーションの時間同期をサポート。

## セットアップ
- この[テンプレート](https://lcj.notion.site/Github-Notion-Star-f07e2f086e4d4f5b9f25693814c836de)をNotionで再現する
- 現在の Repo をフォークします。
- Repo の設定で、notion-sync という新しい Environment を作成し、以下の環境変数を設定します。
   - NOTION_API_KEY 要求された Notion API のキー。テンプレートはこの API と共有する必要があることに注意。
   - NOTION_DATABASE_ID 対応する Notion データベース ID。
   - TOKEN_OF_GITHUB 現在のユーザーの API の Github トークン。
- これに加えて、現在の設定を環境変数の形で変更することもできます：
   - FULLSYNC_LIMIT 完全同期の最大レポ数、デフォルトは2000。
      - インクリメンタル同期を行うレポの最大数。
   - REPO_TOPICS_LIMIT リポジトリに追加するトピック数、デフォルトは最初の50。
   - この設定は github/workflows/*.yml で変更する必要があります。


## 同期開始
### (オプション）完全同期
- 現在の Github Actions で FullSync Notion Star を見つけて実行すると、以前の Star をすべて同期できます。

### (オプション）インクリメンタル同期
- (オプション）現在のデフォルトのポーリング時間は10分です。 増分同期のポーリング時間を変更したい場合は、.github/workflows/partial-sync.ymlを修正し、on.schedule.cronでポーリング時間を設定する必要があります。
- Github Actions内のPartial Sync Notion Starを有効にする（Forkのレポの場合、すべてのポーリングActionsは自動的に無効になっているので、手動で有効にする必要があります）
