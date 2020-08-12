---
title: フェールオーバー クラスター インスタンスを削除する
description: この手順を使用して、SQL Server のフェールオーバー クラスター インスタンスをアンインストールします。 この記事では、先に進む前に、重要な考慮事項について説明します。
ms.custom: seo-lt-2019
ms.date: 12/13/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- clusters [SQL Server], removing failover clustered instance
- failover clustering [SQL Server], removing failover clustered instance
- uninstalling failover clustered instances
- removing failover clustered instances
ms.assetid: bf63353b-69cf-4c5c-98ea-7b151e36537f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: dba18abbd7eb5938b7f2fa4d0c3caff8d5d6f567
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85897673"
---
# <a name="remove-a-sql-server-failover-cluster-instance-setup"></a>SQL Server のフェールオーバー クラスター インスタンスの削除 (セットアップ)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  この手順を使用して、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のフェールオーバー クラスター インスタンスをアンインストールします。  
  
> [!IMPORTANT]  
>  フェールオーバー クラスターのすべてのノードにサービスとしてログインする権限を持つローカル管理者だけが、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] フェールオーバー クラスターを更新または削除できます。  
  
 **Before you begin**  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] フェールオーバー クラスターをアンインストールする前に、次の重要な点について検討します。  
  
-   誤って [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client をアンインストールすると、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] リソースを起動できなくなります。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client を再インストールするには、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] セットアップ プログラムを実行し、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に必要なコンポーネントをインストールします。  
  
-   複数の SQL IP クラスター リソースを持つフェールオーバー クラスターをアンインストールする場合は、クラスター アドミニストレーターを使用してすべての SQL IP リソースを削除する必要があります。  
  
 コマンド プロンプトの構文については、「 [コマンド プロンプトから SQL Server 2016 をインストール](../../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)」を参照してください。  
  
### <a name="to-uninstall-a-ssnoversion-failover-cluster"></a>[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] フェールオーバー クラスターをアンインストールには  
  
1.  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] フェールオーバー クラスターをアンインストールするには、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] セットアップによって提供されるノードの削除機能を使用して、各ノードを個別に削除します。 詳細については、「[SQL Server フェールオーバー クラスターでのノードの追加または削除 &#40;Setup&#41;](../../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQL Server セットアップ ログ ファイルの表示と読み取り](../../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)  
  
  
