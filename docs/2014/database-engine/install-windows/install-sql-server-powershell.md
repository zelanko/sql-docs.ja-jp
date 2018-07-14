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
ms.topic: conceptual
ms.assetid: 854c0b2f-02d2-46a4-a8cc-6b7a5d191cf8
caps.latest.revision: 6
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c5ad01757b050d6beb491e1f0b2878ab124f5d8e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37247028"
---
# <a name="install-sql-server-powershell"></a>SQL Server PowerShell のインストール
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 選択したことを検出した場合、セットアップは停止[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]しますが、Windows PowerShell 2.0 の PowerShell コンポーネントが含まれている機能がインストールされていません。 Windows 管理フレームワークを使用して PowerShell をインストールしてから、セットアップを再実行する必要があります。  
  
## <a name="installing-includessnoversionincludesssnoversion-mdmd-powershell-support"></a>[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell サポートのインストール  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップを使用して、Windows PowerShell に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サポートを提供するソフトウェアをインストールします。 いずれかを選択すると[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]PowerShell が必要な機能のサポートは、セットアップは、Windows PowerShell 2.0 がインストールされていることを確認します。 PowerShell 2.0 が存在する場合は、セットアップし、次がインストールされます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]PowerShell コンポーネント。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell スナップイン。スナップインは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]用の以下の 2 種類の Windows PowerShell サポートを実装する dll ファイルです。  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コマンドレットのセット。 コマンドレットは特定の操作を実装するコマンドです。 たとえば、 **Invoke-Sqlcmd** では、 [!INCLUDE[tsql](../../includes/tsql-md.md)] sqlcmd **ユーティリティを使用して実行することもできる** スクリプトまたは XQuery スクリプトが実行され、 **Invoke-PolicyEvaluation** では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトがポリシー ベースの管理ポリシーに準拠しているかどうかが報告されます。  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロバイダー。 プロバイダーでは、ファイル システム パスと同様のパスを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトの階層内を移動できます。 各オブジェクトは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理オブジェクト モデルのクラスに関連付けられています。 クラスのメソッドやプロパティを使用して、オブジェクトの操作を実行できます。 たとえば、パスでデータベース オブジェクトに移動した場合、Microsoft.SqlServer.Managment.SMO.Database クラスのメソッドとプロパティを使用してデータベースを管理できます。  
  
-   **Sqlps**モジュールを読み込む Windows PowerShell 2.0 セッションにインポートされる、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]スナップイン。  
  
-   非推奨とされる**sqlps**ユーティリティを Windows PowerShell 2.0 セッションを開始し、インポート、 **sqlps**モジュール。  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] は、オブジェクト エクスプローラー ツリーからの Windows PowerShell セッションの起動をサポートします。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントは、Windows PowerShell ジョブ ステップをサポートします。  
  
 インストールされていない、またはがアンインストールされている場合は、Windows PowerShell 2.0 次の手順でインストールする必要があります、 [Windows Management Framework](http://go.microsoft.com/fwlink/?LinkId=186214)ページ。  
  
 セットアップの完了後に Windows PowerShell がアンインストールされる場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]機能の Windows PowerShell は機能しません。 Windows PowerShell をアンインストールできるのは Windows ユーザーです。また、Windows PowerShell のアンインストールは、Windows オペレーティング システムのアップグレードで必要になる場合があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell 機能を使用するには、Windows Management Framework を使用して PowerShell 2.0 を再インストールする必要があります。  
  
## <a name="see-also"></a>参照  
 [SQL Server PowerShell](../../powershell/sql-server-powershell.md)  
  
  
