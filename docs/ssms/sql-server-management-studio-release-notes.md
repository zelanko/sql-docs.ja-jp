---
title: "SQL Server Management Studio - リリース ノート | Microsoft Docs"
ms.custom: 
ms.date: 06/22/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b95337b-80bf-4624-8f5d-cdaf6181d3b8
caps.latest.revision: 51
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: fe6de2b16b9792a5399b1c014af72a2a5ee52377
ms.openlocfilehash: f593303a681e2f52161777fc48f0fb1b479d20d9
ms.contentlocale: ja-jp
ms.lasthandoff: 06/23/2017

---
<a id="sql-server-management-studio----release-notes" class="xliff"></a>

# SQL Server Management Studio - リリース ノート
SQL Server Management Studio の一般公開版リリースにようこそ!  このリリースの SQL Server Management Studio (SSMS) は SQL Server リリースとは別の、スタンドアロン インストールです。 目的は、新しい機能、修正プログラム、SQL Server と Azure SQL Database の最新機能に対するサポートで頻繁に更新することです。  
  
最新の SQL Server Management Studio をインストールするには、「[SQL Server Management Studio &#40;SSMS&#41; のダウンロード](../ssms/download-sql-server-management-studio-ssms.md)」をご覧ください。  
  
このリリースの SQL Server Management Studio に関連する問題と制約を次に示します。  

1. **データベースの復元ウィザードで移行先データベース ファイルの場所を間違ったパス パターンが生成されます**
   これは、SSMS が Linux サーバーに接続されている場合の既知の問題です。 パスが正しくない/奇数を探す場合でも、サーバー側で適切に処理される、つまり機能の問題はありません。

2. **ファイル ブラウザーの問題**
    - SQL Server の 2017 CTP 2.0 を Windows ベースのインスタンスを使用するときにファイル ブラウザー SSMS では、UI を開くには、サーバーに空のフロッピー ドライブまたは固定のディスクがインストールされている Bitlocker で保護されている場合があります。 
    - ファイル ブラウザー UI には、SQL Server 2017 年 1 CTP 2.0 より前のバージョンがサポートされていません。
    


3. **Active Directory ユニバーサル認証を使用して SSMS インスタンス用にログインできる Azure Active Directory アカウントは 1 つだけです。**  
    この制限は、Active Directory ユニバーサル認証に限定されます。Active Directory パスワード認証、Active Directory 統合認証または SQL Server 認証を使用して別のサーバーにログインできます。
    
    回避策としては、別の SSMS インスタンスを使用して、別の Azure Active Directory アカウントとしてログインしてください。 
    
4. **SSMS でのデータ層アプリケーション フレームワーク (DacFx) コマンドおよびスキーマ デザイナーでは、Active Directory ユニバーサル認証はサポートされていません。**  
    SSMS での DacFx を使用するコマンド (例: インポートおよびエクスポート) 、 スキーマ デザイナーでは、現在 Active Directory ユニバーサル認証はサポートされていません。
    
    回避策としては、Active Directory パスワード認証、Active Directory 統合認証または SQL Server 認証など、SSMS で提供される認証の他の形式を使用してください。

5. **SSMS は SQL Server 2016 Integrated Services (SSIS 2016) インスタンスしか接続できません。**  
    以前のバージョンに接続できない SQL Server Integration Services との互換性に関する既知の制限があります。
    
    この問題の回避策としては、 [SSIS インスタンスと連携された SSMS リリース](../ssms/previous-sql-server-management-studio-releases.md)を使用して、SQL Server Integration Service インスタンスに接続してください。 
  
5. **SSMS は、SQL Server 2008 R2 と以前の SQL Server のバージョンのメンテナンス プランを保存しません。**  
    これは将来に対応する既知の制限です。 それまでは、 [SSMS 2014 リリース](../ssms/previous-sql-server-management-studio-releases.md) を使用して、メンテナンス プランを保存してください。  
    
5. **英語以外の SSMS のインストールには、追加のセキュリティ パッケージのインストールが必要になる場合があります。**  
SSMS の英語以外のローカライズされたリリースでは、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 にインストールする場合、 [KB 2862966 セキュリティ更新プログラム パッケージ](https://support.microsoft.com/en-us/kb/2862966) が必要です。

5. **ヘルプをクリック、または F1 キーを押してもヘルプが開きません**  
一部の環境では、ヘルプをクリック、または F1 キーを押すと、**[You'll need a new app to open ms-xhelp]\(ms-xhelp を開くには新しいアプリが必要です\)** と表示されます。 このエラーは既知の問題であり、今後のリリースで修正されます。
  
<a id="feedback" class="xliff"></a>

## フィードバック  
  
![needhelp_person_icon](../ssms/media/needhelp_person_icon.png) [SQL Client Tools Forum](https://social.msdn.microsoft.com/Forums/en-US/home?forum=sqltools) |  [Microsoft Connect で問題や提案を記録](https://connect.microsoft.com/SQLServer/Feedback)。  
  
<a id="see-also" class="xliff"></a>

## 参照  
[SQL Server Management Studio のチュートリアル](../ssms/use-sql-server-management-studio.md)  
[SQL Server Management Studio &amp;#40;SSMS&amp;#41; のダウンロード](../ssms/download-sql-server-management-studio-ssms.md)  
[SQL Server Management Studio の以前のリリース](../ssms/previous-sql-server-management-studio-releases.md)  

  

