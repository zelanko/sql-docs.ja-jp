---
title: "WQL を使用して構成管理の WMI プロバイダーにアクセス |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: wmi
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- query language [WMI]
- WMI Query Language [WMI]
- WQL [WMI]
- WMI Provider for Configuration Management, WQL
ms.assetid: 26499530-d93b-452b-bbe4-217ef1d11e68
caps.latest.revision: 
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e56590202577f6be6c9009237137b4a6909c9542
ms.sourcegitcommit: 0d904c23663cebafc48609671156c5ccd8521315
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2018
---
# <a name="access-wmi-provider-for-configuration-management-using-wql"></a>WQL を使用して構成管理の WMI プロバイダーにアクセスする
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  このセクションでは、WMI Provider for Computer Management に対して [!INCLUDE[msCoName](../../includes/msconame-md.md)] WQL (Windows Management Instrumentation Query Language) ステートメントを実行する方法について説明します。  
  
 この例では、WQL エディター、WBEMtest.exe を使用して、WMI プロバイダーに対して WQL クエリを実行し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス、ネットワーク プロトコル、および別名を列挙します。  
  
### <a name="querying-services-using-wbemtest"></a>WBEMtest を使用したサービスの照会  
  
1.  **開始** メニューのをクリックして**実行**、し、入力**WBEMtest**です。  
  
2.  WBEMtest.exe のダイアログ ボックスが表示されます。 **[接続]**をクリックします。  
  
3.  最初のテキスト フィールドに、WMI Provider for Computer Management の名前空間 (「root\Microsoft\SqlServer\ComputerManagement11」) を入力します。 **[接続]**をクリックします。  
  
4.  をクリックして**クエリ**です。 ローカル コンピューターで実行されている現在のサービスを返すクエリを入力:**選択\*から SqlService です。** **[適用]**をクリックします。  
  
5.  さらに追加することでクエリを絞り込んで**場所 ServiceName"MSSQLSERVER"を =**です。  
  
  
