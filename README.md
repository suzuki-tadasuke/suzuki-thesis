# xlab-thesis-template

卒論・修論のフォーマットです．`fork` して使ってください．重大な変更があった場合は，お知らせしますので，本リポジトリを `upstream` として登録しておき，`fetch` と `merge` を行ってください（[詳しい説明](#フォーク元リポジトリに変更があった場合)）．

```bash
git fetch upstream
git checkout main
git merge upstream/main
```

## ディレクトリ構成

| ファイル・ディレクトリ名 | 説明                                                                                                                              |
| ------------------------ | --------------------------------------------------------------------------------------------------------------------------------- |
| `bibliography/`          | 参考文献のディレクトリ`references.bib`内に bib を入れる．                                                                         |
| `figure/`                | 図のファイルを格納するディレクトリ．                                                                                              |
| `sections/`              | 章ごとの tex ファイルを格納するディレクトリ．                                                                                     |
| `styles/`                | スタイルファイルを格納するディレクトリ．タイトルのフォーマットやレイアウトが`xiaolab.sty`で定義されている．基本いじらなくていい． |
| `.chktexrc`              | tex ファイルの linter である`chktex`の設定ファイル．                                                                              |
| `indentconfig.yaml`      | tex ファイルのフォーマッタである`latexindent`の設定ファイル．                                                                     |
| `main.tex`               | メインファイル．これをコンパイルして，pdf ファイルを出力する．                                                                    |

## 使い方の詳細

### 書き始める

論文を書き始める際は，まずこのリポジトリを`fork`してください．`fork`とは簡単に言えば，リポジトリを自分のリポジトリとしてコピーすることです（[参考](https://docs.github.com/ja/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo)）．`fork`ができたら，`main.tex`をコンパイルしてください．うまく pdf が表示されれば，コンパイルは問題なく完了しているということになります．

コンパイルが問題なく完了したら，`main.tex`の属性（氏名，学修番号など）を編集してください．これを設定することで，適切に表紙が表示されると思います．

```latex
\author{座間 渉}                   % 氏名
\title{肖研究室論文フォーマット}      % 論文タイトル
\graduationYear{2000}             % 卒業年度
\studentId{12345678}              % 学修番号
\thesistype{1}                    % 卒論なら1, 修論なら2
```

### フォーク元リポジトリに変更があった場合

このリポジトリで定義されている内容（表紙のレイアウトや引用のルールなど）に変更があった場合，その変更内容をフォークしたリポジトリにも反映させる必要があります．これには，**upstream**とよばれる仕組みを利用することとします（[参考](https://qiita.com/xtetsuji/items/555a1ef19ed21ee42873)）．

手順としては，まず`fork`したリポジトリ（自分の論文のリポジトリ）をローカルで立ち上げ，以下を実行します．

```bash
git remote add upstream git@github.com:tmuxlab/xlab-thesis-template.git
```

これは`upstream`という名前でフォーク元のリモートリポジトリを登録するという操作です．この操作は，1 回行うだけで OK です（2 回目以降は行う必要なし）．

次に，`fork`したリポジトリで`main`ブランチに移動します．すでに`main`ブランチにいる場合はこれを行う必要はありません．

```bash
git checkout main
```

最後に，upstream の内容を更新して，`fork`したレポジトリの`main`ブランチにフォーク元の`main`ブランチ（`upstream/main`）の内容を取り込みましょう．

```bash
git fetch upstream
git merge upstream/main
```

conflict（競合）が発生した場合は，なんらかの形で解消し，`add`と`commit`をしてください（[参考](https://qiita.com/crarrry/items/c5964512e21e383b73da)）．

以上で変更内容の取り込みは完了となります．

## Github Actions

任意のブランチにおいて`push`または`pull_request`があったとき，Lintter と Formatter が自動で実行されるようになっています．

### 使用ツール

- Linter: [chktex](https://www.nongnu.org/chktex/)
- Formatter: [latexindent](https://github.com/cmhughes/latexindent.pl)

### 設定ファイル

- latexindent: `/.chktexrc`
- chktex: `/indentconfig.yaml`
# suzuki-thesis
