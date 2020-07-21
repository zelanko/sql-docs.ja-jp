---
title: アップグレードアドバイザーの進行状況 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor [SQL Server], analysis progress status
- analyzing system [Upgrade Advisor], progress information
- SQL Server Upgrade Advisor, analysis progress status
- monitoring analysis progress
- progress information [Upgrade Advisor]
- status information [Upgrade Advisor]
ms.assetid: a9e3d1c8-d492-4beb-93c7-f1bc40d4a910
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 692b06051872084ff5e1b16dfaf1f8198a649d62
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85062341"
---
# <a name="upgrade-advisor-progress"></a>アップグレード アドバイザーの進行状況
  アップグレード アドバイザー分析では、選択した各 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントの分析を実行する専用アナライザーから開始します。 コンポーネントが分析されると、**進行状況を示すダイアログボックス**が表示されます。  
  
## <a name="options"></a>オプション  
 **操作**  
 分析対象として選択された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントを指定します。  
  
 **状態**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントの進行状況インターフェイスから返された状態値が表示されます。  
  
 **メッセージ**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の 1 つのアナライザーから返されたエラー、失敗、または成功のメッセージが表示されます。  
  
> [!NOTE]  
>  分析所要時間が非常に長い場合、その分析を停止してアップグレード アドバイザー分析ウィザードを終了してから、そのウィザードを再実行できます。 分析時間を短縮するには、スキャンするコンポーネントを少なくします。  
  
 分析が完了すると、そのレポートがファイルに書き込まれます。 レポートを表示するには、[**レポートの起動**] をクリックして、このページからレポートビューアーを起動します。 後でレポートを表示する場合は、アップグレードアドバイザーの開始ページから**アップグレードアドバイザーレポートビューアー**を開くことができます。  
  
> [!NOTE]  
>  以前のレポートはサーバーを分析するたびに保存されています。 保存されるレポートのファイル名には、タイムスタンプが使用されます。 レポート ビューアーでは、保存されている最近 5 件のレポートを表示できます。  
  
## <a name="see-also"></a>参照  
 [方法: アップグレードアドバイザーを起動する](../../../2014/sql-server/install/how-to-launch-upgrade-advisor.md)   
 [アップグレードアドバイザー分析ウィザードを実行する方法](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md)   
 [SQL Server コンポーネント](../../../2014/sql-server/install/sql-server-components.md)   
 [アップグレードアドバイザーのユーザーインターフェイスリファレンス](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)   
 [アップグレード アドバイザーの使用](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
