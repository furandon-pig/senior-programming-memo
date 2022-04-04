
# XcodeからGit,GitHubを使う

## 事前の準備

 * GitHubにアカウントを作成する
 [GitHubの公式ページ](https://docs.github.com/ja/get-started/signing-up-for-github/signing-up-for-a-new-github-account)、その他参考ホームページを参照に、GitHubにアカウントを作成しておきます。
 * Xcodeももちろんインストールしておきます。また、このガイドではXcode 13.2.1を使用しています。

## XcodeおよびGitHub側のの設定

1. GitHubでPersonal Account Tokenを発行する。
   1. GitHubにログインし、下図を参照にSettings,Developer Settings さらにPersonal Access Tokensの画面を開く


  <div align="center"><img src="git2.jpg" alt="git2" title="git2" width="500" height="312">&nbsp;<img src="git3.jpg" alt="git3" title="git2" width="500" height="312"></div>
  
  
  
  <div align="center"><img src="git4.jpg" alt="git4" title="git4" width="500" height="312"> </div>                 
  
  

  
3. XcodeにGitHubのアカウントを登録する
Xcode -> Preferences -> Accountsを選択し、Git

