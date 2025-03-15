# live-grep-bash

fzf、ripgrep、batを組み合わせた対話的なファイル内容検索ツール

## 特徴

- リアルタイムな検索結果の表示
- シンタックスハイライト付きプレビュー
- 検索結果からファイルパスを簡単に取得

## 必要なもの

- fzf
- ripgrep (rg)
- bat
- bash 4.0以上
- curl

## インストール

インストール/アップデート:

```bash
mkdir -p "${XDG_BIN_HOME:-$HOME/.local/bin}" && curl -fsSL https://raw.githubusercontent.com/ymat19/live-grep-bash/main/live-grep -o "${XDG_BIN_HOME:-$HOME/.local/bin}/live-grep" && chmod +x "${XDG_BIN_HOME:-$HOME/.local/bin}/live-grep"
```

アンインストール:

```bash
rm "${XDG_BIN_HOME:-$HOME/.local/bin}/live-grep"
```

**注意**: インストール先のディレクトリがPATHに含まれていることを確認してください。含まれていない場合は、以下を~/.bashrcまたは~/.zshrcに追加してください：

```bash
export PATH="${XDG_BIN_HOME:-$HOME/.local/bin}:$PATH"
```

## 使い方

### 基本的な使い方

```bash
# カレントディレクトリを検索
live-grep

# 特定のディレクトリを検索
live-grep src/
```

### オプション

```bash
# 特定の拡張子のファイルのみ検索
live-grep -p "*.rs"

# プレビューの前後の行数を指定
live-grep -c 5

# 特定のディレクトリを除外
live-grep -e "node_modules/"
```

### コマンド実行結果をパイプで処理

```bash
# 選択したファイルをVimで開く
live-grep | xargs vim

# 選択したファイルの内容を表示
live-grep | xargs cat
```

### キーバインド

- 検索文字列を入力すると、リアルタイムに結果が表示されます
- 矢印キーで結果をナビゲート
- Enter で選択したファイルのパスを出力
- Ctrl-C で終了

## オプション一覧

- `-p, --pattern PATTERN`: 検索対象のファイルパターン (例: "*.rs")
- `-d, --depth DEPTH`: 検索の深さ
- `-c, --context LINES`: プレビュー時の前後の表示行数 (デフォルト: 2)
- `-e, --exclude PATTERN`: 除外するファイルパターン
- `-h, --help`: ヘルプを表示
- `-v, --version`: バージョンを表示

## ライセンス

MIT License - 詳細は[LICENSE](LICENSE)を参照してください
