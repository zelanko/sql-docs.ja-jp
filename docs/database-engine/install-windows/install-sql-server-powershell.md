---
title: "SQL Server PowerShell のインストール | Microsoft Docs"
ms.custom: 
ms.date: 02/24/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- setup-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 854c0b2f-02d2-46a4-a8cc-6b7a5d191cf8
caps.latest.revision: 9
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 795a19f9f9d3c357d972197736687628ee2ac51d
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="install-sql-server-powershell"></a>SQL Server PowerShell のインストール
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell のコンポーネントは、セットアップによって自動的に構成されます。  
  
## <a name="installing-includessnoversionincludesssnoversion-mdmd-powershell-support"></a>[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell サポートのインストール  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップを使用して、Windows PowerShell に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サポートを提供するソフトウェアをインストールします。 PowerShell サポートを必要とする任意の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能を選択すると、セットアップにより次の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell コンポーネントがインストールされます。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell スナップイン。 スナップインは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]用の以下の 2 種類の Windows PowerShell サポートを実装する dll ファイルです。  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コマンドレットのセット。 コマンドレットは特定の操作を実装するコマンドです。 たとえば、 **Invoke-Sqlcmd** では、 [!INCLUDE[tsql](../../includes/tsql-md.md)] sqlcmd **ユーティリティを使用して実行することもできる** スクリプトまたは XQuery スクリプトが実行され、 **Invoke-PolicyEvaluation** では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトがポリシー ベースの管理ポリシーに準拠しているかどうかが報告されます。  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロバイダー。 プロバイダーでは、ファイル システム パスと同様のパスを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトの階層内を移動できます。 各オブジェクトは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理オブジェクト モデルのクラスに関連付けられています。 クラスのメソッドやプロパティを使用して、オブジェクトの操作を実行できます。 たとえば、パスでデータベース オブジェクトに移動した場合、Microsoft.SqlServer.Managment.SMO.Database クラスのメソッドとプロパティを使用してデータベースを管理できます。  
  
-   **のスナップインを読み込むために Windows PowerShell のセッションにインポートされる** sqlps [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] モジュール。  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] は、オブジェクト エクスプローラー ツリーからの Windows PowerShell セッションの起動をサポートします。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントは、Windows PowerShell ジョブ ステップをサポートします。  
  
 Windows Server 2012 以降と Windows 8 以降には、PowerShell がインストールされ構成されています。 Windows PowerShell のインストールの詳細については、「 [Windows PowerShell のインストール](http://msdn.microsoft.com/library/hh847837.aspx) 」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md)  
  
  

