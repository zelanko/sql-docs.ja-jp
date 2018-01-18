---
title: "TCP/IP のプロパティ ([プロトコル] タブ) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/24/2016
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: configuration-manager
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: TCP/IP [SQL Server], configuration options
ms.assetid: 007638fc-3a24-4460-adbe-545ded5d6f88
caps.latest.revision: "38"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: eacd9f77d0794038ce3d4df00f4af06d8e232e6e
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="tcpip-properties-protocols-tab"></a>[TCP/IP のプロパティ] ダイアログ ボックス ([プロトコル] タブ)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]使用して、 **TCP/IP プロパティ**TCP/IP プロトコルのオプションを構成するダイアログ ボックス。 左ペインで **[TCP/IP]** をクリックすると、詳細ペインに個々の IP アドレス構成が表示されます。  
  
 変更を有効にするには、Microsoft SQL Server を再起動する必要があります。  
  
## <a name="options"></a>オプション  
 **有効**  
 可能な値は、 **[はい]** と **[いいえ]**です。  
  
 **[Keep Alive]**  
 接続のリモート側のコンピューターが使用可能かどうかを確認するために、Keep Alive パケットを送信する間隔 (ミリ秒) を指定します。  
  
 **[すべて受信待ち]**  
 コンピューター上のネットワーク カードに割り当てられているすべての IP アドレスで SQL Server がリッスンするかどうかを指定します。 **[いいえ]**に設定した場合は、各 IP アドレスのプロパティ ダイアログ ボックスを使用して、IP アドレスごとに個別の構成を行ってください。 **[はい]**に設定した場合は、 **[IPAll]** プロパティ ボックスの設定がすべての IP アドレスに適用されます。 既定値は **[はい]**です。  
  
 **[遅延なし]**  
 SQL Server では、このプロパティに対する変更は実装されません。  
  
## <a name="see-also"></a>参照  
 [ネットワーク プロトコルの選択](https://msdn.microsoft.com/library/ms187892(v=sql.130).aspx)   
 [TCP/IP を使用した有効な接続文字列を作成します。](creating-a-valid-connection-string-using-tcp-ip.md)  
  
  
