---
title: Analytics Platform System のタイム ゾーンの構成 |Microsoft Docs
description: タイム ゾーンのページでは、Analytics Platform System (APS) アプライアンス上のすべてのノードのタイム ゾーンを設定することができます。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: f9997ed26cea5c63d69a7be84b25c247add9b692
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961442"
---
# <a name="appliance-time-zone-configuration---analytics-platform-system"></a>アプライアンスのタイム ゾーンの構成 - Analytics Platform System
**タイム ゾーン** ページでは、Analytics Platform System (APS) アプライアンス上のすべてのノードのタイム ゾーンを設定することができます。  
  
## <a name="to-set-the-time-zone"></a>タイム ゾーンを設定するには  
  
1.  Configuration Manager を起動します。 詳細については、次を参照してください。 [Configuration Manager の起動&#40;Analytics Platform System&#41;](launch-the-configuration-manager.md)します。  
  
2.  アプライアンスのサービスを使用して、停止、**サービス状態**Configuration Manager でのページ。 参照してください[PDW のサービス状態&#40;Analytics Platform System&#41; ](pdw-services-status.md)手順についてはします。  
  
3.  Configuration Manager の左側のウィンドウで次のようにクリックします。**タイム ゾーン**します。 目的のタイム ゾーンを選択して、**タイム ゾーン**ドロップダウン メニュー。 場所、に応じてこともできます横のボックスをオンに**夏時間の時計を自動的に調整**します。  
  
4.  クリックして**適用**変更を保存します。  
  
5.  使用して、アプライアンスのサービスを再起動、**サービス状態**Configuration Manager でのページ。 場合は、特権を変更する予定のも、アプライアンスを再起動する前に実行できます。  
  
![DWConfig アプライアンスの時刻](./media/appliance-time-zone-configuration/SQL_Server_PDW_DWConfig_ApplTopTime.png "SQL_Server_PDW_DWConfig_ApplTopTime")  
  
## <a name="see-also"></a>関連項目  
[Configuration Manager の起動&#40;Analytics Platform System&#41;](launch-the-configuration-manager.md)  
  
