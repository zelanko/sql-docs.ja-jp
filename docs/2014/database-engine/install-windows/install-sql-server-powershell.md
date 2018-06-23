---
title: SQL Server PowerShell のインストール | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 854c0b2f-02d2-46a4-a8cc-6b7a5d191cf8
caps.latest.revision: 6
author: mgblythe
ms.author: mblythe
manager: jhubbard
ms.openlocfilehash: 26ddefde6223effd90d2130c40c28011de411802
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36164148"
---
# <a name="install-sql-server-powershell"></a>SQL Server PowerShell のインストール
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 選択したことを検出した場合、セットアップは停止[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Windows PowerShell 2.0 は、PowerShell コンポーネントが含まれている機能がインストールされていません。 Windows 管理フレームワークを使用して PowerShell をインストールしてから、セットアップを再実行する必要があります。  
  
## <a name="installing-includessnoversionincludesssnoversion-mdmd-powershell-support"></a>[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell サポートのインストール  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップを使用して、Windows PowerShell に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サポートを提供するソフトウェアをインストールします。 いずれかを選択すると[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]PowerShell が必要な機能のサポートは、セットアップでは、Windows PowerShell 2.0 がインストールされていることを確認します。 PowerShell 2.0 が存在する場合は、セットアップし、インストール[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]PowerShell コンポーネント。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell スナップイン。スナップインは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]用の以下の 2 種類の Windows PowerShell サポートを実装する dll ファイルです。  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コマンドレットのセット。 コマンドレットは特定の操作を実装するコマンドです。 たとえば、 **Invoke-Sqlcmd** では、 [!INCLUDE[tsql](../../includes/tsql-md.md)] sqlcmd **ユーティリティを使用して実行することもできる** スクリプトまたは XQuery スクリプトが実行され、 **Invoke-PolicyEvaluation** では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトがポリシー ベースの管理ポリシーに準拠しているかどうかが報告されます。  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロバイダー。 プロバイダーでは、ファイル システム パスと同様のパスを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトの階層内を移動できます。 各オブジェクトは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理オブジェクト モデルのクラスに関連付けられています。 クラスのメソッドやプロパティを使用して、オブジェクトの操作を実行できます。 たとえば、パスでデータベース オブジェクトに移動した場合、Microsoft.SqlServer.Managment.SMO.Database クラスのメソッドとプロパティを使用してデータベースを管理できます。  
  
-   **Sqlps**モジュールを読み込む Windows PowerShell 2.0 セッションにインポートされている、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]スナップイン。  
  
-   非推奨**sqlps**ユーティリティを Windows PowerShell 2.0 セッションを開始し、インポート、 **sqlps**モジュール。  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] は、オブジェクト エクスプローラー ツリーからの Windows PowerShell セッションの起動をサポートします。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントは、Windows PowerShell ジョブ ステップをサポートします。  
  
 Windows PowerShell 2.0 がインストールされていないがアンインストールされている場合は、指示に従ってインストールする必要があります、 [Windows Management Framework](http://go.microsoft.com/fwlink/?LinkId=186214)ページ。  
  
 セットアップが完了したら、Windows PowerShell がアンインストールされている場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]機能の Windows PowerShell は機能しません。 Windows PowerShell をアンインストールできるのは Windows ユーザーです。また、Windows PowerShell のアンインストールは、Windows オペレーティング システムのアップグレードで必要になる場合があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell 機能を使用するには、Windows Management Framework を使用して PowerShell 2.0 を再インストールする必要があります。  
  
## <a name="see-also"></a>参照  
 [SQL Server PowerShell](../../powershell/sql-server-powershell.md)  
  
  