---
title: SQL Server PowerShell のインストール | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 854c0b2f-02d2-46a4-a8cc-6b7a5d191cf8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: dd603a59a1ddb2ede3d3c779d31f13424342edc2
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84932573"
---
# <a name="install-sql-server-powershell"></a>SQL Server PowerShell のインストール
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップは、Windows PowerShell 2.0 をインストールしていないのに、PowerShell コンポーネントを含む [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能を選択したことが検出された場合に停止します。 Windows 管理フレームワークを使用して PowerShell をインストールしてから、セットアップを再実行する必要があります。  
  
## <a name="installing-ssnoversion-powershell-support"></a>[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell サポートのインストール  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップを使用して、Windows PowerShell に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サポートを提供するソフトウェアをインストールします。 PowerShell サポートを必要とする [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能を選択すると、Windows PowerShell 2.0 がインストールされているかどうかが確認されます。 PowerShell 2.0 が存在する場合は、セットアップにより次の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell コンポーネントがインストールされます。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]PowerShell スナップイン。スナップインは、次の2種類の Windows PowerShell サポートを実装する dll ファイルです [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コマンドレットのセット。 コマンドレットは特定の操作を実装するコマンドです。 たとえば、 **Invoke-Sqlcmd** では、 [!INCLUDE[tsql](../../includes/tsql-md.md)] sqlcmd **ユーティリティを使用して実行することもできる** スクリプトまたは XQuery スクリプトが実行され、 **Invoke-PolicyEvaluation** では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトがポリシー ベースの管理ポリシーに準拠しているかどうかが報告されます。  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロバイダー。 プロバイダーでは、ファイル システム パスと同様のパスを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトの階層内を移動できます。 各オブジェクトは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理オブジェクト モデルのクラスに関連付けられています。 クラスのメソッドやプロパティを使用して、オブジェクトの操作を実行できます。 たとえば、パスでデータベース オブジェクトに移動した場合、Microsoft.SqlServer.Managment.SMO.Database クラスのメソッドとプロパティを使用してデータベースを管理できます。  
  
-   スナップインを読み込むために Windows PowerShell 2.0 セッションにインポートされる**sqlps**モジュール [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。  
  
-   Windows PowerShell 2.0 セッションを開始し、 **sqlps**モジュールをインポートする非推奨の**sqlps**ユーティリティ。  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] は、オブジェクト エクスプローラー ツリーからの Windows PowerShell セッションの起動をサポートします。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントは、Windows PowerShell ジョブ ステップをサポートします。  
  
 Windows PowerShell 2.0 がインストールされていない場合、またはアンインストールされている場合は、「 [Windows 管理フレームワーク](https://go.microsoft.com/fwlink/?LinkId=186214)」ページの手順に従ってインストールする必要があります。  
  
 セットアップの終了後に Windows PowerShell がアンインストールされると、Windows PowerShell 用の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能は機能しなくなります。 Windows PowerShell をアンインストールできるのは Windows ユーザーです。また、Windows PowerShell のアンインストールは、Windows オペレーティング システムのアップグレードで必要になる場合があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell 機能を使用するには、Windows Management Framework を使用して PowerShell 2.0 を再インストールする必要があります。  
  
## <a name="see-also"></a>参照  
 [SQL Server PowerShell](../../powershell/sql-server-powershell.md)  
  
  
