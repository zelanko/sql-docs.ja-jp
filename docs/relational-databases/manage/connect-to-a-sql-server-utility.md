---
title: SQL Server ユーティリティへの接続 | Microsoft Docs
description: SQL Server のリソース正常性を管理できるように、SQL Server ユーティリティに接続する方法について説明します。 SQL Server Management Studio (SSMS) を使用して接続できます。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: b9b90b8d-241f-4b74-ac14-de7b10ea1821
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1d2ea96cc97f84a342c12ea841a263c8bf06adc0
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85776008"
---
# <a name="connect-to-a-sql-server-utility"></a>SQL Server ユーティリティへの接続
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティに接続する前に、ユーティリティ コントロール ポイント (UCP) を作成する必要があります。 詳細については、「 [SQL Server ユーティリティの機能とタスク](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)」を参照してください。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のリソース正常性を表示および管理するには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] (SSMS) を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティに接続します。  
  
 SSMS を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティに接続するには、次の手順を実行します。  
  
1.  SSMS を起動します。  
  
2.  SSMS で、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに接続します。  
  
3.  **[表示]** をクリックし、 **[ユーティリティ エクスプローラー]** をクリックします。  
  
4.  ユーティリティ エクスプローラーのナビゲーション ウィンドウで、![](../../relational-databases/manage/media/connect-to-utility.gif "Connect_to_Utility") **[ユーティリティへの接続]** をクリックします。  
  
5.  **[サーバーへの接続]** ダイアログ ボックスで、UCP インスタンス名を指定し、 **[接続]** をクリックします。  
  
6.  ユーティリティ エクスプローラーのナビゲーション ウィンドウを表示し、UCP の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] リソースのツリー ビューを表示します。  
  
 新しい UCP を作成した場合も、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティに接続されます。 詳細については、「[SQL Server ユーティリティ コントロール ポイントの作成 &#40;SQL Server ユーティリティ&#41;](../../relational-databases/manage/create-a-sql-server-utility-control-point-sql-server-utility.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQL Server ユーティリティの機能とタスク](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)   
 [リソース正常性ポリシーの結果の表示 &#40;SQL Server ユーティリティ&#40;](../../relational-databases/manage/view-resource-health-policy-results-sql-server-utility.md)  
  
  
