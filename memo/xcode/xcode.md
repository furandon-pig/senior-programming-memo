
# XcodeからGit,GitHubを使う

## 事前の準備

 * GitHubにアカウントを作成する
 [GitHubの公式ページ](https://docs.github.com/ja/get-started/signing-up-for-github/signing-up-for-a-new-github-account)、その他参考ホームページを参照に、GitHubにアカウントを作成しておきます。
 * Xcodeももちろんインストールしておきます。また、このガイドではXcode 13.2.1を使用しています。

## XcodeおよびGitHub側の設定

1. GitHubでPersonal Account Tokenを発行する。 GitHubにログインし、下図を参照にSettings,Developer Settings さらにPersonal Access Tokensの画面を開く
<div align="center"><img src="git02.jpg" alt="git2" title="git2" width="500" height="312">&nbsp;<img src="git03.jpg" alt="git3" title="git2" width="500" height="312"></div>
<div align="center"><img src="git04.jpg" alt="git4" title="git4" width="500" height="312"> </div>  
2. Noteに任意の名前(ここではXcode)、有効期間、およびScopeを設定する。Xcodeで必要なScopeはadmin:public_key,write:discussion,repo,userの４つすべてを選択する
  
  
  
  <div align="center"><img src="git05.jpg" alt="git4" title="git4" width="500" height="312"> </div>                 
  
       
3. 発行されたトークンをコピーしておく
<div align="center"><img src="git06.jpg" alt="git6" title="git6" width="500" height="312"> </div>  
4. XcodeからGitHubにアクセスできるように、アカウント情報とトークンを設定する。Xcode -> Preferences -> Accountsを選択し、GitHubアカウントを追加し、GitHubに登録したメールアドレスを入力し、トークンを貼り付ける


<div align="center"><img src="git07.jpg" alt="git7" title="git7" width="500" height="312">&nbsp;<img src="git08.jpg" alt="git8" title="git8" width="500" height="312"> </div> 

<div align="center"><img src="git09.jpg" alt="git9" title="git9" width="500" height="312"> </div> 



