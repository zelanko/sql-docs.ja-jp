---
title: オプション (SQL Server AlwaysOn、[ダッシュボード] ページ) | Microsoft Docs
ms.custom: ''
ms.date: 05/17/2016
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.suite: sql
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Alwayson.Dashboard
ms.assetid: 4369b588-e982-4b57-80a1-beb2e879ce0b
caps.latest.revision: 8
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 6bc9649dd6bd14a0a34005e369285275c7acb0a9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="options-sql-server-always-on-dashboard-page"></a>オプション (SQL Server AlwaysOn、[ダッシュボード] ページ)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)][ **のオプション]** ダイアログ ボックスの **[SQL Server AlwaysOn ダッシュボード]** ページを使用して、AlwaysOn ダッシュボードを構成します。  
  
 **このページにアクセスするには:**  
  
 **[ツール]** メニューの **[オプション]** をクリックし、 **[SQL Server AlwaysOn]** フォルダーを展開して、 **[ダッシュボード]** をクリックします。  
  
## <a name="on-this-page"></a>このページの内容  
 **[自動更新を有効にする]**  
 クリックすると、自動更新が有効になります。 使用可能なオプションは次のとおりです。  
  
-   **[更新間隔 (秒単位)]** フィールドには、ダッシュボードが更新される秒数が表示されます。 既定値は、30 です。 自動更新を有効にすると、このフィールドを編集して更新間隔を変更できます。  
  
-   **[接続の再試行回数]** には、ダッシュボードが監視している可用性グループの可用性レプリカをホストする [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスにダッシュボードが接続を試行する回数が表示されます。 既定値は、65535 です。 自動更新を有効にすると、このフィールドを編集して接続試行回数を変更できます。  
  
 **[ユーザー定義の AlwaysOn ポリシーを有効にする]。**  
 AlwaysOn ポリシーを定義している場合は、このオプションをクリックしてポリシーを有効にします。  
  
## <a name="see-also"></a>参照  
 [Always On ダッシュボードの使用 &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
