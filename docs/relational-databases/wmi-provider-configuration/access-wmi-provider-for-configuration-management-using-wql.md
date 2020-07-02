---
title: WQL を使用して WMI プロバイダーにアクセスする
description: この例を使用すると、SQL Server でコンピューター管理用の WMI プロバイダーの Windows Management Instrumentation クエリ言語ステートメントを実行する方法を確認できます。
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- query language [WMI]
- WMI Query Language [WMI]
- WQL [WMI]
- WMI Provider for Configuration Management, WQL
ms.assetid: 26499530-d93b-452b-bbe4-217ef1d11e68
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 6e9dc2e3d0faee311945552c485187c8179f3615
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85715140"
---
# <a name="access-wmi-provider-for-configuration-management-using-wql"></a>WQL を使用して構成管理の WMI プロバイダーにアクセスする
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]
  このセクションでは、WMI Provider for Computer Management に対して [!INCLUDE[msCoName](../../includes/msconame-md.md)] WQL (Windows Management Instrumentation Query Language) ステートメントを実行する方法について説明します。  
  
 この例では、WQL エディター、WBEMtest.exe を使用して、WMI プロバイダーに対して WQL クエリを実行し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス、ネットワーク プロトコル、および別名を列挙します。  
  
### <a name="querying-services-using-wbemtest"></a>WBEMtest を使用したサービスの照会  
  
1.  [**スタート**] メニューの [**実行**] をクリックし、「 **WBEMtest**」と入力します。  
  
2.  WBEMtest.exe のダイアログ ボックスが表示されます。 **[Connect]** をクリックします。  
  
3.  最初のテキスト フィールドに、WMI Provider for Computer Management の名前空間 (「root\Microsoft\SqlServer\ComputerManagement11」) を入力します。 **[Connect]** をクリックします。  
  
4.  **[クエリ]** をクリックします。 ローカルコンピューターで現在実行されているサービスを返すクエリを入力します: **SELECT \* FROM sqlservice。** **[適用]** をクリックします。  
  
5.  **WHERE ServiceName = "MSSQLSERVER"** を追加して、クエリをさらに絞り込みます。  
  
  
