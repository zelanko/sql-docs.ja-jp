---
title: イベント通知に関する情報の取得 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- event notifications [SQL Server], metadata
- status information [SQL Server], event notifications
- metadata [SQL Server], event notifications
ms.assetid: 8bc10867-66d6-4f57-ac32-a6c29f3327cd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c8d8271b6279910321058d01c7b2f96b1df62bd0
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85003349"
---
# <a name="get-information-about-event-notifications"></a>イベント通知に関する情報の取得
  次のカタログ ビューは、イベント通知に関するメタデータのクエリに使用できます。  
  
 **サーバー以外のレベルのイベント通知に関する情報を取得するには**  
  
-   [sys.event_notifications &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-event-notifications-transact-sql)  
  
> [!NOTE]  
>  データベース レベルで作成した **sys.event_notifications** の任意のイベント通知に関するメタデータを表示するには、少なくとも、データベースに対して CONTROL 権限、ALTER 権限、TAKE OWNERSHIP 権限、または VIEW DEFINITION 権限を持っているか、イベント通知の所有者であるか、ALTER ANY DATABASE EVENT NOTIFICATION 権限を持っている必要があります。 特定のキューで作成したイベント通知の場合は、少なくとも、オブジェクトに対して CONTROL 権限、ALTER 権限、TAKE OWNERSHIP 権限、または VIEW DEFINITION 権限を持っているか、イベント通知の所有者であるか、ALTER ANY DATABASE EVENT NOTIFICATION 権限を持っている必要があります。  
  
 **サーバーレベルのイベント通知に関する情報を取得するには**  
  
-   [sys.server_event_notifications &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-event-notifications-transact-sql)  
  
> [!NOTE]  
>  **sys.server_event_notifications**の任意のイベント通知に関するメタデータを表示するには、少なくとも、サーバーに対して CONTROL 権限または VIEW ANY DEFINITION 権限を持っているか、イベント通知のログオンまたは所有者であるか、ALTER ANY EVENT NOTIFICATION 権限を持っている必要があります。  
  
 **イベント通知を発生させることができるすべてのイベントに関する情報を取得するには**  
  
-   [sys.event_notification_event_types &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-event-notification-event-types-transact-sql)  
  
> [!NOTE]  
>  このカタログ ビューからイベント グループが返されることはありません。  
  
## <a name="see-also"></a>参照  
 [イベント通知](event-notifications.md)  
  
  
