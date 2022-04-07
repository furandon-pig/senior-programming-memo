
# XcodeからGit,GitHubを使う

## 事前の準備

 * GitHubにアカウントを作成します
 [GitHubの公式ページ](https://docs.github.com/ja/get-started/signing-up-for-github/signing-up-for-a-new-github-account)、その他参考ホームページを参照に、GitHubにアカウントを作成しておきます。
 * Xcodeももちろんインストールしておきます。また、このガイドではXcode 13.2.1を使用しています。

## XcodeおよびGitHub側の設定

1. GitHubでPersonal Account Tokenを発行します。 GitHubにログインし、下図を参照にSettings,Developer Settings さらにPersonal Access Tokensの画面を開きます
<div align="center"><img src="git02.jpg" alt="git2" title="git2" width="500" height="312">&nbsp;<img src="git03.jpg" alt="git3" title="git2" width="500" height="312"></div>
<div align="center"><img src="git04.jpg" alt="git4" title="git4" width="500" height="312"> </div>  
2. Noteに任意の名前(ここではXcode)、有効期間、およびScopeを設定します。Xcodeで必要なScopeはadmin:public_key,write:discussion,repo,userの４つすべてを選択します
  
  
  
  <div align="center"><img src="git05.jpg" alt="git4" title="git4" width="500" height="312"> </div>                 
  
       
3. 発行されたトークンをコピーしておきます


<div align="center"><img src="git06.jpg" alt="git6" title="git6" width="500" height="312"> </div>  


4. XcodeからGitHubにアクセスできるように、アカウント情報とトークンを設定します。Xcode -> Preferences -> Accountsを選択し、GitHubアカウントを追加し、GitHubに登録したメールアドレスを入力し、トークンを貼り付ける。サインインできれば完了


<div align="center"><img src="git07.jpg" alt="git7" title="git7" width="500" height="312">&nbsp;&nbsp;<img src="git08.jpg" alt="git8" title="git8" width="500" height="312"> </div> 

<div align="center"><img src="git09.jpg" alt="git9" title="git9" width="500" height="312"> </div> 

## Xcodeからリポジトリーを作成し、git,GitHubの使用します

1. Source ControlからNew Git Repositoriesを選択し、ローカルにgitリポジトリーを作成します。これによりローカルに最初のcommitが行われます


<div align="center"><img src="git10.jpg" alt="git10" title="git10" width="500" height="312"> </div> 

2. GitHub上にリモートリポジトリーを作成します。左下の図の通りSource Control（１）を選び、続いてRepositories,Remote,New "Hello World" Remoteを選択。右下の図の確認画面が表示されるので、確認の上Createを実行します。注）リポジトリーを他人から見られないようにするためには、Privateを選択します


<div align="center"><img src="git11.jpg" alt="git11" title="git11" width="500" height="312">&nbsp;&nbsp;&nbsp;<img src="git12.jpg" alt="git12" title="git12" width="235" height="207"> </div> 


3. GitHubのWebサイトにログインし、正常にリポジトリーが作成されていることを確認します


<div align="center"><img src="git13.jpg" alt="git13" title="git13" width="490" height="220"> </div> 


4. この後はXcodeのSource Controlメニューからcommit,pushなどのgitコマンドを実行できるようになります。左下は２回commitした状態で、最初のcommit状態を引き出す(Check Out)操作を行っています。右下は最後のcommit状態のソースコードと、最新のソースコード(commit前の段階）を比較しています。


<div align="center"><img src="git14.jpg" alt="git14" title="git14" width="490" height="230">&nbsp;&nbsp;&nbsp;<img src="git15.jpg" alt="git15" title="git15" width="470" height="240"> </div> 
