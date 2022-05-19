# GitHub

## GitHubとは？

GitHubは「Gitリポジトリのホスティングサービス」です。Gitではソースコードの変更を管理する入れ物として「リポジトリ」を作成し、リポジトリをクローンしたのちにファイルの修正・追加をおこない、作業が完了したらプッシュする、という手順が一連の作業となっていました。

```mermaid
flowchart LR
    repo[(リポジトリ)]
    repo1[(リポジトリ)]
    repo1-->開発者
    repo-- プル -->repo1
    repo1-- プッシュ -->repo
```

Gitリポジトリの形態として、ベア(bare)リポジトリ(リモートリポジトリ)とローカルリポジトリがあります。

 * [サル先生のGit入門](https://backlog.com/ja/git-tutorial/intro/02/)

ローカルリポジトリはその場所(ローカル)に作成したリポジトリに対して履歴を記録するものであり、個人でGitを使用するには向いていますが、複数人での作業では向きません。

複数人でリポジトリの内容を共有しつつ、各人の変更内容をリポジトリに反映したいような場合は、ベアリポジトリ(リモートリポジトリ)を用います。この形態であれば、各人がリポジトリをクローン・プッシュすることが可能になります。

作成したリモートリポジトリをインターネット上から参照できる場所に配置しておくことで、複数人がリポジトリにアクセスできます。ただ、この場合はリポジトリを置いておく場所が必要になります。この「場所」を提供している(ホスティングしている)のがGitHubというサービスになります。

また、GitHubはリモートリポジトリのホスティングだけでなく、プルリクやWiki(ドキュメント共有)、GitHub ActionによるCI(Continuous Integration)といった、複数人で開発プロジェクトを進めるための機能も提供されています。

### 補足：パブリックリポジトリとプライベートリポジトリ

前述したように、GitHub上で作成するリポジトリは(Gitから見ると)すべて「ベアリポジトリ」として作成されます。

GitHubでリポジトリ作成する際にはリポジトリの公開範囲を指定することが可能で、「パブリック」か「プライベート」のどちらかを選択します。パブリックリポジトリはインターネット上の誰もが参照できる形でリポジトリを作成し、プライベートリポジトリはごく限られた人(アクセスを許可された人)のみがリポジトリを参照可能になります。

アプリケーションを作成し、アプリストア等で頒布するような場合はプライベートリポジトリにするのが良いでしょう。

## GitHubにアクセスための設定

GitHubを利用できるようにする場合は、以下の流れで設定を進めます。

 * GitHubへのアカウント作成
 * 公開鍵ペアの作成
 * 公開鍵の登録
 * リポジトリの作成

### GitHubへのアカウント作成

まずはGitHubでアカウントを作成します。アカウント登録時には確認メールが送られてくるため、あらかじめメールアドレスを控えておきます。

 * https://github.com/signup

### 公開鍵ペアの作成

GitHubからリポジトリをクローンしたりプッシュする時、通信内容は暗号化された状態で送受信されます。

その際、内部的にはssh(Secure SHell)という機能が利用され、この中で「公開鍵暗号」を用いたデータの暗号化が行われます。
(以前は上記のアカウント作成時に設定したパスワードによる認証も可能でしたが、現在はセキュリティ上の観点から廃止されています)

 * [公開鍵暗号](https://ja.wikipedia.org/wiki/%E5%85%AC%E9%96%8B%E9%8D%B5%E6%9A%97%E5%8F%B7)
 * [RSAをはじめとした暗号化の仕組みと方式の違いとは？](https://eset-info.canon-its.jp/malware_info/special/detail/200908.html)

ssh公開鍵ペアは以下の手順で作成します。 `-t` は公開鍵で用いる暗号化方式、 `-f` は公開鍵のファイル名(デフォルトでは `id_rsa` `id_rsa.pub` になりますが、用途ごとに公開鍵ファイルを作成するの望ましいです)、 `-C` は公開鍵につけるコメントになります。

 * [新しい SSH キーを生成して ssh-agent に追加する](https://docs.github.com/ja/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

```sh
PS> # Windows(PowerShell)の場合。
PS> cd c:\Users\<ユーザ名>\.ssh
PS> ssh-keygen.exe -t rsa -f my-github-key -C 'keypair_for_github'
```

```sh
$ # macOS/Linuxの場合。
$ mkdir -m 700 ~/.ssh
$ cd ~/.ssh
$ ssh-keygen -t rsa -f my-github-key -C 'keypair_for_github'
```

Windows,macOSのいずれでも以下のように公開鍵につけるパスフレーズが聞かれるため入力します。

```sh
PS ssh-keygen.exe -t rsa -f my-github-key -C 'keypair_for_github'
Generating public/private rsa key pair.
Enter passphrase (empty for no passphrase): ***パスフレーズを入力する***
Enter same passphrase again: ***確認のためパスフレーズを再入力する***
Your identification has been saved in my-github-key.
Your public key has been saved in my-github-key.pub.
The key fingerprint is:
SHA256:z85BU1CCvu+flOx/SIgAyGraDm9ej6B8bWWWdSqNOZg winuser@DESKTOP-EAAPTVR
The key's randomart image is:
+---[RSA 3072]----+
|   . .   .o..    |
|    o . .  o     |
|   .   o    .    |
|  o     o. o     |
| +    o So=. .   |
|o .  E X.*.o...  |
| +. o + o.+ +. . |
|..++ =   o.+ .. .|
|.+o o .  .+.+... |
+----[SHA256]-----+
```

### 公開鍵の登録

作成した公開鍵をGitHubに登録します。

#### sshでアクセスできるか確認する。

`~/.ssh/config` に以下を追記します。

```
Host github.com
        HostName        github.com
        User            git
        IdentityFile    ~/.ssh/my-github-key
```

```sh
$ ssh github.com
PTY allocation request failed on channel 0
Hi <ユーザ名> You've successfully authenticated, but GitHub does not provide shell access.
Connection to github.com closed.
```

### リポジトリの作成

 * (後で書く)
