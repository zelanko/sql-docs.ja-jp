---
title: "正常性ポリシーの構成 (SQL Server ユーティリティ) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 030aac3b-8901-4c41-91ed-aba96420276c
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d1e3fdfceb5d12bb37e9f8289b03e5e3db3e84ad
ms.lasthandoff: 04/11/2017

---
# <a name="configure-health-policies-sql-server-utility"></a>正常性ポリシーの構成 (SQL Server ユーティリティ)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のマネージ インスタンスおよびデータ層アプリケーションに関する [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ユーティリティのリソース パラメーターを表示するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティのダッシュボードを使用します。 詳細については、「 [SQL Server ユーティリティの機能とタスク](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)」を参照してください。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティの正常性ポリシーの結果を表示するには、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]からユーティリティ コントロール ポイントに接続します。 詳細については、「 [ユーティリティ エクスプローラーを使用した SQL Server ユーティリティの管理](../../relational-databases/manage/use-utility-explorer-to-manage-the-sql-server-utility.md)」を参照してください。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティの正常性ポリシーは、データ層アプリケーション、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のマネージ インスタンス用に構成できます。 正常性ポリシーは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のすべてのデータ層アプリケーションおよびマネージ インスタンスに対してグローバルに定義できます。また、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータ層アプリケーションごと、およびマネージ インスタンスごとに個別に定義することもできます。  
  
## <a name="monitoring-policies-for-data-tier-applications"></a>データ層アプリケーションのポリシーの監視  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ層アプリケーションの過大使用ポリシーと過小使用ポリシーは次のとおりです。  
  
-   データ層アプリケーションのプロセッサ使用率  
  
-   データ層アプリケーションのデータベース ファイル用のファイル領域  
  
-   データ層アプリケーションの記憶域ボリューム用のファイル領域  
  
-   コンピューターのプロセッサ使用率  
  
> [!NOTE]  
>  データ層アプリケーションの場合、記憶域ボリュームとプロセッサ使用率は読み取り専用ポリシーです。  
  
 データ層アプリケーションのグローバルな監視ポリシーの表示および変更の詳細については、「[ユーティリティの管理 &#40;SQL Server ユーティリティ&#41;](http://msdn.microsoft.com/library/3e5a00c3-8905-40f0-9ddc-d924df9c2f0d)」をご覧ください。  
  
 データ層アプリケーション個々の監視ポリシーの表示および変更の詳細については、「[配置済みのデータ層アプリケーションの詳細 &#40;SQL Server ユーティリティ&#41;](http://msdn.microsoft.com/library/79c41dd9-abcb-434e-9326-00a341d5c867)」をご覧ください。  
  
## <a name="monitoring-policies-for-managed-instances-of-sql-server"></a>SQL Server のマネージ インスタンスのポリシーの監視  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のマネージ インスタンスの過大使用ポリシーと過小使用ポリシーは次のとおりです。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスのプロセッサ使用率。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスのデータベース ファイル用のファイル領域。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの記憶域ボリューム用のファイル領域。  
  
-   コンピューターのプロセッサ使用率  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のマネージ インスタンスのグローバルな監視ポリシーの表示および変更の詳細については、「[ユーティリティの管理 &#40;SQL Server ユーティリティ&#41;](http://msdn.microsoft.com/library/3e5a00c3-8905-40f0-9ddc-d924df9c2f0d)」をご覧ください。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の個々のマネージ インスタンスの監視ポリシーの表示および変更の詳細については、「[マネージ インスタンスの詳細 &#40;SQL Server ユーティリティ&#41;](http://msdn.microsoft.com/library/6e51b7bb-a733-4852-8c33-7f4dbdf931c2)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQL Server ユーティリティの機能とタスク](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)   
 [CPU 使用率のポリシーにおけるノイズの軽減 &#40;SQL Server ユーティリティ&#41;](../../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)  
  
  
