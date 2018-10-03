---
title: 機能ルール (アップグレード) |Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 653b15db-a984-4b4b-b224-81b0285b099b
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 998ff700a63274c2a57f7e3dc9d6981b2e43bb53
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48193116"
---
# <a name="feature-rules-upgrade"></a>機能ルール (アップグレード)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップは、セットアップ操作が完了する前に、コンピューターの構成を検証します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップの実行中に、システムは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストール先であるコンピューターをスキャンし、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の正常なセットアップ動作を妨げる可能性のある状態をチェックします。 セットアップがアップグレード ウィザードを起動する前に、各項目の状態が取得されます。 次に、必要な条件と取得した結果を比較し、ブロックの問題解決に関するガイダンスを提供します。  
  
 システム構成チェッカーは、実行された各ルールの簡単な記述と、実行ステータスを含むレポートを生成します。 システム構成チェッカーのレポートは %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\< YYYYMMDD_HHMM >\\します。  
  
 セットアップ操作を実行する前に、次のトピックを確認してください。  
  
1.  [SQL Server 2014 のインストールに必要なハードウェアおよびソフトウェア](hardware-and-software-requirements-for-installing-sql-server.md)  
  
2.  [SQL Server 2014 の各エディションがサポートする機能](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
3.  [SQL Server インストールにおけるセキュリティの考慮事項](../../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
4.  [SQL Server のローカル言語版](../../../2014/sql-server/install/local-language-versions-in-sql-server.md)  
  
 その他の参考資料:  
  
1.  [サポートされているバージョンとエディションのアップグレード](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)  
  
2.  [フェールオーバー クラスタリングをインストールする前に](../failover-clusters/install/before-installing-failover-clustering.md)  
  
## <a name="see-also"></a>参照  
 [インストール ルール](../../../2014/sql-server/install/install-rules.md)  
  
  
