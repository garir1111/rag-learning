# これはなに？

## 参考文献

1. [LangChain と LangGraph による RAG・AI エージェント［実践］入門](https://amzn.asia/d/abnDoNd)
2. [VSCode で Jupyter Notebook の開発環境を構築する手順](https://zenn.dev/torakm/articles/55b16afb0a3941#6.-vscode-で-jupyter-notebook-を開く)

## これはなに

参考文献 1 では、google colab で実行するように書かれているが、  
colab 特有の動きがあったりして謎に実行できないストレスがあったため、ローカルで実行できるようにした。

## 構築手順

```zsh
$ uv sync
$ uv run python -m ipykernel install --user --name=rag_learning --display-name "Python (rag_learning)
```

vscode で開き、「カーネルを選択する」

以下を実行して、OPEN_API_KEY を Jupyter に教える。

```python
import os
from dotenv import load_dotenv

load_dotenv()

os.environ['OPENAI_API_KEY'] = os.getenv('OPENAI_API_KEY')
```

### 仮想環境の有効化

```zsh
$ . .venv/bin/activate
```

### オプション

```zsh
$ uv run jupyter lab
```

## deploy

書いたら、下記に目次として追加する。
`rag_learning/_toc.yml`

以下でデプロイする。

```zsh
$ jb build --all .
$ git add .
$ git commit -m "とりあえず"
$ git push origin master
$ ghp-import -n -p -f _build/html
```
