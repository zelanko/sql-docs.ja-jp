---
title: SQL Server フェールオーバー クラスターのアップグレード |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- upgrading failover clusters
- clusters [SQL Server], upgrading
- failover clustering [SQL Server], upgrading
ms.assetid: daac41fe-7d0b-4f14-84c2-62952ad8cbfa
caps.latest.revision: 39
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 80f961a228d96561c79fa065b557e229517f73ee
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36176096"
---
# <a name="upgrade-a-sql-server-failover-cluster"></a>SQL Server フェールオーバー クラスターのアップグレード
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、すべてのフェールオーバー クラスター ノードで個別に、[!INCLUDE[ssDE](../../../includes/ssde-md.md)]、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]、[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]、および [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] のフェールオーバー クラスターから[!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)]および [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] をアップグレードすることがサポートされています。  
  
 サポートの詳細は、次のとおりです。  
  
-   ユーザー インターフェイスを使用したアップグレードとコマンド プロンプトからのアップグレードの両方がサポートされています。 詳細については、「[SQL Server フェールオーバー クラスター インスタンスのアップグレード &#40;セットアップ&#41;](upgrade-a-sql-server-failover-cluster-instance-setup.md)」および「[コマンド プロンプトからの SQL Server 2014 のインストール](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)」を参照してください。  
  
-   [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] からのアップグレードについては、各フェールオーバー クラスター ノードでコマンド プロンプトからアップグレードを実行するか、セットアップ UI を使用して各クラスター ノードをアップグレードすることができます。 アップグレードするインスタンスにフルテキスト検索機能およびレプリケーション機能が存在しない場合、これらの機能は、自動的にインストールされ、省略できません。  
  
-   Service Pack のインストールについては、すべてのノードの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] フェールオーバー クラスターに [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] の Service Pack と修正プログラムを個別に適用する必要があります。  
  
-   次のシナリオはサポートされていません。  
  
    -   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のスタンドアロン インスタンスからフェールオーバー クラスターへの移行。  
  
    -   フェールオーバー クラスターへの機能の追加。 たとえば、[!INCLUDE[ssDE](../../../includes/ssde-md.md)] のみの既存のフェールオーバー クラスターに[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]を追加することはできません。  
  
    -   フェールオーバー クラスター ノードからスタンドアロン インスタンスへのダウングレード。  
  
-   詳細については、次を参照してください。 [ AlwaysOn フェールオーバー クラスター インスタンス (SQL Server)](always-on-failover-cluster-instances-sql-server.md)です。  
  
## <a name="upgrading-a-includessnoversionincludesssnoversion-mdmd-multi-subnet-failover-cluster"></a>[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] マルチサブネット フェールオーバー クラスターのアップグレード  
 非マルチサブネットの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] フェールオーバー クラスターを [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] マルチサブネット フェールオーバー クラスターに直接アップグレードすることはできません。 詳細については、「[SQL Server フェールオーバー クラスター インスタンスのアップグレード &#40;セットアップ&#41;](upgrade-a-sql-server-failover-cluster-instance-setup.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [サポートされているバージョンとエディションのアップグレード](../../../database-engine/install-windows/supported-version-and-edition-upgrades.md)   
 [SQL Server フェールオーバー クラスター インスタンスのアップグレード&#40;セットアップ&#41;](upgrade-a-sql-server-failover-cluster-instance-setup.md)   
 [コマンド プロンプトからの SQL Server 2014 のインストール](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)  
  
  