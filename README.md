# Igor Pro Development Skills

Igor Pro の Procedure / マクロ（`.ipf`）を AI コーディングエージェントで安全に実装・編集するための Agent Skills 集です。

## インストール

プロジェクトのディレクトリで実行します。

~~~bash
npx skills add assb-lab/igorpro-dev-skills --skill igorpro-8-development
~~~

pnpm の場合:

~~~bash
pnpm dlx skills add assb-lab/igorpro-dev-skills --skill igorpro-8-development
~~~

インストール時に対象エージェントとインストール先を選択してください。

## 収録 Skill

| Skill | 対象 | 概要 |
| --- | --- | --- |
| [igorpro-8-development](skills/igorpro-8-development/SKILL.md) | Igor Pro **8.04** | Igor Pro 8 互換コーディング、IPT の構文チェック・Lint・Formatter、macOS での IPT インストール、コミット前検証、GitHub Actions の導入判断 |

**対応内容**

- Igor Pro 9 以降の構文・API を避け、8.04 互換の `.ipf` を作成・修正
- ローカルでは `command -v ipt` などで IPT の利用可否を確認
- macOS で未インストールなら公式配布元を確認し、`~/.local/bin/ipt` から利用できるようにする
- 変更したファイルに `ipt check` と `ipt lint` を実施し、必要時のみ `ipt format -i` を実施
- **Private リポジトリの GitHub Actions 新設・有効化・実行頻度変更では、事前にユーザーに確認**
- IPT の静的解析と **Igor Pro 8.04 本体でのコンパイル**を区別して報告

## GitHub Actions のサンプル

[導入ガイド](skills/igorpro-8-development/references/github-actions.md) と [コピー可能なテンプレート](skills/igorpro-8-development/assets/igorpro-ci.yml) を収録しています。

テンプレートは **Skill を使うリポジトリへ明示的にコピーするもの**です。このリポジトリ自身では Actions を有効化しません。Private リポジトリには、利用者に「Push / PR で自動実行」「手動実行のみ」「導入しない」から選択してもらうルールを設けています。

## 注意

- [Igor Programming Tool（IPT）](https://docs.byte-physics.de/ipt/) は別製品です。このリポジトリにバイナリは含まれません。
- IPT の配布バイナリには **リリースから 3 か月の使用期限**があり、最新配布版でも期限切れになる場合があります。
- IPT は Igor Pro 8.04 の公式コンパイラではありません。静的解析に成功しても本体でのコンパイル成功とは限りません。
- IPT が受け付ける文字コードは UTF-8 / ASCII です。

## ディレクトリ構成

~~~text
igorpro-dev-skills/
├── LICENSE
├── README.md
└── skills/
    └── igorpro-8-development/
        ├── SKILL.md
        ├── references/
        │   ├── ipt-setup.md
        │   └── github-actions.md
        └── assets/
            └── igorpro-ci.yml
~~~

## 参考資料

- [Igor Pro / WaveMetrics](https://www.wavemetrics.com/)
- [IPT 公式サイト](https://docs.byte-physics.de/ipt/)
- [VS Code Igor Pro 拡張](https://github.com/fujidana/vscode-igorpro)

## ライセンス

[MIT](LICENSE)（Skill のライセンスであり IPT 本体には適用されません）。
