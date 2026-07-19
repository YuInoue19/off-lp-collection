# off-lp-collection — OFF事業LPの統合リポジトリ

OFF事業のランディングページ（LP）成果物をすべて収める唯一のリポジトリ（旧 gtj-lp のLP成果物を2026-08に吸収統合。gtj-lp はアーカイブ済み）。
GitHub Pages で公開配信中: https://yuinoue19.github.io/off-lp-collection/ （main に push すると1〜2分で自動反映）

## 運用ルール
- LPを編集したら、区切りの良い段階で自動的に commit + push する（確認不要・グローバルルール準拠）。push が配信反映を兼ねる。
- **このリポは Public（全世界公開）。機密を置かない**: 議事録・LP原稿・要件定義・カスタマージャーニー・顧客情報・単価情報は置かず、iCloud `Projects/gtj/lp-制作/` に保存する。
- 構造: `<業種>/<変種>/index.html`。業種= clinic / fitness / salon / common。変種= standard（CBD訴求）/ ads（CBD非訴求・Google広告用）/ 追加は standard-b 等の枝番。
- 同一変種の修正は同じ index.html を上書きする（版管理はGitの履歴が担う。vN フォルダや vN ブランチを作らない）。
- 変種を新設・削除したら、ルートの `index.html`（カタログ）のリンクも同じコミットで更新する。
- ルート直下の `clinic_index.html` 等3枚は旧URL互換の転送スタブ。削除しない。
- 広告表現は薬機法・景表法配慮（gtj/CLAUDE.md準拠）。医療・治療効果を断定しない。
