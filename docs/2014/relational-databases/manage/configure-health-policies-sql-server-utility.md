---
title: 正常性ポリシーの構成 (SQL Server ユーティリティ) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 030aac3b-8901-4c41-91ed-aba96420276c
caps.latest.revision: 7
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4c7d9e8b1934d2e9a7953118e8b60c727eb2c268
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36074812"
---
# <a name="configure-health-policies-sql-server-utility"></a>正常性ポリシーの構成 (SQL Server ユーティリティ)
  ph x="1" /&gt; のマネージド インスタンスおよびデータ層アプリケーションに関する [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ユーティリティのリソース パラメーターを表示するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティのダッシュボードを使用します。 詳細については、「 [SQL Server ユーティリティの機能とタスク](sql-server-utility-features-and-tasks.md)」を参照してください。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティの正常性ポリシーの結果を表示するには、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]からユーティリティ コントロール ポイントに接続します。 詳細については、「 [ユーティリティ エクスプローラーを使用した SQL Server ユーティリティの管理](use-utility-explorer-to-manage-the-sql-server-utility.md)」を参照してください。  
  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティの正常性ポリシーは、データ層アプリケーション、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のマネージド インスタンス用に構成できます。 正常性ポリシーは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のすべてのデータ層アプリケーションおよびマネージド インスタンスに対してグローバルに定義できます。また、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータ層アプリケーションごと、およびマネージド インスタンスごとに個別に定義することもできます。  
  
## <a name="monitoring-policies-for-data-tier-applications"></a>データ層アプリケーションのポリシーの監視  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ層アプリケーションの過大使用ポリシーと過小使用ポリシーは次のとおりです。  
  
-   データ層アプリケーションのプロセッサ使用率  
  
-   データ層アプリケーションのデータベース ファイル用のファイル領域  
  
-   データ層アプリケーションの記憶域ボリューム用のファイル領域  
  
-   コンピューターのプロセッサ使用率  
  
> [!NOTE]  
>  データ層アプリケーションの場合、記憶域ボリュームとプロセッサ使用率は読み取り専用ポリシーです。  
  
 データ層アプリケーションのグローバルな監視ポリシーの表示および変更の詳細については、「[ユーティリティの管理 &#40;SQL Server ユーティリティ&#41;](../../database-engine/utility-administration-sql-server-utility.md)」をご覧ください。  
  
 データ層アプリケーション個々の監視ポリシーの表示および変更の詳細については、「[配置済みのデータ層アプリケーションの詳細 &#40;SQL Server ユーティリティ&#41;](../../database-engine/deployed-data-tier-application-details-sql-server-utility.md)」をご覧ください。  
  
## <a name="monitoring-policies-for-managed-instances-of-sql-server"></a>SQL Server のマネージド インスタンスのポリシーの監視  
 ph x="1" /&gt; のマネージド インスタンスの過大使用ポリシーと過小使用ポリシーは次のとおりです。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスのプロセッサ使用率。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスのデータベース ファイル用のファイル領域。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの記憶域ボリューム用のファイル領域。  
  
-   コンピューターのプロセッサ使用率  
  
 ph x="1" /&gt; のマネージド インスタンスのグローバルな監視ポリシーの表示および変更の詳細については、「[ユーティリティの管理 &amp;#40;SQL Server ユーティリティ&amp;#41;](../../database-engine/utility-administration-sql-server-utility.md)」をご覧ください。  
  
 ph x="1" /&gt; の個々のマネージド インスタンスの監視ポリシーの表示および変更の詳細については、「[マネージド インスタンスの詳細 &amp;#40;SQL Server ユーティリティ&amp;#41;](../../database-engine/managed-instance-details-sql-server-utility.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQL Server ユーティリティの機能とタスク](sql-server-utility-features-and-tasks.md)   
 [CPU 使用率のポリシーにおけるノイズの軽減 &#40;SQL Server ユーティリティ&#41;](reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)  
  
  